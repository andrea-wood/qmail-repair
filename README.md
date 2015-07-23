# qmail-repair
SOURCE: http://pyropus.ca/software/queue-repair/docs.html
queue-repair-0.9.0
queue-repair Documentation

Installing queue-repair

Download the latest version of queue-repair.
Unpack the tarball:
    				tar xzf queue-repair-version.tar.gz
    			
Copy the contents to a suitable location:
    				mkdir /usr/local/lib/queue-repair
    				cp -a queue-repair-version/* /usr/local/lib/queue-repair/
    			
You can install getmail in your home directory or elsewhere if you prefer.
Running queue-repair

Change into the directory you installed queue-repair in, or ensure that directory is in your path.
Stop qmail-send. Running queue-repair on a live queue could give erroneous information in test-only mode, and will seriously confuse qmail in repair mode.
Run queue_repair.py with the options you choose, documented below.

Basic usage information:

    				queue_repair.py [options] [conf-qmail]
    			
conf-qmail defaults to /var/qmail/.

Restart qmail.
queue-repair Options

queue-repair understands the following commandline options:

--help
-h
Display usage information and built-in defaults, then exit.
--test
-t
Run in test-only mode. queue-repair will attempt to report all problems that it finds, without correcting them. This is the default.
--repair
-r
Run in repair mode. queue-repair will attempt to correct all problems that it finds, except if the basic queue directories (queue, queue/mess, queue/info, etc) are not found.
--create
-c
Run in create-and-repair mode. queue-repair will attempt to correct all problems that it finds, including creation of a new queue structure from scratch.
--split N
-s N
Specify N as the value of conf-split. This is the number of split subdirectories for those queue directories which are hashed. The default for qmail is 23. Appropriate values depend on the volume of mail handled, OS filesystem efficiency, and other factors, but this should always be a prime number.

If you do not specify conf-split, queue-repair will attempt to determine the current value from the existing queue. This option can be used, however, to change the conf-split value of an existing queue (qmail will still have to be recompiled with the new value). When creating a new queue, this value must always be specified.

--bigtodo
-b
Use big-todo. queue-repair should be able to automatically determine if you're using qmail patched with the big-todo patch. This option can be used, however, to convert a non-big-todo queue to a big-todo queue (qmail will still have to be recompiled with the big-todo patch).

If neither this option nor --no-bigtodo is used, queue-repair will attempt to determine this automatically. When creating a new queue, either this option or --no-bigtodo must always be specified.

--no-bigtodo
-n
Do not use big-todo. queue-repair should be able to automatically determine if you're using qmail patched with the big-todo patch. This option can be used, however, to convert a big-todo queue to a non big-todo queue (qmail will still have to be recompiled without the big-todo patch).

If neither this option nor --bigtodo is used, queue-repair will attempt to determine this automatically. When creating a new queue, either this option or --bigtodo must always be specified.

--i-want-a-broken-conf-split
Force the use of a non-prime value for conf-split.
