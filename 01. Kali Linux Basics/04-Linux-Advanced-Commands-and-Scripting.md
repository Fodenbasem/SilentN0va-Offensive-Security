# Linux Advanced Commands and Scripting

## Introduction

This file builds on the basics from the previous file and introduces the
tools that are used constantly in real security work: filtering and
transforming text, chaining commands together, monitoring processes,
checking network configuration, and automating tasks with simple Bash
scripts. These are the exact same tools used to parse scan output, filter
log files, and automate repetitive testing steps during real engagements.

## 1. Advanced Text Filtering and Processing

### `grep` - Search Text Using Patterns

`grep` searches input (a file, or piped data) for lines matching a
pattern, and prints the matching lines.

```bash
$ grep "root" /etc/passwd
root:x:0:0:root:/root:/bin/bash

$ grep -i "ERROR" logfile.txt        # -i: case-insensitive search
$ grep -r "password" /etc/          # -r: recursive search through directories
$ grep -v "root" /etc/passwd        # -v: invert match, show lines that do NOT match
$ grep -n "admin" users.txt         # -n: show line numbers of matches
$ grep -c "Failed password" auth.log  # -c: count matching lines instead of printing them
$ grep -E "^[0-9]+" data.txt        # -E: use extended regular expressions
```

### `awk` - Pattern Scanning and Text Processing by Fields

`awk` processes text line by line, splitting each line into fields
(columns), by default separated by whitespace. It is extremely useful for
extracting specific columns of data.

```bash
$ cat /etc/passwd | awk -F: '{print $1}'    # Print only the first field (username),
                                              # -F: sets ":" as the field separator
root
daemon
bin
kali

$ ps aux | awk '{print $2, $11}'    # Print process ID and command name
```

`awk` can also filter by a condition before printing:

```bash
$ awk -F: '$3 >= 1000 {print $1}' /etc/passwd   # Print usernames with UID 1000 or higher
```

### `sed` - Stream Editor for Find and Replace

`sed` transforms text, most commonly used to find and replace text.

```bash
$ sed 's/old/new/' file.txt          # Replace the first occurrence of "old" with "new" per line
$ sed 's/old/new/g' file.txt         # Replace ALL occurrences on each line (g = global)
$ sed -i 's/old/new/g' file.txt      # -i: edit the file in place (saves the change)
$ sed -n '5,10p' file.txt            # Print only lines 5 through 10
```

### `cut` - Extract Sections (Columns) from Lines

```bash
$ cut -d: -f1 /etc/passwd       # -d: sets delimiter to ":", -f1 selects field 1
root
daemon
kali

$ cut -c1-5 file.txt            # Extract characters 1 through 5 from each line
```

### `sort` - Sort Lines of Text

```bash
$ sort names.txt                # Alphabetical sort
$ sort -n numbers.txt           # -n: numeric sort (correct for numbers, not alphabetical)
$ sort -r names.txt             # -r: reverse order
$ sort -u names.txt             # -u: sort and remove duplicate lines
```

### `uniq` - Filter Out Repeated Lines

`uniq` only removes **adjacent** duplicate lines, so input is almost
always sorted first.

```bash
$ sort access.log | uniq              # Remove duplicate lines
$ sort access.log | uniq -c           # -c: show a count of how many times each line appeared
$ sort access.log | uniq -d           # -d: show only lines that had duplicates
```

### `wc` - Word, Line, and Character Count

```bash
$ wc file.txt
  120  850 4820 file.txt
# Output order: lines, words, bytes(characters)

$ wc -l file.txt        # -l: only show line count
120 file.txt
```

### Practical Combination Example

Combining these tools is extremely common in real work. For example,
finding the top 5 most frequent IP addresses hitting a web server from an
access log:

```bash
$ awk '{print $1}' access.log | sort | uniq -c | sort -rn | head -n 5
```

This pipeline: extracts the first field (IP address) from every line,
sorts them, counts how many times each unique IP appears, sorts by that
count in reverse numeric order, then shows only the top 5.

## 2. Piping and I/O Redirection

Every Linux process has three standard data streams:

- **stdin** (standard input, file descriptor 0) - Input a program reads,
  by default from the keyboard.
- **stdout** (standard output, file descriptor 1) - Normal output a
  program produces, by default printed to the terminal.
- **stderr** (standard error, file descriptor 2) - Error messages a
  program produces, also by default printed to the terminal, but kept
  separate from stdout.

### Redirection Operators

```bash
$ echo "Hello World" > file.txt       # > : Redirect stdout to a file, OVERWRITING it
$ echo "Another line" >> file.txt     # >> : Redirect stdout, APPENDING to the file
$ sort < unsorted.txt                 # < : Use a file as stdin input for a command
$ command 2> errors.log               # 2> : Redirect only stderr to a file
$ command > output.log 2>&1           # Redirect both stdout and stderr into the same file
$ command > /dev/null 2>&1            # Discard all output, /dev/null is a special "null" device
```

### Piping with `|`

The pipe operator sends the stdout of one command directly into the stdin
of the next command, allowing small commands to be chained into a
powerful pipeline.

```bash
$ ps aux | grep firefox           # List all processes, filter for "firefox"
$ cat /etc/passwd | grep bash     # Show only users whose default shell is bash
$ ls -la | wc -l                  # Count how many files/directories are in the current folder
```

## 3. Process Management and Monitoring

### `ps` - Show Running Processes

```bash
$ ps aux
USER   PID  %CPU  %MEM    VSZ   RSS TTY   STAT START   TIME COMMAND
root     1   0.0   0.1  16800  9200 ?     Ss   09:00   0:02 /sbin/init
kali   842   0.2   1.5 345000 61000 pts/0 Sl   09:05   0:03 firefox
```

- `a` - Show processes for all users.
- `u` - Display in a user-friendly format with more detail (owner, CPU,
  memory).
- `x` - Include processes not attached to a terminal.

`PID` (Process ID) is the unique number identifying a running process,
used by other commands like `kill`.

### `top` - Real-Time Process Monitor

```bash
$ top
```

Shows a live, constantly updating view of running processes, sorted by
CPU usage by default, along with overall CPU and memory usage. Press `q`
to quit.

### `htop` - Improved, Interactive Process Monitor

An improved, more visual, and easier to use alternative to `top`. Not
always installed by default.

```bash
$ sudo apt install -y htop
$ htop
```

Supports mouse interaction, color-coded CPU/memory bars, and easier
process searching and killing (`F3` to search, `F9` to kill).

### `kill` and `killall` - Stop Running Processes

```bash
$ kill 842              # Send the default signal (TERM, ask to terminate gracefully) to PID 842
$ kill -9 842            # Send SIGKILL (force kill immediately, cannot be ignored)
$ killall firefox        # Kill all processes matching the name "firefox"
```

Common signals:

- `SIGTERM` (15, default) - Politely asks the process to shut down,
  allowing it to clean up first.
- `SIGKILL` (9) - Forcefully and immediately terminates the process, no
  cleanup, used when a process is unresponsive.

### Backgrounding Processes: `&`, `bg`, `fg`, `jobs`

```bash
$ long_running_scan.sh &      # Start a command in the background,
                                # terminal is immediately free for more commands
[1] 5321

$ jobs                        # List background jobs in the current shell
[1]+  Running    long_running_scan.sh &

$ fg %1                       # Bring job 1 back to the foreground
$ bg %1                       # Resume a stopped job in the background
```

Pressing `Ctrl+Z` while a foreground command is running suspends
(pauses) it, after which `bg` can resume it in the background, or `fg`
can bring it back to the foreground.

## 4. Networking Basics

### `ip a` - Show Network Interfaces and IP Addresses (Modern Standard)

```bash
$ ip a
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500
    inet 192.168.1.50/24 brd 192.168.1.255 scope global eth0
```

`ip a` (short for `ip address`) is the modern replacement for `ifconfig`
and shows every network interface along with its assigned IP address.

### `ifconfig` - Legacy Interface Configuration Tool

```bash
$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.50  netmask 255.255.255.0  broadcast 192.168.1.255
```

`ifconfig` is older and considered deprecated on many modern distributions
(may need `sudo apt install net-tools` on newer Kali versions), but it is
still widely recognized and used in scripts and documentation.

### `netstat` - Network Statistics (Legacy)

```bash
$ netstat -tulnp
```

- `-t` - TCP connections.
- `-u` - UDP connections.
- `-l` - Only show listening ports.
- `-n` - Show numeric addresses/ports instead of resolving names.
- `-p` - Show the program/PID using each connection (requires root for
  full detail).

### `ss` - Socket Statistics (Modern Replacement for netstat)

```bash
$ ss -tulnp
```

Uses the same flags as the `netstat` example above, but `ss` is faster
and is the actively maintained modern tool, recommended over `netstat` on
current systems.

### `ping` - Test Basic Network Connectivity

```bash
$ ping -c 4 8.8.8.8
```

Sends ICMP echo request packets to a target and waits for replies,
confirming basic network reachability and measuring round-trip time.
`-c 4` limits it to 4 packets (otherwise it runs continuously until
stopped with `Ctrl+C`).

### `traceroute` - Show the Network Path to a Target

```bash
$ traceroute google.com
```

Shows every network hop (router) the traffic passes through on its way
to the destination, useful for diagnosing routing issues and mapping
network paths.

### `curl` - Transfer Data From or To a URL

```bash
$ curl https://example.com                    # Fetch and print a webpage's HTML
$ curl -I https://example.com                  # -I: fetch only the HTTP headers
$ curl -o page.html https://example.com        # -o: save output to a file
$ curl -X POST -d "user=admin&pass=test" https://example.com/login  # Send a POST request
```

`curl` is one of the most used tools in security testing, for probing web
servers, APIs, and downloading files or exploit code directly from the
command line.

### `wget` - Download Files From the Web

```bash
$ wget https://example.com/file.zip
$ wget -O output.zip https://example.com/file.zip   # -O: specify the output filename
```

`wget` is focused specifically on downloading files (including recursively
downloading entire sites), while `curl` is a more general-purpose tool for
interacting with URLs and APIs.

## 5. Introduction to Bash Automation

Bash scripts allow a sequence of commands to be saved into a file and
executed together, automating repetitive tasks.

### Creating a Basic Script

Create a file called `scan_report.sh`:

```bash
#!/bin/bash
# A simple example script demonstrating variables, a loop, and a condition

# --- Variables ---
target="192.168.1.1"
log_file="scan_results.log"

echo "Starting checks for target: $target"

# --- Conditional statement (if/else) ---
if ping -c 1 -W 2 "$target" > /dev/null 2>&1; then
    echo "$target is UP" | tee -a "$log_file"
else
    echo "$target is DOWN or not responding" | tee -a "$log_file"
fi

# --- For loop: check a small range of ports using bash's own /dev/tcp ---
for port in 22 80 443; do
    if timeout 1 bash -c "echo > /dev/tcp/$target/$port" 2>/dev/null; then
        echo "Port $port is OPEN" | tee -a "$log_file"
    else
        echo "Port $port is CLOSED or filtered" | tee -a "$log_file"
    fi
done

# --- While loop example: count down from 5 ---
count=5
while [ "$count" -gt 0 ]; do
    echo "Countdown: $count"
    count=$((count - 1))
    sleep 1
done

echo "Script finished. Results saved in $log_file"
```

Breaking down the important parts:

- `#!/bin/bash` - Called a "shebang", the very first line of the script.
  It tells the system which interpreter should run this file, in this
  case Bash. It must be the first line, with no blank line above it.
- `#` - Starts a comment, ignored when the script runs, used to explain
  the code.
- `target="192.168.1.1"` - A variable assignment. No spaces are allowed
  around the `=` sign in Bash. Variables are read using a `$` prefix, for
  example `$target` or `"$target"` (the quotes are good practice to
  avoid problems with spaces in values).
- `if ... then ... else ... fi` - Conditional statement. `fi` (if
  spelled backward) closes the `if` block.
- `for port in 22 80 443; do ... done` - A for loop, iterating over a
  fixed list of values (22, 80, 443 in this case), running the block
  between `do` and `done` once for each value.
- `while [ condition ]; do ... done` - A while loop, repeating the block
  as long as the condition remains true.
- `$((count - 1))` - Arithmetic expansion, used to perform basic math in
  Bash.
- `tee -a` - A command that writes output to both the screen and a file
  at the same time, `-a` appends rather than overwriting.

### Making the Script Executable

By default, a newly created script cannot be run directly, it needs
execute permission first.

```bash
$ chmod +x scan_report.sh
```

### Running the Script

Once it has execute permission, run it using a relative or absolute path
(a script's directory is usually not in the system `PATH`, so just typing
its name alone will not work unless it is placed somewhere in `PATH`):

```bash
$ ./scan_report.sh
```

Alternatively, a script can always be run by explicitly calling the
interpreter, even without execute permission:

```bash
$ bash scan_report.sh
```

### A Second, Simpler Example: If/Else With User Input

```bash
#!/bin/bash
# Ask the user for a number and report whether it is even or odd

read -p "Enter a number: " number

if [ $((number % 2)) -eq 0 ]; then
    echo "$number is even"
else
    echo "$number is odd"
fi
```

- `read -p "prompt text" variable_name` - Displays a prompt and stores
  whatever the user types into the given variable.
- `$((number % 2))` - Arithmetic expansion using the modulo operator to
  find the remainder after dividing by 2.
- `-eq` - Numeric "equals" comparison inside `[ ]` test brackets. Other
  numeric comparisons include `-ne` (not equal), `-gt` (greater than),
  `-lt` (less than), `-ge` (greater or equal), `-le` (less or equal).

## Summary

This file covered advanced text processing with `grep`, `awk`, `sed`,
`cut`, `sort`, `uniq`, and `wc`, which together form the backbone of
filtering and analyzing text data such as logs and scan results. It
covered input/output redirection (`>`, `>>`, `<`) and piping (`|`), which
allow small, focused commands to be combined into powerful pipelines.
It covered process management with `ps`, `top`, `htop`, `kill`,
`killall`, and job control (`&`, `bg`, `fg`). It covered basic networking
commands (`ip a`, `ifconfig`, `netstat`, `ss`, `ping`, `traceroute`,
`curl`, `wget`) used constantly for reconnaissance and diagnostics.
Finally, it introduced Bash scripting fundamentals: variables, `if/else`
conditionals, `for` and `while` loops, and how to make a script
executable and run it. Mastering these tools is what turns manual,
repetitive command-line work into fast, repeatable, automated processes,
a core skill for any security professional.
