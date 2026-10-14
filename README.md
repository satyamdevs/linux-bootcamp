# Linux Bootcamp — 90-Minute Workshop Plan

This folder is organized for teaching. Start here.

## Files in this folder

| File | Who is it for | What is it |
|---|---|---|
| `README.md` (this file) | You (instructor) | 90-min run-plan + setup |
| `cheatsheet.md` | Everyone | Clean command reference, Sections 1–11 |
| `student-handout.md` | Students | Challenges 1–6 + checklist, **no solutions** |
| `instructor-guide.md` | You only | Solutions + teaching tips + common mistakes |
| `demos/` | Live demo | Ready-to-run `hello.sh`, `greeting.sh` |
| `docs.md` | Archive | Original file (had duplicated content, kept for reference) |

> Do NOT project `instructor-guide.md` — share only `cheatsheet.md` + `student-handout.md`.

## Setup before class (5 min)

1. Students need: Ubuntu / Linux Mint (or VM), terminal access, home directory write permission.
2. Test these on projector machine:
   ```bash
   whoami; pwd; ls /tmp; free -h; df -h; ps aux | head
   ```
3. No `sudo apt install` during 90-min class — mention it, don't run it.

## 90-Minute Run Plan

### 0:00–0:10 — Welcome + Safety (10 min)
- Show: `whoami`, `pwd`, `date`, `uname -a`, `clear`, `history`
- Emphasize Safety from `cheatsheet.md`:
  - Stay in `~` / `~/linux-lab`
  - `ls` before `rm` / `mv`
  - No `sudo`, no blind copy-paste, `>` overwrites
- Goal for today: navigate, make files, search, run a script, read system info, use pipes.

### 0:10–0:30 — Navigate + Files (20 min, live-coding)
**Teach:** Section 2 + 3 of `cheatsheet.md`
```bash
pwd; ls; ls -la; cd ~; cd /; ls; cd -
mkdir -p ~/linux-lab/{notes,scripts,backup}
echo "My first Linux practice" > ~/linux-lab/notes/day1.txt
cat ~/linux-lab/notes/day1.txt
ls -R ~/linux-lab
```
Student does it with you. Check: everyone has `docs/notes.txt`-style structure.

### 0:30–0:45 — Write, Search, Paths (15 min)
**Teach:** Sections 4, 5, 6
```bash
echo "Line one" > todo.txt; echo "Line two" >> todo.txt; cat todo.txt
grep -in "linux" docs/topic.txt
find . -name "*.txt"
ls /tmp; ls /dev | head; cat /proc/meminfo | head
```
Key point: `>` vs `>>`, `grep -i -n -r`, `/`, `~`, `.`, `..`, `/proc` + `/dev` are special.

### 0:45–1:00 — Permissions + First Script (15 min, highlight moment)
**Teach:** Section 7
```bash
cat demos/hello.sh
chmod u+x demos/hello.sh
./demos/hello.sh
ls -l demos/hello.sh
```
Explain `rwx`, `chmod 644` vs `755`. Everyone runs `hello.sh`.

### 1:00–1:15 — System + Pipes + Network (15 min, fast)
**Teach:** Sections 8, 9, 10 — demo only, no deep dive
```bash
free -h; df -h; uptime; ps aux | head
ls -l > file-list.txt; cat file-list.txt
ps aux | head; cat /proc/meminfo | grep MemAvailable; ls /dev | wc -l
ping -c 4 example.com; ip addr; ip route
```

### 1:15–1:30 — Challenges in class (15 min)
- Give `student-handout.md`. Do Challenges 1–4 together / in pairs.
- Challenges 5–6 as take-home.
- End with Quick Checklist: tick off `pwd,ls,cd,mkdir,cat,cp,mv,grep,chmod,|,>,ps`.

## Commands to keep on screen

```bash
pwd | ls -l | cd | mkdir -p | touch | cat | echo > >> | cp | mv | find | grep -inr | chmod u+x | ./script.sh | ps aux | head | free -h | df -h
```

## After class
1. Share `cheatsheet.md` + `student-handout.md` for practice.
2. Keep `instructor-guide.md` private.
3. Optional cleanup for students: `rm -rf ~/linux-practice ~/linux-lab` — only after verifying with `ls`.
