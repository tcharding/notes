The C Programming Language
==========================

Headers
-------
* locate CONSTANT definition, e.g NAME_MAX
	`grep -R " NAME_MAX " /usr/include`

Switch Statement
----------------
switch(intval) {
case n:
    ...
    break;
case 2: case 3: case 4: /* fall through */
    ...
    break;
default:
    ... 
    break;
}

Pointers
--------
* For code example see /home/tobin/build/github/cpl/scratch/pointers.c

1. pre-fix and postfix increment what p points to
  ++*p
  (*p)++ <!--  ++ has higher precedence than '*' -->

2. pre-fix and postfix increment pointer then fetch what p points to
  *p++
  *++p

* If using function pointer, use typedef to simplify the calls. see
  /home/tobin/build/github/apue/ch4/traverse.c for example (also page 133 of
  apue).

