# NetServa SH

This **SH**ell project is a set of Ubuntu/systemd Bash aliases and env
variables to help make it easier to manage your Bash shell from an upstream
(Github) repository. The project also includes an associated collection of
shell scripts to setup and manage a simple Ubuntu Web, Mail and DNS server
which also provides a foundation for the [NetServa HCP] PHP web interface.

Note: mid-2017 both projects are in an early WIP alpha stage.

## Usage

To use these scripts make sure you have the `git` package installed and
either [fork this project] and clone your own copy (so you can provide
patches via [pull requests]) or simply clone this repo and use the scripts
anyway you care to. The simplest way to install and setup this project is
to copy and paste this one-liner as root. Please [review the script] at
Github first...

    curl -s https://raw.githubusercontent.com/netserva/sh/master/bin/setup-sh | bash

**Note:** make sure `curl` and `git` are installed first. Use `which git`
and if nothing is returned then manually update the package list and make
sure these very basic packages are available...

    sudo apt -y update
    sudo apt -y full-upgrade
    sudo apt -y install --no-install-recommends ca-certificates curl git nano net-tools openssh-server rsync

To install this project manually, copy and paste these 3 lines below...

    git clone --depth 1 https://github.com/netserva/sh ~/.sh
    ~/.sh/bin/shm install
    . ~/.shrc

The above will clone the Github repository to a folder called `.sh` in your
home directory and activate the system. If you have any problems with the
installed symlinks then just remove them with...

    shm remove

or to remove the entire system use...

    shm removeall

You can pull and push from your own forked repo without having to cd into
the ~/.sh installation first...

    shm pull
    shm push

Easily reset the RWX permsissions of all SH scripts to a safe(r) default...

    shm perms

Just type `alias` to see a set of simple aliases, typing `?` will show the
most common ones with some explanation of their usage and `eh` can be used
to customize this list, and yes, `nano` is the default editor of (my)
choice. Feel free to replace the `e` alias with vim or any other editor.

    ? ....... Show this help
    e ....... The nano Editor with a simplified interface
    f ....... Find named files and list them (recursive)
    i ....... Install a package
    l ....... Tail the end of the most common system Logfile
    n ....... Create a new Note in the users home dir
    m ....... Menu System (TODO)
    p ....... Search for a particular running Process
    q ....... Query text string within files (recursive)
    r ....... Remove a package
    s ....... Search for a package
    u ....... Update the package system
    .. ...... Change to parent directory
    eh ...... Edit this Help file
    em ...... Edit Menu file
    es ...... Edit ~/.myrc and re-execute ~/.shrc
    la ...... List All files including dotfiles
    ll ...... Long Listing
    ls ...... Short form List
    se ...... Sudo Edit text files as root
    sn ...... Show Notes created with "n"
    env ..... Show Environmental global variables
    alias ... To show all current Aliases

Some other useful aliases not list above are...

    ram ..... To show a simple sorted list of apps and their ram usage
    block ... Block or drop a an IP from accessing the system
    unblock . Unblock the above blocked IP
    shblock . Show all blocked IPs

Use `alias | grep log` to see some of the logging aliases, tweak or add
more using `es` to `Edit Shell` your custom and long term persistent
`~/.myrc` file.

`n` (notes) and `sn` (show notes) is an ultra simple note taking system and
(TODO) should be expanded to keep the notes in a private Git repo (to allow
for the potential of passwords and any other sensitive info.)

There is also a couple of dozen (still in flux) fairly standard exported
shell variables that are used by some of the scripts in the `~/.sh/bin/`
dir. They can be set and overriden in the `~/.myrc` file to customize them
for each host. For example, the `gethost` shell function on my main
workstation shows...
```
ADMIN='sysadm'
AMAIL='admin@mbox.goldcoast.org'
ANAME='System Administrator'
APASS='changeme_N0W'
A_GID='1000'
A_UID='1000'
CIMAP='/etc/dovecot'
CSMTP='/etc/postfix'
C_DNS='/etc/powerdns'
C_FPM='/etc/php/7.0/fpm'
C_SQL='/etc/mysql'
C_SSL='/etc/ssl'
C_WEB='/etc/nginx'
DBMYS='/var/lib/mysql'
DBSQL='/var/lib/sqlite'
DHOST='localhost'
DNAME='mbox_goldcoast_org'
DPASS='changeme_N0W'
DPATH='/var/lib/sqlite/sysadm/sysadm.db'
DPORT='3306'
DTYPE='sqlite'
DUSER='sysadm'
EXMYS='mysql -BN sysadm'
EXSQL='sqlite3 /var/lib/sqlite/sysadm/sysadm.db'
MPATH='/home/u/mbox.goldcoast.org/home'
OSMIR='archive.ubuntu.com'
OSREL='zesty'
SQCMD='sqlite3 /var/lib/sqlite/sysadm/sysadm.db'
TAREA='Australia'
TCITY='Sydney'
UPASS='changeme_N0W'
UPATH='/home/u/mbox.goldcoast.org'
U_GID='1001'
U_SHL='/bin/sh'
U_UID='1001'
VHOST='mbox.goldcoast.org'
VPATH='/home/u'
VUSER='u1001'
V_PHP='7.0'
WPATH='/home/u/mbox.goldcoast.org/var/www'
```
You would edit (`es`) `~/.myrc` to change the defaults and `sethost` to
dynamically change them when using the `~/.sh/bin` scripts to, for
instance, add a virtual host.

## More documentation

For now, see [NetServa HCP] for more docmentation about using the hosting
management `setup-*` scripts. Some of the scripts in the `bin/` dir are
meant to be used from the PHP web interface but can generally also be used
standalone from the command line as well.

There are also some semi-related posts on my [personal blog].

_All scripts and documentation are Copyright (C) 1995-2017 Mark Constable and Licensed [AGPL-3.0]_

[Github]: https://github.com/netserva/sh
[NetServa HCP]: https://github.com/netserva/www
[review the script]: https://github.com/netserva/sh/blob/master/bin/setup-sh
[AGPL-3.0]: http://www.gnu.org/licenses/agpl-3.0.html
[fork this project]: https://help.github.com/articles/fork-a-repo
[pull requests]: https://help.github.com/articles/using-pull-requests
[personal blog]: https://markc.blog/news/
