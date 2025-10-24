# Linux Fundamentals Cheatsheet

**Author:** Josh Cerutti  
**Source:** TryHackMe — Linux Fundamentals 1–3  
**Purpose:** A concise reference of essential Linux commands and concepts for cybersecurity and system administration.

---

## File System Navigation

| Command | Description | Example |
|----------|--------------|----------|
| `echo` | Output any text we provide | `echo "hello world"`
| `pwd` | Prints the current working directory | `pwd` |
| `ls` | Lists files and directories | `ls -la` |
| `cd` | Change directory | `cd /etc` |

---
## Shell Operators 

| Command | Description | Example |
|----------|--------------|----------|
| `&` | This operator allows you to run commands in the background of your terminal. | `command1 &` |
| `&&` | This operator allows you to run multiple commands so long as the first command is true 
| `mkdir newfolder && cd newfolder` |

## File Operations

| Command | Description | Example |
|----------|--------------|----------|
| `cat` | Display contents of a file | `cat file.txt` |
| `touch` | Create an empty file | `touch notes.txt` |
| `cp` | Copy files or directories | `cp file1 file2` |
| `mv` | Move or rename files | `mv old.txt new.txt` |
| `rm` | Remove files | `rm file.txt` |
| `file` | Determine the type of a file | `file note`
| `mkdir` | make directory | `mkdir name_dir` |
| `rmdir` | Remove empty directories | `rmdir testdir` |

---

## Viewing and Filtering

| Command | Description | Example |
|----------|--------------|----------|
| `head` | Show first lines of a file | `head -n 10 file.txt` |
| `tail` | Show last lines of a file | `tail -n 10 file.txt` |
| `find` | Find specific files | `find -name file.txt` |
| `grep` | Search for patterns in text | `grep "root" /etc/passwd` |
| `awk` | Process and extract text fields | `awk -F: '{print $1}' /etc/passwd` |
| `cut` | Cut text by field delimiter | `cut -d: -f1 /etc/passwd` |

---

## User & Permission Management

| Command | Description | Example |
|----------|--------------|----------|
| `whoami` | Display current username | `whoami` |
| `id` | Show user ID and group info | `id` |
| `adduser` | Create new user | `sudo adduser bob` |
| `passwd` | Change user password | `passwd bob` |
| `chmod` | Change file permissions | `chmod 755 script.sh` |
| `chown` | Change file owner | `sudo chown bob:bob file.txt` |

---

## Networking Basics

| Command | Description | Example |
|----------|--------------|----------|
| `ifconfig` | Show network interfaces | `ifconfig` |
| `ping` | Test connectivity | `ping google.com` |
| `netstat` | Display network connections | `netstat -tuln` |
| `ss` | Modern replacement for netstat | `ss -tuln` |
| `scp` | Copy files over SSH | `scp file.txt user@remote:/home/user/` |
| `ssh` | Connect to remote host | `ssh user@ip_address` |

---

## System Info & Processes

| Command | Description | Example |
|----------|--------------|----------|
| `uname -a` | Display system information | `uname -a` |
| `top` | Show running processes | `top` |
| `ps` | List running processes | `ps aux` |
| `kill` | Terminate a process by PID | `kill 1234` |
| `df -h` | Show disk usage | `df -h` |
| `free -h` | Show memory usage | `free -h` |

---

## Tips

- Use `man <command>` to view manual pages (e.g., `man ls`)
- `>` overwrites output to a file, while `>>` appends
- Combine commands with pipes `|` (e.g., `ls -l | grep ".txt"`)
- The -R flag is used to remove directories and all their contents. 
- Always use `sudo` carefully!

---

### Notes to Self
`find` command is very useful when locating known named files. What can we do if we do not know the name?
  If we do NOT know the name of a file we wish to use `find` with, we can use a Wildcard (*) 
  to search for anything that has the '.txt' file name with: 'find -name *.txt'


`>` (Redirection) VS `>>` (Append)
The ">" command functions as an overwrite. For example, `echo "Hello World" > greetings.txt` will:
  1). create the text file "greetings.txt" if it does not exist 
  2). redirects the output into "greetings.txt" and 
  3). will overwrite any existing text withing "greetings.txt"

The `>>` command will also redirect specified outputs to a file and will ADD to the end of the file:
  1). EX: `echo "hello world" >> greetings.txt` will add "hello world" to the text file
  2). Therefore, just like "hello world" if we `echo "line 1" >> greetings.txt` and
  `echo "line 2" >> greetings.txt`, we will generate "line 1" and "line 2"

  The Key Difference to these functions is ">>" will not overwrite the existing file with the output
  *⚠️Disclaimer⚠️* There is no going back once ">" is used. Even if by accident!

```markdown
Example:
- `grep` can search recursively with `-r`
- `/etc/passwd` stores user account information
- `/etc/shadow` contains user account information
