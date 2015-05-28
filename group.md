== Group VM setup ==

=== Overview ===
Virtual Machine for groups. 
* Configure Host
* Iptables
* LAMP
* Mediawiki
* Postfix
* Mailman

=== Configure Host ===
* spin it up Debian 8 instance
* add host name to /etc/hostname
* add entry to /etc/hosts with fqdn
* add user
* add user and root bash config files
* add user ssh key
* harden ssh (disable password login / restar)

=== iptables ===
create iptables.test.rules with rules for ssh and http[s]
* # iptables-restore < iptables.test.rules
check it
* # cp to /etc/iptables.up.rules
start at boot
* # echo 'iptables-restore < /etc/iptables.up.rules' > /etc/network/if-pre-up.d
turn on x bit
* # chmod u+x /etc/network/if-pre-up/iptables

=== LAMP ===

install Apache
* # apt-get install apache2

install mariaDB
* # apt-get install mariadb-server
* # mysql_secure_installation

install php
* # apt-get install php5 php-pear php5-mysql
* # touch /var/www/php-info.php
* # echo '<?php phpinfo()?>' >> /var/www/html/phpinfo.php

restart apache
* # service apache2 restart

test it by going to http://webaddress.com/phpinfo.php

=== mysql create database ===
* # mysqladmin -u root -p create nameDB

login as root
* # mysql -u root -p

create user and give perms on above database
* mysql> GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON nameDB.* TO 'name'@'localhost' IDENTIFIED BY 'userpassword';

flush and quit
* mysql> FLUSH PRIVILEGES;
* mysql> \q

after quit remove login info and remove line GRANT ...
* # vim ~/.mysql_history

=== mediawiki ===
setup server
* # apt-get install curl php5-intl php5-gd php5-xcache
* # service apache2 restart

check latest vesion https://www.mediawiki.org/wiki/Download and get source
* $ curl -O http://releases.wikimedia.org/mediawiki/1.24/mediawiki-1.24.2.tar.gz
untar it and move it to apache document root then proceed to add a database

=== Postfix ===
* # apt-get install postfix
check log
* # cat /var/log/mail.log
postconf
* # postconf -e "myorigin = example.com"
* # postconf -e "myhostname=server1.example.com"
* # postconf -e "relay_domains = example.com, example2.com, example3.com"
* # postfix reload
test using telnet
* # telnet localhost 25
test by sending mail
* $ mail -s 'test' your@email < /dev/null
spam control, add the following to /etc/postfix/main.cf
> smtpd_recipient_restrictions = reject_invalid_hostname,
        reject_unknown_recipient_domain,
        reject_unauth_destination,
        reject_rbl_client sbl.spamhaus.org,
        permit

> smtpd_helo_restrictions = reject_invalid_helo_hostname,
        reject_non_fqdn_helo_hostname,
        reject_unknown_helo_hostname
> smtpd_client_restrictions = reject_rbl_client dnsbl.sorbs.net

DKIM exim4
----------
* apt-get install exim4
* cd /etc/exim4
* openssl genrsa -out dkim.27564764.key 1024
* openssl rsa -in dkim.27564764.key -out dkim.27564764.pub -pubout -outform PEM
create file /etc/exim4/conf.d/main/00_localmacros
> DKIM_CANON = relaxed
> DKIM_SELECTOR = 27564764
> DKIM_PRIVATE_KEY = /etc/exim4/dkim.27564764.key
> DKIM_DOMAIN = ${lc:${domain:$h_from:}}
* update-exim4.conf
* service exim4 restart

add DNS text record (key is in /etc/exim4/dkim.27564764.pub)

=== DKIM postfix ===
* # apt-get install opendkim opendkim-tools
append to config file /etc/opendkim.conf

AutoRestart             Yes
AutoRestartRate         10/1h
UMask                   002
Syslog                  yes
SyslogSuccess           Yes
LogWhy                  Yes

Canonicalization        relaxed/simple

ExternalIgnoreList      refile:/etc/opendkim/TrustedHosts
InternalHosts           refile:/etc/opendkim/TrustedHosts
KeyTable                refile:/etc/opendkim/KeyTable
SigningTable            refile:/etc/opendkim/SigningTable

Mode                    sv
PidFile                 /var/run/opendkim/opendkim.pid
SignatureAlgorithm      rsa-sha256

UserID                  opendkim:opendkim

Socket                  inet:12301@localhost

* # echo 'SOCKET="inet:12301@localhost"' >> /etc/default/opendkim

add these four lines to /etc/postfix/main.cf (see comment below)
* milter_protocol = 2
* milter_default_action = accept
* smtpd_milters = inet:localhost:12301
* non_smtpd_milters = inet:localhost:12301
if last two variables are already defined then add the above values as
comma seperated list e.g
* smtpd_milters = unix:/spamass/spamass.sock, inet:localhost:12301
* non_smtpd_milters = unix:/spamass/spamass.sock, inet:localhost:12301
create the key directories
* # mkdir opendkim
* # mkdir opendkim/keys

create file /etc/opendkim/TrustedHosts with following lines
* 127.0.0.1
* localhost
* *.example.com

create key table /etc/opendkim/KeyTable
* mail._domainkey.example.com example.com:mail:/etc/opendkim/keys/example.com/mail.private

Create a signing table /etc/opendkim/SigningTable
* *@example.com mail._domainkey.example.com

create the keys
* # mkdir /etc/opendkim/keys/example.com
* # cd /etc/opendkim/keys/example.com
* # opendkim-genkey -s mail -d example.com
* # chown opendkim:opendkim mail.private

create a DNS record with the contents of mail.txt

=== mailman ===
* open port 25 in firewall
* # apt-get install mailman
* # newlist mailman

edit postfix config file /etc/postfix/main.cf
* add list.example.com to list of relay_domians
* relay_domains = example.com, lists.example.com

in same file add hash map
* alias_maps = hash:/etc/aliases,hash:/var/lib/mailman/data/aliases
then execute
* # postconf -e "transport_maps = hash:/etc/postfix/transport"
* # postconf -e "mailman_destination_recipient_limit = 1"

confirm that /etc/postfix/master.cf contains
> mailman unix – n n – – pipe flags=FR user=list
argv=/var/lib/mailman/bin/postfix-to-mailman.py ${nexthop} ${user}

create the file /etc/postfix/transport
* lists.example.com mailman:
then postmap it (ignoring warding, we added this line already above)
* # postmap /etc/postfix/transport

add to file /etc/mailman/mm_cfg.py
> MTA = ‘Postfix’
DEB_LISTMASTER = ‘postmaster@example.com’
POSTFIX_STYLE_VIRTUAL_DOMAIN = [‘lists.example.com’]

* # service mailman start
* # service postfix restart

* ? do we need an apache alias
* cp /etc/mailman/apache.conf /etc/apache2/sites-available
and edit it
also newlist has not added aliases


=== links ===

ssh hardening
<https://howto.biapy.com/en/debian-gnu-linux/system/security/harden-the-ssh-access-security-on-debian>

digitalocean Mediawiki guide
* https://www.digitalocean.com/community/tutorials/how-to-install-mediawiki-on-ubuntu-14-04

debian postfix guide
* https://wiki.debian.org/Postfix

digital ocean DKIM
* https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-dkim-with-postfix-on-debian-wheezy

exim4 and DKIM
* http://www.iodigitalsec.com/exim-dkim-and-debian-configuration/

;Various Linux Services

[ ntpd ]

manuall sync server
* ntpd -gq

[end]
