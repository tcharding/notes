Perl5
=====

One liners
----------
* change all occurrences in file of foo to bar
perl -pi -e 's/foo/bar/g' file

* remove lines containing 'lunch'
perl -n -i -e 'print unless /lunch/' May.md

Building Distribution 
---------------------
Build new skeleton with
1. h2xs -AX -n Name
2. cd Name
3. perl Makefile.PL
4. make
5. make test

To add a module 'New'
1. Create lib/New.pl
2. Creat t/New.t
3. Update MANIFEST
4. Re-run steps 3-5 above
