encrb - encrypted remote backups
================================

encrb backs up plaintext local directories to remote machine as encrypted,
using encfs --reverse and rsync.

Example
-------

    $ ./encrb $HOME/documents $HOME/projects some.server.eu:/home/user/backups/

Usage
-----

    $ ./encrb --help
    Usage: encrb [options] dir-to-back-up1... remotepath
    
    Options:
      -h, --help            show this help message and exit
      -k KEYFILE, --keyfile=KEYFILE
                            encfs keyfile to use
      -p PASSFILE, --passfile=PASSFILE
                            file containing encfs keyfile password
      -b BWLIMIT, --bwlimit=BWLIMIT

Dependencies
------------

* encfs 1.7.4 or later
* python
* rsync

License
-------

encrb is licensed under GPLv3, see http://www.gnu.org/licenses/gpl-3.0.html
