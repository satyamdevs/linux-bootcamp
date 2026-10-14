# Student Handout — Hands-on Challenges
Try these yourself before looking at any solutions. Work in `~` unless told otherwise.

> Safety: stay in `~/linux-lab` or `~/linux-practice`. Use `ls` before `rm` / `mv`. `>` overwrites files.

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

# Quick command checklist

Tick when you can do it without looking:

- [ ] `pwd`, `ls`, `cd`
- [ ] `mkdir`, `touch`, `cat`
- [ ] `cp`, `mv`, `rm`
- [ ] `echo`, `>`, `>>`
- [ ] `find`, `grep`, `wc`
- [ ] `chmod`, run a script
- [ ] `ps`, `top`, `free`, `df`, `uptime`
- [ ] `|` pipes and output redirection
- [ ] `ping`, `ip addr`, `ip route`
