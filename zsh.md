Z Shell notes
=============

_Mainly taken from text 'From Bash to Z Shell' - Kiddle, Peek, and Stephenson_

Ctl-t <!-- transpose last two chars -->
Ctl-l <!-- clear screen -->
Esc-. <!-- show last argument to previous command -->
Ctl-u <!-- kill line -->

bindkey -L <!-- show key bindings -->

whereis <cmnd> <!-- Locate the binary, source, and manual-page files for a cmnd -->

Esc-h <!-- gets man page for current command -->

History
-------
!:0 <!-- argument from previous command by number -->
!:3 <!-- 3rd argument -->

!:$ <!-- last argument -->
!:* <!-- all the args -->
!:1:h <!-- head of the 1st arg i.e directory -->
!:1:t <!-- tail of the 1st arg i.e file -->

--

% sched 17:02 echo This is a reminder
% cd <search> <replace> <!-- uses <search> <replace> to build dir from pwd -->

% whence -vm '*ls' <!-- lists all programs matching pattern (not regex) -->

Here Documents and Strings
--------------------------
mutt -s 'blah' $EMAIL_ADDRESS <<HERE
this is the
content of the here doc
HERE

mutt -s 'blah' $EMAIL_ADDRESS <<<"and now a terser email"

Misc
----
setopt numericglobsort
setopt complete_in_word

