64ar
========

tar-style command for handling C64-specific files. So far only t64 archives are supported.

## Warnig

This is experimental code and most likely unfit for your purposes. It might accidentally delete all your data, or worse. Make a backup!

This tool does not support CC64S freeze files (.FRZ).

## Usage
``` bash
$ ./64ar vt wizball.t64    # list content
$ cat bumpingbuggies.t64 | ./64ar xP    # extract content, try to preserve file order
$ ./64ar c ANTIRIAD/ >antiriad.t64    # create T64 of all files in directory
$ ./64ar -Rf brucelee.t64    # fix malformed archive
$ ./64ar E paradroid.t64    # interactively edit archive
$ ./64ar --help
```
