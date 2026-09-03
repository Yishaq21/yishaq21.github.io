---
title: Bash | Programacion
description: Learn Bash basics
date: 2026-09-20 10:00:0 +0000
categories: [Programming, Bash]
tags: [Bash, Programming]
pin: false
mermaid: true
---
# Bash 

Notes to review Bash concepts, syntax, and short examples

---

# 1. What is Bash?

**Bash** (Bourne Again SHell) is a **Unix shell** and command-line interpreter, widely used on Linux systems.

Used for:

* Executing commands
* Managing files and directories
* Working with processes
* Automating repetitive tasks
* Analyzing logs
* Managing permissions
* Creating scripts

```bash
echo "Hello World"
```

### What is a shell?

A **shell** is a program that lets you interact with the operating system using commands. Examples: Bash, Zsh, Fish, PowerShell.

---

# 2. Bash Scripts

A Bash script is a **text file containing a sequence of commands**.

```bash
#!/bin/bash

echo "Hello World"
echo "This is my first Bash script"
```

The first line (`#!/bin/bash`) is the **shebang** — it tells the OS which interpreter to use.

## Running a script

```bash
bash script.sh
```

Or make it executable:

```bash
chmod +x script.sh
./script.sh
```

---

# 3. Comments

```bash
#!/bin/bash

# This is a comment
echo "Hello"
```

Everything after `#` on that line is ignored.

---

# 4. Variables

```bash
name="Isaac"
age=27

echo "$name"
echo "$age"
```

**No spaces around `=`.**

Correct: `name="Isaac"`
Incorrect: `name = "Isaac"`

## Access

```bash
echo "$name"
echo "${name}"          # useful next to other text
echo "${name}_user"
```

## Quoting

```bash
filename="my file.txt"
echo "$filename"
```

Without quotes, spaces can cause unexpected behavior.

---

# 5. Environment Variables

```bash
echo "$HOME"
echo "$USER"
echo "$PATH"
```

| Variable    | Meaning                           |
| ----------- | ---------------------------------- |
| `$HOME`     | User's home directory             |
| `$USER`     | Current username                  |
| `$PATH`     | Directories searched for commands |
| `$PWD`      | Current directory                 |
| `$SHELL`    | Current shell                     |
| `$HOSTNAME` | System hostname                   |

View all: `env` or `printenv`

---

# 6. User Input

```bash
read -p "Enter your name: " name
echo "Hello $name"
```

---

# 7. Command Substitution

Stores a command's output in a variable.

```bash
current_user=$(whoami)
current_directory=$(pwd)
date_now=$(date)
```

---

# 8. Data Types

Bash isn't strongly typed — almost everything is treated as **strings**, though it supports integer arithmetic.

```bash
result=$((10 + 5))
echo "$result"       # 15
```

`number=10` and `text="10"` are internally treated as text, unless used inside an arithmetic operation.

---

# 9. Arithmetic Operators

```bash
$(( expression ))
```

```bash
a=10
b=5

sum=$((a + b))
difference=$((a - b))
multiplication=$((a * b))
division=$((a / b))
remainder=$((a % b))
```

| Operator | Meaning        |
| -------- | -------------- |
| `+`      | Addition       |
| `-`      | Subtraction    |
| `*`      | Multiplication |
| `/`      | Division       |
| `%`      | Remainder      |

```bash
if (( 10 > 5 )); then
    echo "10 is greater"
fi
```

---

# 10. Strings

```bash
message="Hello World"
echo "$message"
```

## Length

```bash
echo "${#message}"      # 5 for "Hello"
```

## Manipulation

```bash
text="Hello World"
echo "${text/World/Bash}"    # Hello Bash

text="HELLO"
echo "${text,,}"              # lowercase

text="hello"
echo "${text^^}"               # uppercase
```

---

# 11. Comparisons

## Integers

| Operator | Meaning               |
| -------- | --------------------- |
| `-eq`    | Equal                 |
| `-ne`    | Not equal             |
| `-gt`    | Greater than          |
| `-lt`    | Less than             |
| `-ge`    | Greater than or equal |
| `-le`    | Less than or equal    |

```bash
if [ "$age" -ge 18 ]; then
    echo "Adult"
fi
```

## Strings

| Operator | Meaning             |
| -------- | -------------------- |
| `=`      | Equal                |
| `!=`     | Not equal            |
| `-z`     | String is empty      |
| `-n`     | String is not empty  |

```bash
if [ "$username" = "Isaac" ]; then
    echo "User found"
fi
```

---

# 12. File Tests

| Operator | Meaning                      |
| -------- | ------------------------------ |
| `-f`     | Regular file exists           |
| `-d`     | Directory exists              |
| `-e`     | Path exists                   |
| `-r`     | File is readable              |
| `-w`     | File is writable              |
| `-x`     | File is executable            |
| `-s`     | File exists and is not empty  |

```bash
if [ -f "$file" ]; then
    echo "File exists"
else
    echo "File does not exist"
fi
```

---

# 13. Conditionals

```bash
if [ "$age" -lt 18 ]; then
    echo "Minor"
elif [ "$age" -lt 65 ]; then
    echo "Adult"
else
    echo "Senior"
fi
```

Closed with `fi`.

---

# 14. Logical Operators

## `&&` (AND)

```bash
[ -f "log.txt" ] && echo "File exists"
```

## `||` (OR)

```bash
[ -f "config.txt" ] || echo "File not found"
```

## `!` (negation)

```bash
if [ ! -f "config.txt" ]; then
    echo "Config does not exist"
fi
```

---

# 15. `case`

```bash
read -p "Enter an option: " option

case "$option" in
    start)
        echo "Starting service"
        ;;
    stop)
        echo "Stopping service"
        ;;
    restart)
        echo "Restarting service"
        ;;
    *)
        echo "Unknown option"
        ;;
esac
```

---

# 16. `for`

```bash
for user in Isaac Maria David; do
    echo "User: $user"
done
```

## Looping through files

```bash
for file in *.log; do
    echo "Processing: $file"
done
```

---

# 17. `while`

```bash
count=1
while [ "$count" -le 5 ]; do
    echo "$count"
    count=$((count + 1))
done
```

---

# 18. `until`

Runs while the condition is **false** (opposite logic of `while`).

```bash
count=1
until [ "$count" -gt 5 ]; do
    echo "$count"
    count=$((count + 1))
done
```

---

# 19. `break`, `continue`

```bash
for number in 1 2 3 4 5; do
    if [ "$number" -eq 3 ]; then
        break
    fi
    echo "$number"
done
```

```bash
for number in 1 2 3 4 5; do
    if [ "$number" -eq 3 ]; then
        continue
    fi
    echo "$number"
done
```

---

# 20. Functions

```bash
check_disk() {
    echo "Checking disk..."
}

check_disk
```

## Parameters

```bash
greet() {
    echo "Hello $1"
}

greet "Isaac"
```

## Multiple parameters

```bash
add_numbers() {
    result=$(( $1 + $2 ))
    echo "$result"
}

add_numbers 10 5    # 15
```

## `return`

`return` gives an **exit status** (0–255), not an arbitrary value.

```bash
check_file() {
    if [ -f "$1" ]; then
        return 0
    else
        return 1
    fi
}

if check_file "logs.txt"; then
    echo "File exists"
fi
```

---

# 21. Script Arguments

```bash
#!/bin/bash
echo "First argument: $1"
echo "Second argument: $2"
```

```bash
./script.sh hello world
```

| Variable | Meaning                         |
| -------- | -------------------------------- |
| `$0`     | Script name                     |
| `$1`     | First argument                  |
| `$2`     | Second argument                 |
| `$#`     | Number of arguments             |
| `$@`     | All arguments                   |
| `$?`     | Exit status of previous command |

---

# 22. Exit Status

```text
0 = success
non-zero = failure or another condition
```

```bash
ls /tmp
echo "$?"
```

```bash
if ls /tmp > /dev/null 2>&1; then
    echo "Command succeeded"
else
    echo "Command failed"
fi
```

---

# 23. `&&` and `||` for Error Handling

Bash doesn't have `try/except`. Instead, it relies on exit statuses and conditional execution.

```bash
mkdir backup && echo "Backup directory created"
mkdir backup || echo "Could not create directory"
mkdir backup && echo "Success" || echo "Failed"
```

---

# 24. `set -e`, `set -u`, `set -o pipefail`

```bash
set -e              # stop the script if a command fails
set -u               # treat unset variables as errors
set -o pipefail      # fail if any command in a pipeline fails
```

Common combination:

```bash
set -euo pipefail
```

These have edge cases — worth understanding the script's behavior before using them blindly.

---

# 25. Reading Files

```bash
while IFS= read -r line; do
    echo "$line"
done < "data.txt"
```

`-r` prevents backslashes from being interpreted as escapes. `IFS=` prevents leading/trailing whitespace from being trimmed on each line.

---

# 26. Creating and Writing Files

```bash
touch data.txt                    # create empty file
echo "Hello World" > data.txt     # overwrite
echo "Another line" >> data.txt   # append
cat data.txt                      # read
```

| Operator | Meaning            |
| -------- | ------------------- |
| `>`      | Write/overwrite     |
| `>>`     | Append              |
| `<`      | Use file as input   |

---

# 27. Pipes

```bash
ls | grep ".log"
ps aux | grep nginx
```

The output of the first command becomes the input of the second.

---

# 28. Redirection

```bash
ls > files.txt                   # stdout
ls /invalid 2> errors.txt        # stderr
command > output.txt 2> errors.txt
command > output.txt 2>&1        # everything together
```

---

# 29. grep

```bash
grep "ERROR" application.log
grep -i "error" application.log      # case-insensitive
grep -n "ERROR" application.log      # with line numbers
grep -v "INFO" application.log       # inverted (does NOT contain)
grep -c "FAILED" application.log     # count matches
```

---

# 30. Regex with grep

```bash
grep -E "ERROR|FAILED|CRITICAL" application.log
```

Extract IPs (a pattern, not full validation):

```bash
grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}' application.log
```

---

# 31. cut

```bash
echo "Isaac:27:Student" | cut -d ":" -f 1
```

`-d ":"` = delimiter, `-f 1` = first field.

---

# 32. awk

```bash
echo "Isaac 27 Student" | awk '{print $1}'   # Isaac
echo "Isaac 27 Student" | awk '{print $2}'   # 27
```

Log example:

```bash
awk '{print $1}' login.log
```

---

# 33. sed

```bash
echo "Hello World" | sed 's/World/Bash/'    # Hello Bash
sed 's/old/new/g' file.txt                   # replace all occurrences
```

---

# 34. find

```bash
find /var/log -name "*.log"
find /var/log -type f -mtime -1               # modified in the last day
find / -type f -size +100M 2>/dev/null        # larger than 100 MB
find /path -type f -executable
```

---

# 35. File and Directory Commands

| Command | Purpose                 |
| ------- | ------------------------- |
| `pwd`   | Show current directory   |
| `ls`    | List files               |
| `cd`    | Change directory         |
| `mkdir` | Create directory         |
| `touch` | Create file              |
| `cp`    | Copy                     |
| `mv`    | Move/rename              |
| `rm`    | Remove                   |
| `cat`   | Display file             |
| `less`  | Read interactively       |
| `head`  | Beginning of file        |
| `tail`  | End of file              |

---

# 36. tail

```bash
tail application.log
tail -f application.log          # real-time monitoring
tail -f /var/log/auth.log
```

---

# 37. head

```bash
head application.log
head -n 20 application.log
```

---

# 38. Permissions

| Permission | Meaning |
| ---------- | ------- |
| `r`        | Read    |
| `w`        | Write   |
| `x`        | Execute |

Apply to: user/owner, group, others.

```text
-rwxr-xr--
Owner:  rwx
Group:  r-x
Others: r--
```

---

# 39. chmod

```bash
chmod +x script.sh
chmod 755 script.sh
```

```text
7 = rwx, 5 = r-x, 5 = r-x
755 = owner rwx, group r-x, others r-x
```

---

# 40. chown

```bash
sudo chown user:user file.txt
```

---

# 41. sudo

```bash
sudo systemctl restart nginx
sudo cat /var/log/auth.log
```

Use elevated privileges only when necessary.

---

# 42. Processes

```bash
ps
ps aux
top
htop
ps aux | grep nginx
```

---

# 43. kill

```bash
kill 1234           # default signal (TERM)
kill -15 1234         # normal termination request
kill -9 1234           # forced (SIGKILL) — use only if normal termination fails
```

---

# 44. Networking Commands

| Command      | Purpose                  |
| ------------ | -------------------------- |
| `ip`         | Network configuration    |
| `ping`       | Test connectivity        |
| `ss`         | View sockets/connections |
| `curl`       | HTTP requests             |
| `wget`       | Download resources       |
| `dig`        | DNS queries               |
| `hostname`   | Show hostname             |
| `traceroute` | Trace network path        |

```bash
ip addr
ping 8.8.8.8
ss -tuln
curl https://example.com
```

---

# 45. System Information

```bash
whoami        # current user
hostname      # hostname
uname -a      # system info
uptime        # how long the system has been running
df -h         # disk usage
free -h       # memory usage
du -sh /var/log   # size of a directory
```

---

# 46. Cron Jobs

```bash
crontab -l    # view
crontab -e    # edit
```

```text
0 * * * * /home/user/check_disk.sh    # every hour, minute 0
0 2 * * * /home/user/backup.sh         # every day at 2:00 AM
```

---

# 47. Script Security

Good practices:

* Quote variables
* Validate user input
* Avoid unnecessary `sudo`
* Avoid executing untrusted input
* Use absolute paths when appropriate
* Check exit statuses
* Protect sensitive files
* Don't store passwords directly in scripts

## Dangerous example

```bash
command="$user_input"
eval "$command"
```

`eval` can let user-controlled input be interpreted as shell code.

## Better approach

```bash
case "$option" in
    start) systemctl start myservice ;;
    stop)  systemctl stop myservice ;;
    *)     echo "Invalid option" ;;
esac
```

---

# 48. Bash and Regex

```bash
grep -E "FAILED|ERROR|CRITICAL" application.log
grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}' application.log
```

Combinable with `grep`, `sed`, `awk`, `find`. Useful for: log analysis, detecting failed logins, finding IPs, extracting usernames, searching suspicious patterns.

---

# 49. Example — Failed Login Attempts

Sample log:

```text
192.168.1.10 FAILED
192.168.1.20 SUCCESS
192.168.1.10 FAILED
192.168.1.30 FAILED
192.168.1.10 FAILED
```

```bash
grep "FAILED" login.log
grep "FAILED" login.log | awk '{print $1}'
grep "FAILED" login.log | awk '{print $1}' | sort | uniq -c
```

Output:

```text
3 192.168.1.10
1 192.168.1.30
```

---

# 50. Security Automation Script

```bash
#!/bin/bash

LOG_FILE="login.log"

if [ ! -f "$LOG_FILE" ]; then
    echo "Log file not found."
    exit 1
fi

echo "Failed login attempts:"
echo

grep "FAILED" "$LOG_FILE" | awk '{print $1}' | sort | uniq -c
```

Steps: define the log file → check it exists → search `FAILED` → extract IP → sort → count duplicates.

---

# 51. Monitoring Example

```bash
#!/bin/bash

MEMORY=$(free | awk '/Mem:/ {printf "%.0f", $3/$2 * 100}')

echo "Memory usage: ${MEMORY}%"

if [ "$MEMORY" -ge 85 ]; then
    echo "WARNING: High memory usage"
else
    echo "Memory usage is normal"
fi
```

Can be combined with: cron, logging, email, monitoring systems, alerting tools.

---

# 52. Bash vs Python

| Bash                                 | Python                                       |
| ------------------------------------- | --------------------------------------------- |
| Excellent for Linux commands         | Better for complex logic                     |
| Great for system administration      | Better for larger programs                   |
| Easy command pipelines               | Rich libraries                               |
| Excellent for shell automation       | Better data structures                       |
| Great for quick scripts              | Better maintainability for complex projects  |
| Strong integration with Linux tools  | Better for APIs and applications             |

```bash
grep "ERROR" application.log
```

```python
with open("application.log") as file:
    for line in file:
        if "ERROR" in line:
            print(line)
```

---

# 53. Common Commands — Quick Reference

| Command     | Purpose                 |
| ----------- | -------------------------- |
| `pwd`       | Current directory        |
| `ls`        | List files               |
| `cd`        | Change directory         |
| `mkdir`     | Create directory         |
| `touch`     | Create file              |
| `cp`        | Copy                     |
| `mv`        | Move/rename              |
| `rm`        | Remove                   |
| `cat`       | Display file             |
| `less`      | Read file                |
| `head`      | First lines              |
| `tail`      | Last lines               |
| `grep`      | Search text              |
| `awk`       | Process fields/text      |
| `sed`       | Transform text           |
| `cut`       | Extract fields           |
| `find`      | Search files             |
| `sort`      | Sort output              |
| `uniq`      | Remove/count duplicates  |
| `wc`        | Count lines/words        |
| `chmod`     | Change permissions       |
| `chown`     | Change ownership         |
| `ps`        | View processes           |
| `kill`      | Send process signal      |
| `ip`        | Network information      |
| `ss`        | Network sockets          |
| `curl`      | HTTP requests            |
| `df`        | Disk usage               |
| `free`      | Memory usage             |
| `systemctl` | Manage services          |
| `crontab`   | Schedule jobs            |

---

# 54. Bash vs Shell vs Terminal

* **Terminal**: the interface I use to interact with the system.
* **Shell**: interprets and executes commands.
* **Bash**: is one specific type of shell.

```text
Terminal → Shell → Bash → Commands / Scripts
```

---

# 55. Syntax to Remember

```bash
name="Isaac"                      # variable
echo "$name"                       # usage
if [ "$x" -eq 10 ]; then ... fi    # condition
for file in *.log; do ... done     # loop
check_file() { ... }                # function
echo "$1"                            # argument
user=$(whoami)                       # command substitution
result=$((10 + 5))                    # arithmetic
ps aux | grep nginx                    # pipe
echo "test" > file.txt                 # redirect
echo "test" >> file.txt                # append
exit 1                                  # exit
```

---

# 56. General Checklist

* What Bash is and what a shell is
* Shebang, comments
* Variables, environment variables
* User input, command substitution
* Arithmetic, comparisons
* `if`, `elif`, `else`, `case`
* `for`, `while`, `until`, `break`, `continue`
* Functions, function and script arguments
* Exit statuses, `&&`, `||`
* `set -euo pipefail`
* File handling, pipes, redirection
* `grep`, `awk`, `sed`, `cut`, `find`
* Permissions, `chmod`, `chown`, `sudo`
* Processes, networking commands
* Cron, basic regex
* Script security best practices

---

# 57. Full Reference Script

```bash
#!/bin/bash

LOG_FILE="login.log"

if [ ! -f "$LOG_FILE" ]; then
    echo "Log file not found."
    exit 1
fi

echo "Analyzing failed login attempts..."

grep "FAILED" "$LOG_FILE" \
    | awk '{print $1}' \
    | sort \
    | uniq -c

echo "Analysis completed."
```

```text
Variables → File validation → Conditionals → Exit status →
grep → awk → sort → uniq → Pipes → Automation
```

---
---

# 58. Going Further — Bash as a Programming Language

The section above covers the essentials. This part gathers the pieces of Bash that behave more like a real programming language — useful for writing more robust scripts, or to review when a more advanced concept slips my mind.

---

## 58.1 Arrays

Indexed arrays (ordered, like a list):

```bash
servers=("web01" "web02" "db01")

echo "${servers[0]}"        # web01
echo "${servers[@]}"        # all elements
echo "${#servers[@]}"       # number of elements (3)
```

```bash
for server in "${servers[@]}"; do
    echo "Checking $server"
done
```

Adding an element:

```bash
servers+=("db02")
```

---

## 58.2 Associative Arrays (Bash 4+)

Works like a dictionary: key → value.

```bash
declare -A status

status["web01"]="up"
status["web02"]="down"

echo "${status[web01]}"     # up

for host in "${!status[@]}"; do
    echo "$host is ${status[$host]}"
done
```

`declare -A` is required — without it, Bash creates a normal indexed array.

---

## 58.3 `[[ ]]` vs `[ ]`

`[[ ]]` is Bash's own, more powerful version of the classic `test` command (`[ ]`).

```bash
if [[ "$name" == "Isaac" && -n "$name" ]]; then
    echo "Match"
fi
```

Advantages of `[[ ]]`:

* Supports `&&`, `||`, and pattern matching directly
* Less strict quoting requirements for variables (though quoting is still good practice)
* Supports `=~` for regex matching

```bash
email="user@example.com"

if [[ "$email" =~ ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$ ]]; then
    echo "Valid format"
fi
```

---

## 58.4 Returning Data from a Function

`return` only gives an exit status (0–255). To get an actual **value** (a string or number) back, use `echo` + command substitution.

```bash
get_uptime() {
    local minutes=$(( $(cut -d. -f1 /proc/uptime) / 60 ))
    echo "$minutes"
}

result=$(get_uptime)
echo "Uptime: $result minutes"
```

### `local` variables

Inside functions, declare variables as `local` unless a global scope is actually needed — this avoids accidentally overwriting variables elsewhere in the script.

```bash
add() {
    local a=$1
    local b=$2
    echo $((a + b))
}
```

---

## 58.5 `getopts` — Command-Line Flags

For scripts with more than a couple of positional arguments, `getopts` allows real CLI-style flags (`-u user -f file -v`).

```bash
#!/bin/bash

while getopts "u:f:v" opt; do
    case "$opt" in
        u) user="$OPTARG" ;;
        f) file="$OPTARG" ;;
        v) verbose=true ;;
        *) echo "Usage: $0 -u user -f file [-v]"; exit 1 ;;
    esac
done

echo "User: $user"
echo "File: $file"
```

```bash
./script.sh -u isaac -f data.txt -v
```

---

## 58.6 Here-Documents (heredoc)

Lets you embed multi-line text (or generate files/configs) directly inside a script.

```bash
cat << EOF > report.txt
System report
User: $(whoami)
Date: $(date)
EOF
```

Variables expand inside the heredoc unless the delimiter is quoted:

```bash
cat << 'EOF'
This $variable will NOT be expanded.
EOF
```

---

## 58.7 `trap` — Signals and Cleanup

`trap` lets a script react to signals (like `Ctrl+C`) or run cleanup code no matter how it exits.

```bash
cleanup() {
    echo "Cleaning up temporary files..."
    rm -f /tmp/mytemp_*
}

trap cleanup EXIT

trap 'echo "Interrupted!"; exit 1' SIGINT
```

`EXIT` runs the function whenever the script ends (success, error, or interruption) — very useful in scripts that create temp files or lock files.

---

## 58.8 Debugging

```bash
bash -x script.sh
```

Prints every command as it executes, with variable values already substituted.

Can also be enabled for just part of a script:

```bash
set -x
# commands to debug
set +x
```

---

## 58.9 Arithmetic: `let`, `(( ))`, `expr`

```bash
let "sum = 5 + 3"
echo "$sum"          # 8

((count++))           # increment
((count += 5))         # add 5

expr 5 + 3             # older external command, rarely used today
```

`(( ))` is generally preferred in modern scripts for both arithmetic and numeric conditionals.

---

## 58.10 Modular Scripts with `source`

Lets you split code into reusable files and load them with `source` (or `.`).

`helpers.sh`:

```bash
#!/bin/bash

log() {
    echo "[$(date '+%Y-%m-%d %H:%M:%S')] $1"
}
```

`main.sh`:

```bash
#!/bin/bash

source ./helpers.sh

log "Script started"
```

---

## 58.11 Recursion Example

```bash
factorial() {
    local n=$1
    if (( n <= 1 )); then
        echo 1
    else
        local sub=$(factorial $((n - 1)))
        echo $((n * sub))
    fi
}

factorial 5   # 120
```

---

## 58.12 A More Complete Example

Combining arrays, associative arrays, functions that return values, `trap`, and safe flags:

```bash
#!/bin/bash
set -euo pipefail

declare -A HOST_STATUS
HOSTS=("8.8.8.8" "1.1.1.1" "192.0.2.1")

check_host() {
    local host=$1
    if ping -c 1 -W 1 "$host" &> /dev/null; then
        echo "up"
    else
        echo "down"
    fi
}

cleanup() {
    echo "Finished checking ${#HOSTS[@]} hosts."
}
trap cleanup EXIT

for host in "${HOSTS[@]}"; do
    HOST_STATUS["$host"]=$(check_host "$host")
done

for host in "${!HOST_STATUS[@]}"; do
    echo "$host -> ${HOST_STATUS[$host]}"
done
```

This script checks connectivity to several hosts, stores the result in an associative array, and prints a summary — combining arrays, functions that return data, `trap` for cleanup, and safe scripting flags (`set -euo pipefail`).

---

## 58.13 Advanced Checklist

* Indexed and associative arrays (`declare -A`)
* `[[ ]]` vs `[ ]`, including `=~` for regex
* Returning real values from functions via `echo` + command substitution
* Variable scoping with `local`
* `getopts` for CLI-style flags
* Heredocs (`<< EOF`)
* `trap` for cleanup and signal handling
* Debugging with `bash -x` / `set -x`
* `(( ))` and `let` for arithmetic and increments
* `source` for modular scripts
* Basic recursion (conceptual awareness)