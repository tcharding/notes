GnuPG 
-----

edit key
  gpg --edit-key YOURMASTERID

gpg --fingerprint you@email.com

sign and trust
--------------
gpg --interactive --edit-key address@to.sign
trust
sign

export the persons key and send it to them
gpg --export --armor address@you.signed

when you receive a signed key back import it with
gpg --import file.asc

export subkeys
gpg --export-secret-subkeys YOURMASTERKEYID >secret-subkeys

or just the ones you want
gpg --export-secret-subkeys SUBKEYID! [SUBKEYID! ..] >secret-subkeys

remove master secret key
gpg --delete-secret-key YOURMASTERID

import subkeys back in
gpg --import secret-subkeys

