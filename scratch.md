General notes
-------------
send email from command line
* mail -s 'subject' th@lgnt.com.au < /dev/null

get external ip address
* curl http://ipecho.net/plain; echo

replace all occurrences of a string with another 
* sed -i -- 's/foo/bar/g' file.name
and now recursively
* find . -type f -exec sed -i 's/foo/bar/g' {}+
remove last line of file
* sed -i '$ d' foo.txt

set file and directory premissions
* find . -type f -exec chmod 644 {} \;
* find . -type d -exec chmod 755 {} \;
