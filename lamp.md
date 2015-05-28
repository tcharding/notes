iptables 
--------

create iptables.test.rules
* iptables-restore < iptables.test.rules
check it
* cp to /etc/iptables.up.rules
start at boot
* echo 'iptables-restore < /etc/iptables.up.rules' > /etc/network/if-pre-up.d
turn on x bit
* chmod u+x /etc/network/if-pre-up/iptables


LAMP
---

install Apache
* apt-get install apache2

install mariaDB
* apt-get install mariadb-server
* mysql_secure_installation

install php
* apt-get install php5 php-pear php5-mysql
* touch /var/www/php-info.php
* echo '<?php phpinfo(); ?>' >> /var/www/html/phpinfo.php

restart apache
* service apache2 restart

mysql
-----
create database
* mysqladmin -u root -p create nameDB

login as root
* mysql -u root -p

create user and give perms on above database
* GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER,
  CREATE TEMPORARY TABLES, LOCK TABLES ON nameDB.* TO
  'name'@'localhost' IDENTIFIED BY 'userpassword';

flush and quit
* FLUSH PRIVILEGES;
* \q

after quit remove login info 
* vim ~/.mysql_history

[links]

; ssh hardening
<https://howto.biapy.com/en/debian-gnu-linux/system/security/harden-the-ssh-access-security-on-debian>

; linode LAMP setup guide
<https://www.linode.com/docs/websites/lamp/lamp-server-on-debian-7-wheezy>
