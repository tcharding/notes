The C Programming Language
==========================

Misc
----
* To check if a file exists, check return value of stat(3p).
* When require a buffer for building strings use memory streams (apue page 171)

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

Signals 
-------
* A signal is *generated* for a process (or *sent to* a process) when the event
  that causes the signal occurs.
* A signal is *delivered* to a process when the action for the signal is
  taken. During the time between generation and delivery the signal is said to be
  *pending*.
* A process has the option of *blocking* a signal. If a signal that is blocked
  is generated for a process, and if the action for that signal is either
  default or catch, then the signal remains pending until the process either
  unblocks or ignores the signal.
* A signals *disposition* is the action that is taken when the signal is delivered.  
* Each process has a *signal mask* which is the set of signals currently
  blocked by the process.

Signal 'disposition' is one of:
1. Ignore the signal
2. Catch the signal
3. Let the default action apply

Signal disposition is examined or modified with sigaction(2)
`int sigaction(int signum, const struct sigaction *act,
                     struct sigaction *oldact);`
struct sigaction {
               void     (*sa_handler)(int);
               void     (*sa_sigaction)(int, siginfo_t *, void *);
               sigset_t sa_mask;
               int      sa_flags;
               void     (*sa_restorer)(void);
};
sa_mask is signal set that is additionally blocked when the signal catcher is
run.  

* Wrapper function for sigaction(): `Sigfunc *signal(int signo, Sigfunc *func)`,
  where *func* is either *SIG_DFL*, *SIG_IGN*, or pointer to signal handling
  function.

Threads 
-------
Each thread has its own signal process mask but shares the signal disposition of
the process.

