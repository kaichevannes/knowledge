# Security and File Permissions

Read is 4, Write is 2, Execute is 1 (rwx). This is how we get the chmod numbers. First we specify owner, then group, then everyone else. `chown owner:group file` to change owner.

## Linux Accounts

User accounts (stored in `/etc/passwd`) have a username, UID and password — `/etc/shadow` contains the actual encrypted password. New users can be added with `useradd <user>` and `passwd <user>`. Users are deleted with `userdel`. A Linux group (stored in `/etc/group`) is a collection of users referred to with a GID. Groups are added with `groupadd -g <GID> <group-name>`, deleted with `groupdel <group-name>`.

Users have a username, UID, GID, Home Directory, and Default Shell. We can check the IDs of a user with `id <username>`. Root (the superuser account) has UID 0, system accounts are < 100 or between 500 - 1000 and have no home directory — used by software and services that don't run as root like ssh and mail. Service accounts are created when services are installed in Linux like nginx. The `who` command shows a list of logged in users, `last` gives a historical log of users and reboot times.

`su` allows you to switch to any other user in the system — usually we only use `sudo` to act as the superuser. Only users listed in`/etc/sudoers` can use sudo. Sudoers specifies the user or group who can sudo, the host they can run it on, the user they can run it as, and the commands they are allowed to use.

## SSH

Generate a new ssh key pair with `ssh-keygen`.

To add your public key to a remote host you can use the `ssh-copy-id` command.

`scp /home/bob/<file> <remote-host>:/home/bob` allows us to copy files to a remote host.
