# du — Disk Usage

## What it does
The `du` (disk usage) command shows how much disk space a file or directory is using.

## Syntax
`du [OPTION]... [FILE]...`

## Key Flags

| Flag | Long form | What it does |
|---|---|---|
| `-h` | `--human-readable` | sizes in K, M, G |
| `-s` | `--summarize` | only show total (not per file) |
| `-a` | `--all` | show all files (not just directories) |
| `-c` | `--total` | show grand total at end |
| `-d N` | `--max-depth=N` | limit to N levels deep |

## Examples

### Example 1: Total size of a directory
`du -sh /etc`
Output:
3.2M    /etc

### Example 2: Sizes of all top-level directories
`du -sh /*`
Output:
8.0K    /bin
4.0K    /dev
3.2M    /etc
12M     /lib

### Example 3: Per-file sizes inside directory
`du -h /var/log | head -10`
Output:
4.0K    /var/log/cups
8.0K    /var/log/apache2
3.4M    /var/log/install.log

### Example 4: All files (not just dirs)
`du -ah /etc | head -10`
Output:
4.0K    /etc/hosts
4.0K    /etc/hostname
3.0K    /etc/passwd

### Example 5: Limit depth
`du -h --max-depth=1 /`
Output:
4.0K    /bin
3.2M    /etc
12M     /lib

## Red Team Use Cases

- `du -ah / | sort -rh | head -20` — Find unusually large files (potential payloads/dumps)
- `du -sh /tmp` — Check size of /tmp (potential exfil staging)
- `du -sh /var/log/auth.log*` — Check stolen data dumps
- `du -ah /home/* | sort -rh | head -10` — Find big files in user homes (potential exfil)

## Practice
- `du -sh /etc`
- `du -sh /var/log`
- `du -sh ~/*`
- `du -h /etc | head -10`
- `du -ah /tmp 2>/dev/null | head -10`
- `du -sh /* 2>/dev/null`

## Key Learnings
- `-s` = summary (just total)
- `-h` = human-readable
- `-a` = all files
- Combine: `-sh` (summary + human), `-ah` (all + human)
- `-d N` or `--max-depth=N` to limit depth