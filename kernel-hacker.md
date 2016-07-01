How To Become a Kernel Hacker
=============================
_one way of_

Pre-amble
---------
For completeness, before you start you need:
1. A computer
2. A 'good' internet connection
3. A working familiarity with a text editor (set up for kernel dev helps)
4. A working familiarity with git

Buy the following three books:
1. Linux Kernel Development - Robert Love
2. Linux Device Drivers - Corbet, Rumini, Kroh-Hartman
3. Essential Linux Device Drivers - Sreekrishnan Venkateswaran

Step 1
------
Read Robert Loves book

Step 2
------
Download, build and run a custom kernel. Warning: don't mess with .config too
much at this stage - it will cause you grief. Try to get a running config from
some place (i.e /proc/config)

Step 3
------

Start reading ldd3. Make sure you get the source (from the website or from one
of the various ports on GitHub). Play with each and every file as it is
mentioned in the text, don't skip any. This is the easiest kernel code you are
going to come across, make sure you are totally comfortable with it. You could
even clear any checkpatch.pl warnings :)

By this stage you are comfortable editing and building kernel code. Also you
have a bit of an idea about /proc/* and /sysfs. You are comfortable
inserting/removing modules and also messing with them via /dev/.

Step 3
------
Set up email client, and also some system to sort mail e.g mutt, fetchmail,
procmail. The more time you spend understanding these now the better.

Subscribe to the following mailing lists:

* Linux Kernel Mailing List:
 'echo subscribe linux-kernel | mail majordomo@vger.kernel.org'

* Linux Newbies:
 see http://kernelnewbies.org/ML

* Device drivers:
 see driverdev.osuosl.org,
 'echo subscribe devicetree | mail majordomo@vger.kernel.org'

Step 4
------
Read linux-tree/README
Read Documentation/HOWTO
start to read Documentation/* starting with the files mentioned in HOWTO

Step 5
------
Start reading eldd. During this time you can start playing around in
drivers/staging. You should learn how to use sparse and coccinelle. See
Documentation/. Now is the time you should try to send your first patch, be
warned minor checkpatch.pl warning patches are usually ignored. However there is
only one way to learn the process and that's by doing it. Don't be afraid but be
polite and try to get everything right :) see linuxnewbies.org for submitting
your first patch.

Step 6
------
Conquer the world.
