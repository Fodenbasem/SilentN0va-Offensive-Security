# Linux Basics and Kali Linux Module

## Overview

This module is the starting point for anyone learning Linux for offensive
security work. Linux is the operating system that almost every security
tool, penetration testing distribution, and server on the internet is built
on. Before a person can use tools like Nmap, Metasploit, or Burp Suite
effectively, they need to be comfortable with the Linux command line,
understand how the filesystem is organized, know how permissions work, and
be able to read and write simple shell scripts.

This module builds that foundation from zero, using Kali Linux as the main
working environment because it is the most widely used penetration testing
distribution in the industry.

## Core Objectives

By the end of this module, the learner should be able to:

- Install and configure Kali Linux on a virtual machine, safely and correctly.
- Explain the architecture of Linux, including the kernel, shell, and
  filesystem layout.
- Navigate the filesystem, manage files and directories, and control file
  permissions and ownership.
- Manage users, groups, and privilege elevation with `sudo` and `su`.
- Use advanced text processing tools (`grep`, `awk`, `sed`) to filter and
  transform data, a skill used constantly during penetration testing.
- Understand input/output redirection and piping to chain commands together.
- Monitor and control running processes.
- Perform basic network diagnostics and information gathering from the
  command line.
- Write simple Bash scripts to automate repetitive tasks.

These skills map directly onto real offensive security work. For example,
filtering log files with `grep` and `awk` is the same skill used to parse
scan results from Nmap. Understanding file permissions is the same
knowledge used to find privilege escalation paths on a target machine.

## Table of Contents

| File | Description |
|---|---|
| [README.md](README.md) | This file. Module overview and practice resources. |
| [01-How-to-Install-Kali-Linux-on-VM.md](01-How-to-Install-Kali-Linux-on-VM.md) | Full guide to installing Kali Linux on VirtualBox and VMware, including system requirements and post-install setup. |
| [02-What-is-Linux-Architecture.md](02-What-is-Linux-Architecture.md) | Linux architecture, kernel, shell, the Filesystem Hierarchy Standard, and distribution families. |
| [03-Linux-Basic-Commands.md](03-Linux-Basic-Commands.md) | Core CLI navigation, file manipulation, permissions, ownership, and user management. |
| [04-Linux-Advanced-Commands-and-Scripting.md](04-Linux-Advanced-Commands-and-Scripting.md) | Text processing, redirection, process management, networking basics, and Bash scripting. |

## How to Use This Module

Read the files in order, from 01 to 04. Each file assumes the knowledge
from the previous file. Do not just read the commands, type every single
one of them into a real Kali Linux terminal (or a virtual machine) as you
go. Muscle memory in the terminal only comes from practice, not from
reading.

A good approach is:

1. Read a section.
2. Open a terminal and run every example command shown in that section.
3. Change the example slightly (different filename, different flag) and
   run it again to see how the output changes.
4. Move to the next section only once the previous commands feel natural.

## Top Practice Platforms

Reading documentation is not enough. Real skill comes from hands-on
practice. The following platforms are excellent, widely respected places
to practice Linux and command-line skills outside of this module:

- **OverTheWire (Bandit)**
  A free wargame designed specifically to teach the basics of Linux
  command-line usage through a series of levels. Each level requires
  finding a password to log in to the next level using SSH. This is
  considered the standard starting point for beginners in offensive
  security. Website: https://overthewire.org/wargames/bandit/

- **LinuxJourney**
  A free, structured, beginner-friendly resource that teaches Linux
  concepts (filesystem, permissions, users, processes, networking) with
  short lessons and small interactive quizzes. Good for building
  theoretical understanding alongside practical work.
  Website: https://linuxjourney.com/

- **CMD Challenge**
  A set of small, timed command-line challenges that focus on solving
  practical problems using standard Unix/Linux commands such as `grep`,
  `sed`, `awk`, and `find`. Useful for sharpening speed and command
  combinations. Website: https://cmdchallenge.com/

- **SadServers**
  Realistic Linux server troubleshooting scenarios. Each challenge drops
  the learner into a broken or misconfigured server and asks them to fix
  a specific problem. This builds real sysadmin-style problem solving,
  which is directly useful when working with target machines and lab
  environments. Website: https://sadservers.com/

- **TryHackMe**
  A guided, beginner-friendly cybersecurity training platform with rooms
  covering Linux fundamentals, Kali Linux usage, privilege escalation,
  and full penetration testing paths. It combines short theory sections
  with hands-on virtual machines directly in the browser.
  Website: https://tryhackme.com/

It is recommended to complete at least the OverTheWire Bandit wargame
alongside this module, since it directly reinforces the commands taught in
files 03 and 04.
