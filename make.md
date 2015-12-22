GNU Make 
========
wildcard expansion happens automatically in rules but not
when a variable is set. Use;

$(wildcard *.c)

or

objects := $(patsubst %.c,%.o,$(wildcard *.c))

foo : $(objects)
    cc -o foo $(objects)


