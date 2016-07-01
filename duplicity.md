Duplicity
=========

* list current files
$ duplicity list-current-files file:///mnt/xhd/duplicity

Restore
-------
Note: destination file/directory must not exist. Source file is relative to
backup root.

$ duplicity --file-to-restore home/tobin/build/scheme/* file:///mnt/xhd/duplicity /path/to/recovery-dir
