# Linux Basic Commands

## Introduction

This file covers the core commands needed to work comfortably in a Linux
terminal: moving around the filesystem, creating and manipulating files,
controlling permissions and ownership, and managing users. Every command
below should be typed into a real terminal to build muscle memory, reading
alone is not enough.

Throughout this file, `$` at the start of a line represents a normal
user's command prompt, and `#` represents a root user's prompt. Do not
type the `$` or `#` themselves, they are just prompt indicators.

## 1. Directory Navigation

### `pwd` - Print Working Directory

Shows the full path of the directory you are currently in.

```bash
$ pwd
/home/kali
```

### `ls` - List Directory Contents

Lists the files and directories inside the current (or specified)
directory.

```bash
$ ls
Desktop  Documents  Downloads  Pictures
```

Common useful flags:

- `-l` - Long listing format, shows permissions, owner, group, size,
  and modification date.
- `-a` - Show all files, including hidden files (files starting with a
  dot, `.`).
- `-h` - Human-readable file sizes (KB, MB, GB instead of raw bytes),
  used together with `-l`.
- `-la` (or `-al`) - Combines `-l` and `-a`, the most commonly used
  combination.
- `-lh` - Combines `-l` and `-h`, long listing with readable sizes.

```bash
$ ls -la
total 32
drwxr-xr-x  5 kali kali 4096 Aug 10 09:15 .
drwxr-xr-x  3 root root 4096 Aug  1 10:00 ..
-rw-------  1 kali kali  220 Aug  1 10:00 .bash_history
-rw-r--r--  1 kali kali 3771 Aug  1 10:00 .bashrc
drwxr-xr-x  2 kali kali 4096 Aug 10 09:14 Documents

$ ls -lh /var/log
-rw-r-----  1 root adm  1.2M Aug 17 08:00 syslog
-rw-r-----  1 root adm  340K Aug 17 08:00 auth.log
```

### `cd` - Change Directory

Moves from the current directory into another directory.

```bash
$ cd Documents          # Move into a subdirectory named Documents
$ cd ..                 # Move up one directory (to the parent)
$ cd /etc                # Move to an absolute path
$ cd ~                  # Move to your home directory
$ cd -                  # Move to the previous directory you were in
$ cd                    # With no argument, also goes to the home directory
```

Understanding **absolute paths** (start with `/`, always describe the
full location from root) versus **relative paths** (describe a location
relative to where you currently are) is essential:

```bash
$ pwd
/home/kali
$ cd Documents          # relative path, moves to /home/kali/Documents
$ cd /home/kali/Documents  # absolute path, same destination either way
```

## 2. File Manipulation

### `touch` - Create an Empty File (or Update Timestamp)

```bash
$ touch notes.txt
$ ls -l notes.txt
-rw-r--r-- 1 kali kali 0 Aug 17 10:00 notes.txt
```

If the file already exists, `touch` just updates its "last modified"
timestamp instead of creating a new file.

### `mkdir` - Make a Directory

```bash
$ mkdir project
$ mkdir -p project/scripts/python   # -p creates parent directories as needed
```

Without `-p`, `mkdir project/scripts/python` would fail with an error if
`project` and `project/scripts` did not already exist.

### `rm` - Remove Files and Directories

```bash
$ rm notes.txt              # Delete a single file
$ rm -r project              # Delete a directory and everything inside it (recursive)
$ rm -rf project             # Same, but force, no confirmation prompts, no errors if missing
```

`rm -rf` is extremely powerful and dangerous. It deletes without asking
for confirmation and works recursively through directories. Always
double-check the path before running it, especially as root. There is
normally no "recycle bin" recovery in Linux.

### `cp` - Copy Files and Directories

```bash
$ cp report.txt report_backup.txt      # Copy a file
$ cp report.txt /home/kali/Documents/  # Copy a file into a directory
$ cp -r project/ project_backup/        # Copy an entire directory (recursive)
```

### `mv` - Move or Rename Files and Directories

```bash
$ mv oldname.txt newname.txt        # Rename a file (same directory)
$ mv report.txt Documents/          # Move a file into a directory
$ mv Documents/ Documents_2024/     # Rename a directory
```

There is no separate "rename" command in Linux, `mv` is used for both
moving and renaming, since renaming is really just "moving" a file to a
new name in the same location.

### `cat` - Display Full File Contents

Prints the entire contents of a file to the terminal at once. Best for
small files.

```bash
$ cat /etc/hostname
kali
```

`cat` can also combine multiple files:

```bash
$ cat file1.txt file2.txt > combined.txt
```

### `less` - View File Contents Page by Page

Better than `cat` for large files, since it lets you scroll instead of
dumping everything to the screen at once.

```bash
$ less /var/log/syslog
```

Inside `less`:

- `Space` or `Page Down` - Next page.
- `b` - Previous page.
- `/searchterm` - Search forward for text.
- `n` - Jump to the next search match.
- `q` - Quit and return to the terminal.

### `head` - Show the Beginning of a File

```bash
$ head file.txt              # Shows the first 10 lines by default
$ head -n 20 file.txt         # Shows the first 20 lines
```

### `tail` - Show the End of a File

```bash
$ tail file.txt               # Shows the last 10 lines by default
$ tail -n 50 file.txt          # Shows the last 50 lines
$ tail -f /var/log/auth.log    # Follow mode: keeps watching the file and
                               # prints new lines as they are added, very
                               # useful for monitoring logs in real time
```

## 3. File Permissions and Ownership

### Understanding File Types and Permissions in `ls -l`

```bash
$ ls -l notes.txt
-rw-r--r-- 1 kali kali 220 Aug 17 10:00 notes.txt
```

Breaking down `-rw-r--r--`:

- Position 1: File type. `-` means regular file, `d` means directory,
  `l` means symbolic link.
- Positions 2-4 (`rw-`): Permissions for the **owner** (user) of the file.
- Positions 5-7 (`r--`): Permissions for the **group** the file belongs to.
- Positions 8-10 (`r--`): Permissions for **others** (everyone else).

Each permission group has three possible flags:

- `r` (read) - View file contents, or list a directory's contents.
- `w` (write) - Modify file contents, or create/delete files inside a
  directory.
- `x` (execute) - Run the file as a program/script, or enter
  ("traverse") a directory with `cd`.

A `-` in place of a letter means that permission is not granted.

### `chmod` - Change File Permissions

`chmod` can be used with either **symbolic mode** or **numeric (octal)
mode**.

**Symbolic mode:**

```bash
$ chmod u+x script.sh     # Add execute permission for the owner (user)
$ chmod g-w file.txt      # Remove write permission for the group
$ chmod o-r secret.txt    # Remove read permission for others
$ chmod a+r file.txt      # Add read permission for all (user, group, others)
$ chmod u=rwx,g=rx,o= file.txt  # Set exact permissions for each category
```

`u` = user/owner, `g` = group, `o` = others, `a` = all. `+` adds a
permission, `-` removes it, `=` sets it exactly.

**Numeric (octal) mode:**

Each permission has a numeric value: `r` = 4, `w` = 2, `x` = 1. Add them
together for each category (owner, group, others) to get a 3-digit code.

```bash
$ chmod 755 script.sh
```

This means:

- Owner: 7 = 4+2+1 = read, write, execute (`rwx`)
- Group: 5 = 4+0+1 = read, execute (`r-x`)
- Others: 5 = 4+0+1 = read, execute (`r-x`)

```bash
$ chmod 644 file.txt
```

- Owner: 6 = 4+2 = read, write (`rw-`)
- Group: 4 = read only (`r--`)
- Others: 4 = read only (`r--`)

Common permission patterns:

| Numeric | Meaning | Typical use |
|---|---|---|
| 755 | rwxr-xr-x | Executable scripts, programs |
| 644 | rw-r--r-- | Regular text/data files |
| 700 | rwx------ | Private scripts, only owner can access |
| 600 | rw------- | Private files, e.g. SSH private keys |
| 777 | rwxrwxrwx | Everyone can do anything (avoid, security risk) |

### `chown` - Change File Owner

```bash
$ sudo chown kali file.txt              # Change owner to user "kali"
$ sudo chown kali:kali file.txt         # Change owner and group together
$ sudo chown -R kali:kali /home/kali/project  # Recursively change ownership
```

### `chgrp` - Change Group Ownership

```bash
$ sudo chgrp developers file.txt
```

Changes only the group associated with a file, leaving the owner
unchanged.

## 4. User Management and Privilege Elevation

### `whoami` - Show the Current Username

```bash
$ whoami
kali
```

### `id` - Show User and Group IDs

```bash
$ id
uid=1000(kali) gid=1000(kali) groups=1000(kali),27(sudo),1001(wireshark)
```

This shows the numeric User ID (`uid`), primary Group ID (`gid`), and all
groups the current user belongs to. Being in the `sudo` group is what
allows a normal user to run commands as root using `sudo`.

### `sudo` - Execute a Single Command as Root

```bash
$ sudo apt update
```

`sudo` ("superuser do") runs one command with root privileges, then
returns to the normal user afterward. It normally asks for the current
user's own password (not the root password), and only works if that
user has been granted sudo rights (usually by being a member of the
`sudo` group).

### `su` - Switch User

```bash
$ su root          # Switch to the root user (asks for root's password)
$ su - root         # Same, but also loads root's full environment (recommended)
$ su - student       # Switch to a different regular user account
```

The difference between `sudo` and `su`:

- `sudo` runs a single command with elevated privileges, and returns to
  the original user immediately after.
- `su` opens an entirely new shell session logged in as a different user,
  which continues until you type `exit`.

### `useradd` - Create a New User Account

```bash
$ sudo useradd -m -s /bin/bash student
```

- `-m` - Create a home directory for the new user (`/home/student`).
- `-s /bin/bash` - Set Bash as the user's default shell.

After creating the account, it has no password set and cannot log in
until one is assigned (see `passwd` below).

### `passwd` - Set or Change a Password

```bash
$ passwd                  # Change your own password
$ sudo passwd student     # Set/change another user's password (as root)
```

The command interactively prompts for the new password (and confirmation),
it is not typed as a command-line argument for security reasons.

## Summary

This file covered navigating the filesystem with `pwd`, `ls`, and `cd`,
manipulating files and directories with `touch`, `mkdir`, `rm`, `cp`, and
`mv`, viewing file contents with `cat`, `less`, `head`, and `tail`,
understanding and changing permissions with `chmod` (both symbolic and
numeric modes), changing ownership with `chown` and `chgrp`, and managing
users and privilege elevation with `whoami`, `id`, `sudo`, `su`,
`useradd`, and `passwd`. These are the daily-driver commands used
constantly in any Linux terminal session, and they form the foundation
needed before moving on to the advanced commands and scripting covered in
the next file.
