Email get, sort, send
=====================

current stack: getmail, procmail, mutt (abook), msmtp
LOG=~/log/

Miscellaneous
-------------
~/.mutt/whitelist

default mailbox is IN-catchall
white listed email goes into IN-inbox

fetchmail
---------
~/.getmail/
log: $LOG/getmail.log

procmail
--------
~/.procmailrc
~/.procmail.d/
log: $LOG/procmail.log


mutt
----

h <!-- toggle headers -->

mutt -H /tmp/0001-<whatever your filename is> <!-- send patch -->

Esc P   <!-- Decrypt message -->

mutt -R <!-- launch mutt read only -->

* send patch
mutt -H 0001-mm-Fix-sparse-use-plain-integer-as-NULL-pointer.patch  -s 'test subject' -c 'th@tobin.cc, tb@tobin.cc' me@tobin.cc



abook
-----
sort
s - by first name
S - by last name
F - by group

'a' while in email adds sender to abook

