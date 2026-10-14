# Instructor Guide — Solutions + Teaching Tips
PRIVATE — do not share with students.

## Solutions (examples; equivalents are fine)

### Challenge 1
```bash
cd ~
mkdir -p linux-lab/{notes,scripts,backup}
touch linux-lab/notes/day1.txt
echo "Today I learned Linux commands." > linux-lab/notes/day1.txt
echo "I will keep practicing." >> linux-lab/notes/day1.txt
cat linux-lab/notes/day1.txt
ls -R linux-lab
```

### Challenge 2
```bash
cp ~/linux-lab/notes/day1.txt ~/linux-lab/backup/
mv ~/linux-lab/backup/day1.txt ~/linux-lab/backup/day1-copy.txt
find ~/linux-lab -name "*.txt"
wc -l ~/linux-lab/notes/day1.txt
```

### Challenge 3
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

### Challenge 4
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

### Challenge 5
```bash
whoami
pwd
uname -r
free -h
df -h
uptime
```

### Challenge 6
```bash
ls /dev | wc -l
grep "Mem" /proc/meminfo
ps aux | head -n 6
```

---

## Teaching tips for 90-min flow

- **Ch 1:** Most common error is `mkdir linux-lab/notes` without `-p` after `linux-lab` doesn't exist. Teach `mkdir -p`.
- **Ch 2:** Students forget `mv` source path is `backup/day1.txt`, not `notes/day1.txt`. Have them `ls backup/` first.
- **Ch 3:** Stress `-i` vs `-n` — do `grep` then `grep -i` then `grep -in` live so they see difference.
- **Ch 4:** Two failures: missing `#!/bin/bash` first line, and `Permission denied` (forgot `chmod u+x`). Show `ls -l` before/after chmod.
- **Ch 5/6:** Keep fast. `top` — remind `q` to quit, otherwise projector freezes.

## Quick checks while walking around

- `ls -R ~/linux-lab` should show `notes/day1.txt`, `backup/day1-copy.txt`, `scripts/greeting.sh`.
- `ls -l` on scripts should show `x` flag.
- If `find` returns nothing, they are in wrong directory — `pwd` first.

## What to skip if running late

Skip Networking live demo (Sec 10), assign Ch 5–6 as homework. Never skip Permissions demo — it's the aha moment.
