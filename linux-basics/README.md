# Linux Basics — Core Command Reference

Reference for fundamental Linux commands used in OverTheWire Bandit CTF (Level 0 → Level 7).

## Commands

| Command | Purpose | File |
|---|---|---|
| `ls` | List directory contents | [ls.md](ls.md) |
| `cd` | Change directory | [cd.md](cd.md) |
| `cat` | Read/concatenate files | [cat.md](cat.md) |
| `file` | Determine file type | [file.md](file.md) |
| `du` | Disk usage | [du.md](du.md) |
| `find` | Search files by metadata | [find.md](find.md) |

## Cheat Sheet

```bash
# Listing
ls -la /etc            # all files (hidden included)
ls -lh ~               # human-readable sizes
ls -lt /var/log        # sort by time

# Reading
cat -n file            # with line numbers
cat -et file           # reveal special chars (^I, $)
cat > file << 'EOF'    # heredoc write

# Type Detection
file /etc/passwd       # ASCII text
file -b filename       # brief mode

# Disk Usage
du -sh /etc            # total size
du -ah /path           # all files

# Search
find / -name "*.conf" 2>/dev/null
find / -user root -type f 2>/dev/null
find / -size +1M 2>/dev/null
find / -perm -4000 2>/dev/null   # SUID binaries
Red Team Patterns
bash

find / -perm -4000 -type f 2>/dev/null    # SUID (priv esc)
find / -name "id_rsa" 2>/dev/null         # SSH keys
find / -name "*.bak" 2>/dev/null          # Backup files
cat /etc/passwd                           # User accounts
cat /etc/shadow                           # Password hashes (root)
