64ar
========

tar-style command for handling C64-specific files. So far only t64 archives are supported.

## Warnig

This is experimental code and most likely unfit for your purposes. It might accidentally delete all your data, or worse. Make a backup!

This tool does not support CC64S freeze files (.FRZ).

## Usage

If you know tar, 64ar's syntax will feel familiar. The old-style argument block without trailing dash is supported as well: 

``` bash
$ ./64ar vtf wizball.t64    # list content
$ cat bumpingbuggies.t64 | ./64ar xP    # extract content, try to preserve file order
$ ./64ar c ANTIRIAD/ >antiriad.t64    # create T64 of all files in directory
$ ./64ar -Rf brucelee.t64    # fix malformed archive
$ ./64ar -Ef paradroid.t64    # interactively edit archive
$ ./64ar --help
```

Example editor session fixing a malformed, lazy-named T64 archive:
``` python
$ ./64ar -Ef brucelee.t64 
WARNING: number of files does not match header info: 0, should be 1. FIXED
WARNING: wrong length 48069 in header, should be 33072. FIXED
Welcome to the 64ar interactive python shell.
The archive is loaded as the object t.
Type help(t) and help(T64File) for usage info.

#tape name:   'DEMO TAPE'
#signature:   'C64S tape file\r\nDemo tape\x1a......'
#version:     100
#dir entries: 30
  0:44  $0801/$8931    33072 DEMO TAPE/FILE.P00

ready.
In [1]: t.name = "BRUCE LEE"

In [2]: t[0].name = "BRUCE LEE"

In [3]: t.cleanup()

In [4]: t.info()
#tape name:   'BRUCE LEE'
#signature:   'C64 tape image file'
#version:     100
#dir entries: 1

In [5]: t.dir()
BRUCE LEE/BRUCE LEE.P00

In [6]: exit 
bye.
Do you want to save changes (y/[n])? y
 saved.
```
