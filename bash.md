BASH notes 
==========

** use on top of all scripts **
set -o nounset

Debugging
---------
to echo commands before they are run
`bash -x script`
or from within the script
`set -o xtrace` to turn it on
`set +o xtrace` to turn it off

Special Parameters
------------------
$# = number of parameters passed
$$ = pid
$* = list of all parameters as a single var separated by $IFS
$@ = as for $* but different somehow?
** generally use "$@" ** to access all parameters

Miscellaneous
-------------
redirect stdout and stderr  
`cmnd >out.txt 2>&1`

* = glob
? = single character wildcard
[set] = matches against 's' or 'e' or 't'
[^set] = negates set

{} = arbitrary string set
`ls my_{fingers, toes}.txt`

show files containing 'function'
`less $(grep -l function *)` or
`grep -l function * | less`

Lists
`test -e file && echo file exists || echo file does not exist`

statement blocks
> test -e file && {
>	echo do
>	echo multiple
>	echo commands
> }
