# ls — List Directory Contents

## What it does
The `ls` command lists files and subdirectories inside a directory. By default, it shows the current directory.

## Syntax
`ls [OPTION]... [FILE]...`

## Key Flags

| Flag | Long form | What it does |
|---|---|---|
| `-l` | — | long format (permissions, owner, size, date) |
| `-a` | `--all` | show all files including hidden (`.file`) |
| `-h` | `--human-readable` | file sizes in K, M, G |
| `-t` | — | sort by modification time (newest first) |
| `-S` | — | sort by file size (largest first) |
| `-r` | `--reverse` | reverse order |
| `-R` | `--recursive` | list subdirectories recursively |

## Examples

### Example 1: Basic listing
`ls`
Output:
Desktop    Documents  Downloads  Music      Pictures

### Example 2: Long format with all files
`ls -la /etc`
Output:
total 1234
drwxr-xr-x  88 root root  4.0K Nov  7 12:34 .
drwxr-xr-x  23 root root  4.0K Oct 20 09:00 ..
-rw-r--r--   1 root root  3.0K Nov  1 10:00 hosts
-rw-r--r--   1 root root   220 Feb 13  2026 hostname

### Example 3: Human-readable sizes
`ls -lh ~`
Output:
total 8.0K
drwx------  4 bunny  staff  128B Oct  4 22:23 Desktop
drwxr-xr-x 69 bunny  staff  2.2K Oct  6 19:35 Library

### Example 4: Sort by size
`ls -lhS /usr/bin | head -5`
Output:
total 250M
-rwxr-xr-x  1 root root  25M Sep 12 09:00 python3.11
-rwxr-xr-x  1 root root  18M Sep 12 09:00 python3

## Red Team Use Cases

- `ls -la ~/.ssh/` — Find SSH keys (hidden folder)
- `ls -la /etc/` — List sensitive config files
- `ls -la /tmp/` — Check /tmp for potential payloads
- `ls -lt /var/log/` — Find recently modified log files

## Practice
- `ls -la /etc/`
- `ls -lh ~`
- `ls -lt /var/log`
- `ls -lhS /usr/bin | head -10`
- `ls -la ~/.ssh/`

## Key Learnings
- `-l` = long format
- `-a` = all (hidden files included)
- `-h` = human-readable
- Combine flags: `-la`, `-lh`, `-lS`
- Hidden files start with `.` (dot)