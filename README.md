This is an implementation of **Shrug**, a subset of the version control system Git.

Shrug is a contraction of **Sh**ell-**ru**nning-**g**it.

Shrug only implements a few of the more commonly used commands of Git. It is written using
POSIX-compatible shell. The program is run using
[*dash(1)*](https://manpages.debian.org/buster/dash/dash.1.en.html)
which is referenced at the beginning of each file using
```
#!/bin/dash
```
If [*dash(1)*](https://manpages.debian.org/buster/dash/dash.1.en.html)
is installed elsewhere on your local machine, then you need to modify this line
to point towards where
[*dash(1)*](https://manpages.debian.org/buster/dash/dash.1.en.html)
is installed. For example, someone running MacOS would use
```
#!/usr/bin/env dash
```

The commands that are implemented are
- `shrug-init`: Used to create an empty Shrug repository
- `shrug-add *filenames*...`: Used to add one or more files to the "index".
- `shrug-commit [-a] -m *commit message*`: Saves all files in the index to the repository.
    - The "-m" option is necessary for all commits
    - An optional "-a" option which causes all files already in the index to have their
    contents from the current directory added to the index before the commit
- `shrug-log`: prints out all commits made to the repository
- `shrug-show *[commit]:filename*`: prints the contents of the specified filename
    as of the specified commit. If commit is omitted, the contents of the
    file in the index should be printed.
- `shrug-rm [--force] [--cached] *filenames*...`: removes a file from the index
    and current directory.
    - If the "--cached" option is specified, the file is removed only from the index,
    and not from the current directory.
    - The "--force" option will carry out the removal even if the user will lose work.
- `shrug-status`: shows the status of all files in the current directory, index and repository.

To run each command, run in the terminal
```
sh shrug-init
sh shrug-add *filenames*
sh shrug-commit [-a] -m *commit message*
sh shrug-log
sh shrug-show *[commit]:filename*
sh shrug-rm [--force] [--cached] *filenames*
sh shrug-status
```

Alternatively, you can run the following once to
add executable permissions.
```
chmod +x shrug-init
chmod +x shrug-add
chmod +x shrug-commit
chmod +x shrug-log
chmod +x shrug-show
chmod +x shrug-rm
chmod +x shrug-status
```
And then run the shrug programs using
```
./shrug-init
./shrug-add *filenames*
./shrug-commit [-a] -m *commit message*
./shrug-log
./shrug-show *[commit]:filename*
./shrug-rm [--force] [--cached] *filenames*
./shrug-status
```
