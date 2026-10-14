# Linux Commands & Hands-on Practice
## Beginner-friendly reference sheet

Use this as a command cheat sheet during the workshop and for practice later. Run commands in your own home directory unless the task says otherwise.

> **Safety:** Avoid running commands with `sudo` unless you understand what they do. Do not copy commands from the internet blindly. Commands like `rm -r` can permanently delete files.
# Linux Commands & Hands-on Practice
## Beginner-friendly reference sheet

Use this as a command cheat sheet during the workshop and for practice later. Run commands in your own home directory unless the task says otherwise.

> **Safety:** Avoid running commands with `sudo` unless you understand what they do. Do not copy commands from the internet blindly. Commands like `rm -r` can permanently delete files.

---

## 1. First commands

| Command | What it does | Try it |
|---|---|---|
| `whoami` | Shows your username | `whoami` |
| `pwd` | Shows your current directory | `pwd` |
| `date` | Shows date and time | `date` |
| `uname -a` | Shows kernel/system information | `uname -a` |
| `clear` | Clears the terminal screen | `clear` |
| `history` | Shows recently used commands | `history` |
| `man ls` | Opens the manual for `ls` | Press `q` to quit |
| `ls --help` | Shows help for a command | `ls --help` |

## 2. Navigate directories

| Command | What it does |
|---|---|
| `ls` | List files and folders |
| `ls -l` | Detailed listing |
| `ls -a` | Include hidden files |
| `ls -lh` | Detailed listing with readable file sizes |
| `pwd` | Print current directory |
| `cd foldername` | Enter a folder |
| `cd ..` | Go up one directory |
| `cd ~` | Go to your home directory |
| `cd /` | Go to the filesystem root |
| `cd -` | Return to the previous directory |

### Practice

```bash
pwd
ls
ls -la
cd ~
pwd
cd /
ls
cd -
pwd
```

## 3. Create, read, copy, move, and delete files

| Command | What it does |
|---|---|
| `mkdir practice` | Create a directory |
| `mkdir -p project/docs` | Create nested directories |
| `touch notes.txt` | Create an empty file, or update its timestamp |
| `cat notes.txt` | Display a file |
| `less notes.txt` | Read a file page by page; press `q` to quit |
| `head notes.txt` | Show the first 10 lines |
| `tail notes.txt` | Show the last 10 lines |
| `cp a.txt b.txt` | Copy a file |
| `cp a.txt folder/` | Copy a file into a folder |
| `mv old.txt new.txt` | Rename or move a file |
| `rm notes.txt` | Delete a file |
| `rmdir empty-folder` | Delete an empty directory |
| `file notes.txt` | Identify the file type |
| `wc -l notes.txt` | Count lines |
| `wc -w notes.txt` | Count words |

### Practice: make a tiny workspace

```bash
cd ~
mkdir linux-practice
cd linux-practice
mkdir docs backup
touch docs/notes.txt
echo "My first Linux practice" > docs/notes.txt
cat docs/notes.txt
cp docs/notes.txt backup/
mv backup/notes.txt backup/first-notes.txt
ls -R
```

**Check:** You should have `docs/notes.txt` and `backup/first-notes.txt`.

## 4. Write and append text

```bash
echo "Hello Linux"
echo "Line one" > notes.txt
echo "Line two" >> notes.txt
cat notes.txt
```

- `>` writes output to a file and **overwrites** its previous contents.
- `>>` adds output to the end of a file.
- Be careful: `>` can erase existing file contents.

### Practice

1. Create `todo.txt` with one line using `>`.
2. Add two more lines using `>>`.
3. Display the file with `cat`.
4. Count its lines with `wc -l todo.txt`.

## 5. Search for files and text

| Command | What it does |
|---|---|
| `find . -name "*.txt"` | Find `.txt` files below the current directory |
| `find ~ -type d -name "Downloads"` | Find directories named `Downloads` under your home directory |
| `grep "Linux" notes.txt` | Find lines containing `Linux` |
| `grep -n "Linux" notes.txt` | Also show matching line numbers |
| `grep -i "linux" notes.txt` | Search without case sensitivity |
| `grep -r "Linux" .` | Search recursively in files under the current directory |

### Practice

```bash
cd ~/linux-practice
echo "Linux is useful" > docs/topic.txt
echo "I am learning commands" >> docs/topic.txt
echo "linux works with files" >> docs/topic.txt
grep -in "linux" docs/topic.txt
find . -name "*.txt"
```

## 6. Understand paths

- `/` — filesystem root
- `~` — your home directory
- `.` — current directory
- `..` — parent directory
- `/tmp` — temporary files
- `/etc` — system configuration files
- `/dev` — device interfaces
- `/proc` — process and kernel information exposed by the kernel

### Practice

```bash
pwd
cd ~
pwd
ls /tmp
ls /dev | head
cat /proc/meminfo | head
```

Some files under `/proc` and `/dev` are special interfaces, not ordinary documents.

## 7. Permissions

```bash
ls -l
chmod u+x script.sh
chmod 644 notes.txt
chmod 755 script.sh
```

In `ls -l` output, permissions are shown as `r` (read), `w` (write), and `x` (execute).

- `chmod u+x script.sh` adds execute permission for the file owner.
- `chmod 644 notes.txt` gives the owner read/write and others read-only access.
- `chmod 755 script.sh` gives the owner read/write/execute and others read/execute.

### Make and run a simple script

```bash
cd ~/linux-practice
cat > hello.sh <<'EOF'
#!/bin/bash
echo "Hello from a Linux script!"
whoami
pwd
EOF
chmod u+x hello.sh
./hello.sh
```

## 8. Processes and system information

| Command | What it does |
|---|---|
| `ps` | Shows processes associated with the current terminal |
| `ps aux` | Shows a broader process list |
| `top` | Live process/resource view; press `q` to quit |
| `free -h` | Memory usage |
| `df -h` | Disk-space usage |
| `du -sh foldername` | Approximate size of a folder |
| `uptime` | Time since boot and load averages |
| `hostname` | Shows the computer's hostname |
| `lscpu` | CPU information |
| `lsblk` | Lists block devices and partitions |

### Practice

```bash
whoami
hostname
uptime
free -h
df -h
ps aux | head
```

## 9. Pipes and redirection

```bash
ls -l > file-list.txt
echo "another line" >> file-list.txt
cat file-list.txt
ps aux | head
cat /proc/meminfo | grep MemAvailable
ls /dev | wc -l
```

- `|` sends one command's output to another command.
- `>` redirects output to a file, replacing its contents.
- `>>` appends output to a file.
- `wc -l` counts lines; `wc -w` counts words; `wc -c` counts bytes.

## 10. Networking basics

```bash
ping -c 4 example.com
ip addr
ip route
```

- `ping -c 4 example.com` sends four test packets; network policies or firewalls may block responses.
- `ip addr` shows network interfaces and addresses.
- `ip route` shows routing information.

## 11. Package management on Ubuntu/Linux Mint

```bash
apt search package-name
apt show package-name
sudo apt update
sudo apt install package-name
```

- `apt update` refreshes the package lists; it does not upgrade installed apps.
- `apt install` installs software.
- `sudo` runs a command with elevated privileges. Enter your password only when you trust the command.
- Ask your instructor before installing or removing packages during a workshop.

---

# Hands-on Challenges

Try these yourself before looking at the sample solution.

## Challenge 1 — Your first workspace

1. Go to your home directory.
2. Create `linux-lab`.
3. Inside it, create `notes`, `scripts`, and `backup`.
4. Create `notes/day1.txt`.
5. Put two lines of text in it.
6. Display the file and list the directory structure.

**Useful commands:** `cd`, `mkdir`, `touch`, `echo`, `cat`, `ls -R`

## Challenge 2 — Copy, rename, and find

1. Copy `notes/day1.txt` into `backup`.
2. Rename the copied file to `day1-copy.txt`.
3. Find all `.txt` files inside `linux-lab`.
4. Count the lines in the original file.

**Useful commands:** `cp`, `mv`, `find`, `wc -l`

## Challenge 3 — Search a file

1. Create a file containing these lines:
   - `Linux is open source`
   - `I use the terminal`
   - `Linux runs on servers`
   - `Practice makes progress`
2. Search for the word `Linux`.
3. Repeat the search without caring about uppercase/lowercase.
4. Display line numbers for matches.

**Useful commands:** `echo`, `>`, `>>`, `grep`, `grep -i`, `grep -n`

## Challenge 4 — Make a script

1. Create `scripts/greeting.sh`.
2. Make it print your name, current directory, and current date.
3. Add execute permission.
4. Run it.

**Useful commands:** `cat`, `chmod`, `./script-name`

## Challenge 5 — Inspect your system

Find out:
- Your username
- Your current directory
- Your Linux kernel version
- Your available memory
- Your available disk space
- How long the computer has been running

**Useful commands:** `whoami`, `pwd`, `uname -r`, `free -h`, `df -h`, `uptime`

## Challenge 6 — Pipes

Write commands that:
1. Count how many entries are listed in `/dev`.
2. Show only lines containing `Mem` from `/proc/meminfo`.
3. Display the first five processes from `ps aux`.

**Useful commands:** `ls`, `wc -l`, `grep`, `head`, `|`

---

# Sample Solutions

Try the challenges first. These are examples; equivalent commands are fine.

## Challenge 1

```bash
cd ~
mkdir -p linux-lab/{notes,scripts,backup}
touch linux-lab/notes/day1.txt
echo "Today I learned Linux commands." > linux-lab/notes/day1.txt
echo "I will keep practicing." >> linux-lab/notes/day1.txt
cat linux-lab/notes/day1.txt
ls -R linux-lab
```

## Challenge 2

```bash
cp ~/linux-lab/notes/day1.txt ~/linux-lab/backup/
mv ~/linux-lab/backup/day1.txt ~/linux-lab/backup/day1-copy.txt
find ~/linux-lab -name "*.txt"
wc -l ~/linux-lab/notes/day1.txt
```

## Challenge 3

```bash
cat > ~/linux-lab/notes/search.txt <<'EOF'
Linux is open source
I use the terminal
Linux runs on servers
Practice makes progress
EOF

grep "Linux" ~/linux-lab/notes/search.txt
grep -i "linux" ~/linux-lab/notes/search.txt
grep -in "linux" ~/linux-lab/notes/search.txt
```

## Challenge 4

```bash
cat > ~/linux-lab/scripts/greeting.sh <<'EOF'
#!/bin/bash
echo "Hello, student!"
whoami
pwd
date
EOF

chmod u+x ~/linux-lab/scripts/greeting.sh
~/linux-lab/scripts/greeting.sh
```

## Challenge 5

```bash
whoami
pwd
uname -r
free -h
df -h
uptime
```

## Challenge 6

```bash
ls /dev | wc -l
grep "Mem" /proc/meminfo
ps aux | head -n 6
```

---

# Quick command checklist

- [ ] `pwd`, `ls`, `cd`
- [ ] `mkdir`, `touch`, `cat`
- [ ] `cp`, `mv`, `rm`
- [ ] `echo`, `>`, `>>`
- [ ] `find`, `grep`, `wc`
- [ ] `chmod`, run a script
- [ ] `ps`, `top`, `free`, `df`, `uptime`
- [ ] `|` pipes and output redirection
- [ ] `ping`, `ip addr`, `ip route`

## Good practice habits

1. Practice inside `~/linux-practice` or another folder you created.
2. Use `ls` before deleting or moving files.
3. Read command help with `command --help` or `man command`.
4. Be cautious with `sudo`, `rm -r`, and commands copied from unknown sources.
5. Make a guess about what a command will do, run it, then verify the result.
---

## 1. First commands

| Command | What it does | Try it |
|---|---|---|
| `whoami` | Shows your username | `whoami` |
| `pwd` | Shows your current directory | `pwd` |
| `date` | Shows date and time | `date` |
| `uname -a` | Shows kernel/system information | `uname -a` |
| `clear` | Clears the terminal screen | `clear` |
| `history` | Shows recently used commands | `history` |
| `man ls` | Opens the manual for `ls` | Press `q` to quit |
| `ls --help` | Shows help for a command | `ls --help` |

## 2. Navigate directories

| Command | What it does |
|---|---|
| `ls` | List files and folders |
| `ls -l` | Detailed listing |
| `ls -a` | Include hidden files |
| `ls -lh` | Detailed listing with readable file sizes |
| `pwd` | Print current directory |
| `cd foldername` | Enter a folder |
| `cd ..` | Go up one directory |
| `cd ~` | Go to your home directory |
| `cd /` | Go to the filesystem root |
| `cd -` | Return to the previous directory |

### Practice

```bash
pwd
ls
ls -la
cd ~
pwd
cd /
ls
cd -
pwd
```

## 3. Create, read, copy, move, and delete files

| Command | What it does |
|---|---|
| `mkdir practice` | Create a directory |
| `mkdir -p project/docs` | Create nested directories |
| `touch notes.txt` | Create an empty file, or update its timestamp |
| `cat notes.txt` | Display a file |
| `less notes.txt` | Read a file page by page; press `q` to quit |
| `head notes.txt` | Show the first 10 lines |
| `tail notes.txt` | Show the last 10 lines |
| `cp a.txt b.txt` | Copy a file |
| `cp a.txt folder/` | Copy a file into a folder |
| `mv old.txt new.txt` | Rename or move a file |
| `rm notes.txt` | Delete a file |
| `rmdir empty-folder` | Delete an empty directory |
| `file notes.txt` | Identify the file type |
| `wc -l notes.txt` | Count lines |
| `wc -w notes.txt` | Count words |

### Practice: make a tiny workspace

```bash
cd ~
mkdir linux-practice
cd linux-practice
mkdir docs backup
touch docs/notes.txt
echo "My first Linux practice" > docs/notes.txt
cat docs/notes.txt
cp docs/notes.txt backup/
mv backup/notes.txt backup/first-notes.txt
ls -R
```

**Check:** You should have `docs/notes.txt` and `backup/first-notes.txt`.

## 4. Write and append text

```bash
echo "Hello Linux"
echo "Line one" > notes.txt
echo "Line two" >> notes.txt
cat notes.txt
```

- `>` writes output to a file and **overwrites** its previous contents.
- `>>` adds output to the end of a file.
- Be careful: `>` can erase existing file contents.

### Practice

1. Create `todo.txt` with one line using `>`.
2. Add two more lines using `>>`.
3. Display the file with `cat`.
4. Count its lines with `wc -l todo.txt`.

## 5. Search for files and text

| Command | What it does |
|---|---|
| `find . -name "*.txt"` | Find `.txt` files below the current directory |
| `find ~ -type d -name "Downloads"` | Find directories named `Downloads` under your home directory |
| `grep "Linux" notes.txt` | Find lines containing `Linux` |
| `grep -n "Linux" notes.txt` | Also show matching line numbers |
| `grep -i "linux" notes.txt` | Search without case sensitivity |
| `grep -r "Linux" .` | Search recursively in files under the current directory |

### Practice

```bash
cd ~/linux-practice
echo "Linux is useful" > docs/topic.txt
echo "I am learning commands" >> docs/topic.txt
echo "linux works with files" >> docs/topic.txt
grep -in "linux" docs/topic.txt
find . -name "*.txt"
```

## 6. Understand paths

- `/` — filesystem root
- `~` — your home directory
- `.` — current directory
- `..` — parent directory
- `/tmp` — temporary files
- `/etc` — system configuration files
- `/dev` — device interfaces
- `/proc` — process and kernel information exposed by the kernel

### Practice

```bash
pwd
cd ~
pwd
ls /tmp
ls /dev | head
cat /proc/meminfo | head
```

Some files under `/proc` and `/dev` are special interfaces, not ordinary documents.

## 7. Permissions

```bash
ls -l
chmod u+x script.sh
chmod 644 notes.txt
chmod 755 script.sh
```

In `ls -l` output, permissions are shown as `r` (read), `w` (write), and `x` (execute).

- `chmod u+x script.sh` adds execute permission for the file owner.
- `chmod 644 notes.txt` gives the owner read/write and others read-only access.
- `chmod 755 script.sh` gives the owner read/write/execute and others read/execute.

### Make and run a simple script

```bash
cd ~/linux-practice
cat > hello.sh <<'EOF'
#!/bin/bash
echo "Hello from a Linux script!"
whoami
pwd
EOF
chmod u+x hello.sh
./hello.sh
```

## 8. Processes and system information

| Command | What it does |
|---|---|
| `ps` | Shows processes associated with the current terminal |
| `ps aux` | Shows a broader process list |
| `top` | Live process/resource view; press `q` to quit |
| `free -h` | Memory usage |
| `df -h` | Disk-space usage |
| `du -sh foldername` | Approximate size of a folder |
| `uptime` | Time since boot and load averages |
| `hostname` | Shows the computer's hostname |
| `lscpu` | CPU information |
| `lsblk` | Lists block devices and partitions |

### Practice

```bash
whoami
hostname
uptime
free -h
df -h
ps aux | head
```

## 9. Pipes and redirection

```bash
ls -l > file-list.txt
echo "another line" >> file-list.txt
cat file-list.txt
ps aux | head
cat /proc/meminfo | grep MemAvailable
ls /dev | wc -l
```

- `|` sends one command's output to another command.
- `>` redirects output to a file, replacing its contents.
- `>>` appends output to a file.
- `wc -l` counts lines; `wc -w` counts words; `wc -c` counts bytes.

## 10. Networking basics

```bash
ping -c 4 example.com
ip addr
ip route
```

- `ping -c 4 example.com` sends four test packets; network policies or firewalls may block responses.
- `ip addr` shows network interfaces and addresses.
- `ip route` shows routing information.

## 11. Package management on Ubuntu/Linux Mint

```bash
apt search package-name
apt show package-name
sudo apt update
sudo apt install package-name
```

- `apt update` refreshes the package lists; it does not upgrade installed apps.
- `apt install` installs software.
- `sudo` runs a command with elevated privileges. Enter your password only when you trust the command.
- Ask your instructor before installing or removing packages during a workshop.

---

# Hands-on Challenges

Try these yourself before looking at the sample solution.

## Challenge 1 — Your first workspace

1. Go to your home directory.
2. Create `linux-lab`.
3. Inside it, create `notes`, `scripts`, and `backup`.
4. Create `notes/day1.txt`.
5. Put two lines of text in it.
6. Display the file and list the directory structure.

**Useful commands:** `cd`, `mkdir`, `touch`, `echo`, `cat`, `ls -R`

## Challenge 2 — Copy, rename, and find

1. Copy `notes/day1.txt` into `backup`.
2. Rename the copied file to `day1-copy.txt`.
3. Find all `.txt` files inside `linux-lab`.
4. Count the lines in the original file.

**Useful commands:** `cp`, `mv`, `find`, `wc -l`

## Challenge 3 — Search a file

1. Create a file containing these lines:
   - `Linux is open source`
   - `I use the terminal`
   - `Linux runs on servers`
   - `Practice makes progress`
2. Search for the word `Linux`.
3. Repeat the search without caring about uppercase/lowercase.
4. Display line numbers for matches.

**Useful commands:** `echo`, `>`, `>>`, `grep`, `grep -i`, `grep -n`

## Challenge 4 — Make a script

1. Create `scripts/greeting.sh`.
2. Make it print your name, current directory, and current date.
3. Add execute permission.
4. Run it.

**Useful commands:** `cat`, `chmod`, `./script-name`

## Challenge 5 — Inspect your system

Find out:
- Your username
- Your current directory
- Your Linux kernel version
- Your available memory
- Your available disk space
- How long the computer has been running

**Useful commands:** `whoami`, `pwd`, `uname -r`, `free -h`, `df -h`, `uptime`

## Challenge 6 — Pipes

Write commands that:
1. Count how many entries are listed in `/dev`.
2. Show only lines containing `Mem` from `/proc/meminfo`.
3. Display the first five processes from `ps aux`.

**Useful commands:** `ls`, `wc -l`, `grep`, `head`, `|`

---

# Sample Solutions

Try the challenges first. These are examples; equivalent commands are fine.

## Challenge 1

```bash
cd ~
mkdir -p linux-lab/{notes,scripts,backup}
touch linux-lab/notes/day1.txt
echo "Today I learned Linux commands." > linux-lab/notes/day1.txt
echo "I will keep practicing." >> linux-lab/notes/day1.txt
cat linux-lab/notes/day1.txt
ls -R linux-lab
```

## Challenge 2

```bash
cp ~/linux-lab/notes/day1.txt ~/linux-lab/backup/
mv ~/linux-lab/backup/day1.txt ~/linux-lab/backup/day1-copy.txt
find ~/linux-lab -name "*.txt"
wc -l ~/linux-lab/notes/day1.txt
```

## Challenge 3

```bash
cat > ~/linux-lab/notes/search.txt <<'EOF'
Linux is open source
I use the terminal
Linux runs on servers
Practice makes progress
EOF

grep "Linux" ~/linux-lab/notes/search.txt
grep -i "linux" ~/linux-lab/notes/search.txt
grep -in "linux" ~/linux-lab/notes/search.txt
```

## Challenge 4

```bash
cat > ~/linux-lab/scripts/greeting.sh <<'EOF'
#!/bin/bash
echo "Hello, student!"
whoami
pwd
date
EOF

chmod u+x ~/linux-lab/scripts/greeting.sh
~/linux-lab/scripts/greeting.sh
```

## Challenge 5

```bash
whoami
pwd
uname -r
free -h
df -h
uptime
```

## Challenge 6

```bash
ls /dev | wc -l
grep "Mem" /proc/meminfo
ps aux | head -n 6
```

---

# Quick command checklist

- [ ] `pwd`, `ls`, `cd`
- [ ] `mkdir`, `touch`, `cat`
- [ ] `cp`, `mv`, `rm`
- [ ] `echo`, `>`, `>>`
- [ ] `find`, `grep`, `wc`
- [ ] `chmod`, run a script
- [ ] `ps`, `top`, `free`, `df`, `uptime`
- [ ] `|` pipes and output redirection
- [ ] `ping`, `ip addr`, `ip route`

## Good practice habits

1. Practice inside `~/linux-practice` or another folder you created.
2. Use `ls` before deleting or moving files.
3. Read command help with `command --help` or `man command`.
4. Be cautious with `sudo`, `rm -r`, and commands copied from unknown sources.
5. Make a guess about what a command will do, run it, then verify the result.