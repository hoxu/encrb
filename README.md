encrb - encrypted remote backups
================================

encrb backs up plaintext local directories to remote machine as encrypted,
using encfs --reverse and rsync.

Example
-------

    $ ./encrb $HOME/documents $HOME/projects some.server.eu:/home/user/backups/

First run will generate a random password, save it to KEYFILE and prompt for
encfs settings (pressing enter picks the defaults). Further runs will not
require any user input.

Usage
-----

    $ ./encrb --help
    Usage: encrb [options] dir-to-back-up1... remotepath
    
    Options:
      -h, --help            show this help message and exit
      -k KEYFILE, --keyfile=KEYFILE
                            encfs keyfile to use [~/.encfs6-encrb.xml]
      -p PASSFILE, --passfile=PASSFILE
                            file containing encfs keyfile password [~/.encfs-
                            password]
      -b BWLIMIT, --bwlimit=BWLIMIT
                            Bandwidth limit (KiB/s) for rsync [0]

Dependencies
------------

* encfs 1.7.4 or later
* python
* rsync

License
-------

encrb is licensed under GPLv3, see http://www.gnu.org/licenses/gpl-3.0.html
