GnuPG 
-----

edit key
  gpg-edit-key YOURMASTERID

export subkeys
gpg --export-secret-subkeys YOURMASTERKEYID >secret-subkeys

or just the ones you want
gpg --export-secret-subkeys SUBKEYID! [SUBKEYID! ..] >secret-subkeys

remove master secret key
gpg --delete-secret-key YOURMASTERID

import subkeys back in
gpg --import secret-subkeys

