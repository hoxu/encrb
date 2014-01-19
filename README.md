encrb - encrypted remote backups
================================

encrb backs up plaintext local directories to remote machine as encrypted,
using encfs --reverse and rsync.

Example
-------

    $ ./encrb $HOME/documents $HOME/projects some.server.eu:/home/user/backups/

First run will generate a random password, save it to PASSFILE and prompt for
encfs settings (pressing enter picks the defaults). Encfs KEYFILE is also
created. Further runs will not require any user input.

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

Backing up keyfile and password
-------------------------------

**Remember to back up the keyfile and the password**! If you lose them, you
will lose access to the encrypted data. Naturally you should not back up the
keyfile to the same place where you put the actual backups. And it is a very
good idea to have multiple backups of the keyfile (and password). For maximum
security, keep the data, the keyfile and the password at different locations.

Running from crontab
--------------------

You most likely want to run encrb from crontab. I recommend using flock or
something similar to make sure no multiple instances are running, like this:

    30 0 * * * flock -n /tmp/encrb.lockfile /path/to/encrb --bwlimit 100 $HOME/docs $HOME/projects some.server.eu:/home/user/backups/

Dependencies
------------

* encfs 1.7.4 or later
* python
* rsync

License
-------

encrb is licensed under GPLv3, see http://www.gnu.org/licenses/gpl-3.0.html
