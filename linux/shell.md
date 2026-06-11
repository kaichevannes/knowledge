# Shell

Internal commands are built in to linux like echo, cd, pwd, set. External commands are binaries: mv, date, uptime, cp. `type` is used to determine whether or not a command is internal or external.

## Files

`du -sh <file>` is used to view file size (alternatively `ls -lh <file>`). `tar` (tape archive) is used to group files & directories into tarballs, useful for archiving data: `-c` is used to create an archive, `-f` specifies the name of the tarfile to create, `-z` compresses a tarball to reduce its size; `-xf` extracts the contents from a tarball.

`locate <file>` finds all instances in the filesystem but requires the mlocate.db database which needs to be updated with `updatedb`. `find <dir> -name <file>` doesn't require the database, instead using system calls to the kernel: opendir(), readdir(), stat().

`grep` is used to search for text within a file: `-i` is case insensitive, `-r` searches recursively in a directory, `-v` finds non matching, `-w` finds exact matches, `-A <n>` and `-B <n>` allows us to specify lines before and after a match.

## IO

stdin / stdout / stderr. `>` redirects from stdout, overwriting a file. `>>` appends to a file. To redirect just the error messages we use `2>`, to append this we do `2>>`. When we want a command to show no error output we do `2> /dev/null`. `/dev/null` is known as the bit bucket, coming from the term for a real life bucket where punch card bits were collected. We use a device driver to output to because of the UNIX philosophy that everything is a file.

## Pipes

`tee` prints stdout before doing the pipe. Like an actual T pipe, it spits it out below and continues it forward.
