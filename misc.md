Miscellaneous notes
===================

echo -e "\xE2\x98\xA0" <!-- skull and crossbones -->

find -type f -iname "Makefile" -exec grep -H "KERNEL" {} \; 

gpg --search-keys who@address.com

move block left/right in python mode
C-c <
C-c >

`file`: determine file type
`uniq`: only unique lines

emacs: set file mode on per file basis
# -*-shell-script-mode-*-

send email from command line
`mail -s 'subject' th@lgnt.com.au < /dev/null`
`mutt -s 'this subject' -a 'MIME'd attachmend' -a 'an' -- john@home.com`
`mutt -s 'sub' -i 'inline_file' john@home.com`

get external ip address
`curl http://ipecho.net/plain; echo`

replace all occurrences of a string with another 
`sed -i -- 's/foo/bar/g' file.name`
`perl -pi -e 's/foo/bar/g' file`

and now recursively
`find . -type f -exec sed -i 's/foo/bar/g' {} \;`

remove last line of file
`sed -i '$ d' foo.txt`


set file and directory premissions
`find . -type f -exec chmod 644 {} \;`
`find . -type d -exec chmod 755 {} \;`

exclude mounted directories
`find / -mount -name test.file`

echo -e "\n now on new line"

