---
title: "man - head tail"
description: ""
summary: ""
date: 2024-10-22T09:32:39+05:30
lastmod: 2024-10-22T09:32:39+05:30
draft: true
weight: 998
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## head --help

```bash
Usage: head [OPTION]... [FILE]...
Print the first 10 lines of each FILE to standard output.
With more than one FILE, precede each with a header giving the file name.

With no FILE, or when FILE is -, read standard input.

Mandatory arguments to long options are mandatory for short options too.
  -c, --bytes=[-]NUM       print the first NUM bytes of each file;
                             with the leading '-', print all but the last
                             NUM bytes of each file
  -n, --lines=[-]NUM       print the first NUM lines instead of the first 10;
                             with the leading '-', print all but the last
                             NUM lines of each file
  -q, --quiet, --silent    never print headers giving file names
  -v, --verbose            always print headers giving file names
  -z, --zero-terminated    line delimiter is NUL, not newline
      --help        display this help and exit
      --version     output version information and exit

NUM may have a multiplier suffix:
b 512, kB 1000, K 1024, MB 1000*1000, M 1024*1024,
GB 1000*1000*1000, G 1024*1024*1024, and so on for T, P, E, Z, Y, R, Q.
Binary prefixes can be used, too: KiB=K, MiB=M, and so on.
```


## man head

```bash
NAME
       head - output the first part of files

SYNOPSIS
       head [OPTION]... [FILE]...

DESCRIPTION
       Print  the  first 10 lines of each FILE to standard output.  With more than one FILE, precede
       each with a header giving the file name.

       With no FILE, or when FILE is -, read standard input.

       Mandatory arguments to long options are mandatory for short options too.

       -c, --bytes=[-]NUM
              print the first NUM bytes of each file; with the leading '-', print all but  the  last
              NUM bytes of each file

       -n, --lines=[-]NUM
              print the first NUM lines instead of the first 10; with the leading '-', print all but
              the last NUM lines of each file

       -q, --quiet, --silent
              never print headers giving file names

       -v, --verbose
              always print headers giving file names

       -z, --zero-terminated
              line delimiter is NUL, not newline

       --help display this help and exit

       --version
              output version information and exit

       NUM  may  have  a  multiplier  suffix:  b 512, kB 1000, K 1024, MB 1000*1000, M 1024*1024, GB
       1000*1000*1000, G 1024*1024*1024, and so on for T, P, E, Z, Y, R, Q.  Binary prefixes can  be
       used, too: KiB=K, MiB=M, and so on.
```



## tail --help

```bash
Usage: tail [OPTION]... [FILE]...
Print the last 10 lines of each FILE to standard output.
With more than one FILE, precede each with a header giving the file name.

With no FILE, or when FILE is -, read standard input.

Mandatory arguments to long options are mandatory for short options too.
  -c, --bytes=[+]NUM       output the last NUM bytes; or use -c +NUM to
                             output starting with byte NUM of each file
  -f, --follow[={name|descriptor}]
                           output appended data as the file grows;
                             an absent option argument means 'descriptor'
  -F                       same as --follow=name --retry
  -n, --lines=[+]NUM       output the last NUM lines, instead of the last 10;
                             or use -n +NUM to skip NUM-1 lines at the start
      --max-unchanged-stats=N
                           with --follow=name, reopen a FILE which has not
                             changed size after N (default 5) iterations
                             to see if it has been unlinked or renamed
                             (this is the usual case of rotated log files);
                             with inotify, this option is rarely useful
      --pid=PID            with -f, terminate after process ID, PID dies
  -q, --quiet, --silent    never output headers giving file names
      --retry              keep trying to open a file if it is inaccessible
  -s, --sleep-interval=N   with -f, sleep for approximately N seconds
                             (default 1.0) between iterations;
                             with inotify and --pid=P, check process P at
                             least once every N seconds
  -v, --verbose            always output headers giving file names
  -z, --zero-terminated    line delimiter is NUL, not newline
      --help        display this help and exit
      --version     output version information and exit

NUM may have a multiplier suffix:
b 512, kB 1000, K 1024, MB 1000*1000, M 1024*1024,
GB 1000*1000*1000, G 1024*1024*1024, and so on for T, P, E, Z, Y, R, Q.
Binary prefixes can be used, too: KiB=K, MiB=M, and so on.

With --follow (-f), tail defaults to following the file descriptor, which
means that even if a tail'ed file is renamed, tail will continue to track
its end.  This default behavior is not desirable when you really want to
track the actual name of the file, not the file descriptor (e.g., log
rotation).  Use --follow=name in that case.  That causes tail to track the
named file in a way that accommodates renaming, removal and creation.

```


## man tail

```bash
NAME
       tail - output the last part of files

SYNOPSIS
       tail [OPTION]... [FILE]...

DESCRIPTION
       Print  the  last  10 lines of each FILE to standard output.  With more than one FILE, precede
       each with a header giving the file name.

       With no FILE, or when FILE is -, read standard input.

       Mandatory arguments to long options are mandatory for short options too.

       -c, --bytes=[+]NUM
              output the last NUM bytes; or use -c +NUM to output starting with  byte  NUM  of  each
              file

       -f, --follow[={name|descriptor}]
              output appended data as the file grows;

              an absent option argument means 'descriptor'

       -F     same as --follow=name --retry

       -n, --lines=[+]NUM
              output  the last NUM lines, instead of the last 10; or use -n +NUM to skip NUM-1 lines
              at the start

       --max-unchanged-stats=N
              with --follow=name, reopen a FILE which has not

              changed size after N (default 5) iterations to see if it has been unlinked or  renamed
              (this  is  the  usual  case of rotated log files); with inotify, this option is rarely
              useful

       --pid=PID
              with -f, terminate after process ID, PID dies

       -q, --quiet, --silent
              never output headers giving file names

       --retry
              keep trying to open a file if it is inaccessible

       -s, --sleep-interval=N
              with -f, sleep for approximately N seconds (default 1.0) between iterations; with ino‐
              tify and --pid=P, check process P at least once every N seconds

       -v, --verbose
              always output headers giving file names

       -z, --zero-terminated
              line delimiter is NUL, not newline

       --help display this help and exit

       --version
              output version information and exit

       NUM may have a multiplier suffix: b 512, kB 1000, K  1024,  MB  1000*1000,  M  1024*1024,  GB
       1000*1000*1000,  G 1024*1024*1024, and so on for T, P, E, Z, Y, R, Q.  Binary prefixes can be
       used, too: KiB=K, MiB=M, and so on.

       With --follow (-f), tail defaults to following the file descriptor, which means that even  if
       a tail'ed file is renamed, tail will continue to track its end.  This default behavior is not
       desirable  when you really want to track the actual name of the file, not the file descriptor
       (e.g., log rotation).  Use --follow=name in that case.  That causes tail to track  the  named
       file in a way that accommodates renaming, removal and creation.

```
