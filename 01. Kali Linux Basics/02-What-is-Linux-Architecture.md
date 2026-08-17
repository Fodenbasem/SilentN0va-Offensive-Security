# What is Linux Architecture

## Introduction to Linux

Linux is a free, open-source, Unix-like operating system kernel, originally
created by Linus Torvalds in 1991. Today "Linux" usually refers to a full
operating system built around that kernel, packaged together with system
tools, libraries, and software into what is called a **distribution**
(often shortened to "distro"). Examples of distributions include Ubuntu,
Debian, Fedora, and Kali Linux.

## Why Linux is the Standard for Security Professionals

Linux is the dominant operating system in offensive and defensive
security work for several practical reasons:

1. **Open Source and Transparent** - The full source code of the kernel
   and most tools is publicly available. Security professionals can read
   exactly how a system works, audit it, and modify it, this is
   impossible with closed-source operating systems.

2. **Powerful Command Line** - Nearly every action in Linux can be
   performed from the terminal and can be scripted. This makes automation,
   repeatability, and chaining of small tools together (a core Unix
   philosophy) very natural. Most security tools are built as command-line
   programs first.

3. **Runs Most of the Internet** - The vast majority of servers, cloud
   infrastructure, and networking equipment in the world run Linux.
   Understanding Linux means understanding the actual systems that are
   being defended or tested.

4. **Free and Purpose-Built Distributions** - Distributions like Kali
   Linux and Parrot OS are built specifically for penetration testing,
   coming pre-loaded with hundreds of security tools, configured and
   ready to use.

5. **Fine-Grained Permissions and Control** - Linux's permission model,
   process handling, and networking stack are directly configurable,
   which is essential both for building attack tools and for
   understanding how to secure real systems.

## The Linux Architecture

Linux, like most modern operating systems, is organized into layers. Each
layer only needs to know how to talk to the layer directly next to it,
which keeps the design clean and modular.

```
 -------------------------------------------------
|                 User Applications                |
|      (Firefox, Nmap, Bash scripts, Wireshark)     |
 -------------------------------------------------
|                    Shell                          |
|         (Bash, Zsh - interprets commands)         |
 -------------------------------------------------
|                System Libraries                   |
|    (glibc and others - provide functions that     |
|     applications use to talk to the kernel)        |
 -------------------------------------------------
|                    Kernel                         |
|  (Process management, memory management, device   |
|   drivers, filesystem, networking)                 |
 -------------------------------------------------
|                    Hardware                       |
|         (CPU, RAM, Disk, Network Card)             |
 -------------------------------------------------
```

### 1. The Kernel

The kernel is the core of the operating system. It runs with the highest
level of privilege and directly manages the computer's hardware. Its main
responsibilities are:

- **Process Management** - Deciding which programs run, when, and for how
  long (scheduling), and isolating processes from each other.
- **Memory Management** - Allocating and freeing RAM for running programs,
  and managing virtual memory (swap).
- **Device Drivers** - Communicating with hardware such as disks,
  network cards, USB devices, and graphics cards.
- **Filesystem Management** - Reading and writing files on storage
  devices through various filesystem formats (ext4, xfs, btrfs, etc).
- **Networking** - Handling the network stack, so programs can send and
  receive data over the network.

Ordinary applications never touch hardware directly, they must ask the
kernel to do it for them, through a controlled interface called
**system calls**.

### 2. System Libraries

System libraries (most importantly `glibc`, the GNU C Library, on most
Linux distributions) provide a standard set of functions that
applications use to request services from the kernel. Instead of every
application needing to know the exact low-level details of making a
system call, it can call a library function like `open()` or `read()`,
and the library handles the details of talking to the kernel underneath.

### 3. The Shell

The shell is a program that reads commands typed by a user (or from a
script) and executes them. It acts as the interface between the human and
the operating system. Common shells include:

- **Bash (Bourne Again Shell)** - The default shell on most Linux
  distributions, including Kali Linux.
- **Zsh (Z Shell)** - A more feature-rich shell, popular for its
  customization options, used by default on some distributions like
  newer Kali versions and Parrot OS in some configurations.
- **sh (Bourne Shell)** - The original, more minimal Unix shell, still
  used as the default `/bin/sh` target on many systems for compatibility.

The shell is what interprets a typed command like `ls -la /home`, finds
the `ls` program, and asks the kernel (through system libraries) to
execute it.

### 4. User Space

Everything that is not the kernel is generally referred to as **user
space** (or "userland"). This includes the shell, system libraries,
graphical desktop environments, and all applications, from a web browser
to Nmap. Programs in user space run with restricted privileges compared
to the kernel, and normally cannot directly access hardware, they must
go through the kernel.

This separation between kernel space (privileged, trusted) and user space
(restricted, untrusted by default) is a fundamental security boundary in
Linux. Privilege escalation, a core topic in penetration testing, is
about a user-space process finding a way to gain kernel-level or root
privileges that it should not normally have.

## The Filesystem Hierarchy Standard (FHS)

Linux organizes all files and directories into a single tree structure,
starting from one root directory written as `/`. There are no separate
drive letters like `C:\` or `D:\` as in Windows, everything, including
other disks and USB drives, is "mounted" somewhere inside this one tree.

The **Filesystem Hierarchy Standard (FHS)** defines the standard purpose
of the main directories, so that software and administrators know exactly
where to expect certain kinds of files. Below is a detailed breakdown of
the most important directories.

### `/` (Root)

The top of the entire filesystem tree. Every other directory exists
inside this one directory, directly or indirectly. Only the root user can
write directly into `/` under normal permission settings.

### `/bin`

Contains essential command binaries (programs) needed for basic system
functionality, available to all users, and needed even in single-user or
recovery mode. Examples: `ls`, `cp`, `mv`, `cat`, `bash` itself. On modern
Kali/Debian systems, `/bin` is often a symbolic link pointing to
`/usr/bin`.

### `/etc`

Contains system-wide **configuration files**. Almost every installed
service or program stores its main configuration here. Examples:

- `/etc/passwd` - Local user account information.
- `/etc/shadow` - Encrypted user passwords (readable only by root).
- `/etc/hosts` - Manual hostname-to-IP mappings.
- `/etc/ssh/sshd_config` - SSH server configuration.

This directory is extremely important in penetration testing, misconfigured
files here are a very common source of privilege escalation and
information disclosure.

### `/home`

Contains the personal directories of regular (non-root) users. Each user
typically gets their own subdirectory, for example `/home/kali` or
`/home/student`. This is where a normal user's personal files, downloads,
desktop, and configuration files usually live.

### `/root`

The home directory specifically for the **root** user (the Linux
superuser/administrator account). It is separate from `/home` for
security and practical reasons, so root's files remain accessible even if
`/home` is on a separate disk that fails to mount.

### `/tmp`

A directory for **temporary files**. Any user can usually write here.
Files in `/tmp` are often automatically deleted on reboot or after a
certain time period, depending on system configuration. It is commonly
used by both legitimate programs and attackers as a writable, low-privilege
location to drop files temporarily.

### `/var`

Contains **variable data**, meaning files that are expected to change and
grow while the system runs. Examples:

- `/var/log` - System and application log files, extremely important for
  security monitoring and forensic investigation.
- `/var/www` - Common default location for web server files (on many
  web server configurations).
- `/var/mail` - Local mail storage.

### `/usr`

Stands for "Unix System Resources" (not "user"). Contains the majority of
user-facing applications, libraries, and documentation that are not
essential for basic booting. Important subdirectories:

- `/usr/bin` - Most user command binaries.
- `/usr/sbin` - System administration binaries.
- `/usr/lib` - Libraries used by binaries in `/usr/bin` and `/usr/sbin`.
- `/usr/share` - Architecture-independent shared data (documentation,
  icons, wordlists in the case of Kali, such as `/usr/share/wordlists`).

### `/opt`

Used for **optional, third-party, or self-contained software packages**
that are not part of the standard distribution packaging system. Many
security tools that are manually installed (not through `apt`) get placed
here, for example some versions of Metasploit or custom tools may live
under `/opt`.

### Other Notable Directories

- `/sbin` - Essential system binaries typically used by the administrator
  (root), such as commands for networking and disk management.
- `/dev` - Device files, representing hardware devices as files (for
  example `/dev/sda` for a disk, `/dev/null` as a "black hole" device).
- `/proc` - A virtual filesystem providing real-time information about
  running processes and kernel parameters, does not exist on disk, it is
  generated by the kernel on the fly.
- `/mnt` and `/media` - Standard mount points for manually mounted
  filesystems (`/mnt`) and removable media like USB drives (`/media`).

## Difference Between Linux Distributions: Debian-based vs RedHat-based

Most Linux distributions belong to one of a few major "families," based
on which package management system and base system they build on. The two
most important families for security work are Debian-based and
RedHat-based.

| Feature | Debian-based | RedHat-based |
|---|---|---|
| Examples | Debian, Ubuntu, Kali Linux, Parrot OS | RHEL, CentOS/CentOS Stream, Fedora, Rocky Linux, AlmaLinux |
| Package format | `.deb` | `.rpm` |
| Package manager | `apt` / `apt-get` / `dpkg` | `dnf` / `yum` / `rpm` |
| Install command | `sudo apt install <package>` | `sudo dnf install <package>` |
| Update command | `sudo apt update && sudo apt upgrade` | `sudo dnf update` |
| Common use case | Desktops, developer machines, security distros (Kali) | Enterprise servers, corporate environments |
| Configuration philosophy | Generally more permissive defaults | Generally stricter defaults (SELinux often enforced) |

Kali Linux itself is built on **Debian** (specifically Debian Testing),
which is why every command in this module that installs software uses
`apt`. Knowing this distinction matters in real engagements because
target servers are frequently RedHat-based (especially in corporate and
government environments), and a penetration tester needs to recognize
`rpm`/`yum`/`dnf`-based systems and adjust commands accordingly.

## Summary

Linux is built in layers: hardware at the bottom, then the kernel
managing that hardware directly, then system libraries providing a
standard interface, then the shell interpreting user commands, and
finally user-space applications on top. The Filesystem Hierarchy Standard
gives every file and directory a predictable, standard location, which is
essential knowledge both for normal system administration and for
security work like locating configuration files, logs, and privilege
escalation opportunities. Finally, distributions differ mainly in their
package management system, with Debian-based (`apt`, used by Kali Linux)
and RedHat-based (`dnf`/`yum`) being the two families most relevant to
security professionals.
