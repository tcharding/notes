MIX Assembly Language (and development environment)
==================================================

At terminal 
-----------
* compile
$ mixasm file.mixal
* run 
$ mixvm -r file	   <!-- non-interactive -->
$ mixvm -r -d file <!-- dump registers -->
$ mixvm -r -t file <!-- output execution time -->

Within Emacs 
------------
* compile as usual
* run mix virtual machine  
M-x mixvm

mixvm 
-----
pc <!-- program counter -->
run
abpa NUM <!-- add break point address -->
abp NUM	 <!-- add break point line number -->
help	 <!-- help -->
