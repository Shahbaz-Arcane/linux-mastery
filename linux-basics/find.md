# find — Search Files by Metadata

## What it does
The `find` command searches the file system for files matching criteria like name, type, size, owner, or modification time.

## Syntax
`find [PATH] [EXPRESSION]`

## Key Flags / Expressions

| Expression | What it does |
|---|---|
| `-name "pattern"` | match filename (case-sensitive) |
| `-iname "pattern"` | match filename (case-insensitive) |
| `-type f` | only regular files |
| `-type d` | only directories |
| `-size +N` | larger than N (c=bytes, k, M, G) |
| `-size -N` | smaller than N |
| `-mmin -N` | modified within last N minutes |
| `-user NAME` | owned by user NAME |
| `-group NAME` | owned by group NAME |
| `-perm -4000` | SUID bit set |
| `-exec CMD {} \;` | run CMD on each match |

## Examples

### Example 1: Find by name
`find /etc -name "*.conf" 2>/dev/null | head -5`
Output:
/etc/ssh/ssh_config
/etc/resolv.conf
/etc/man.conf

### Example 2: Find by type (only directories)
`find ~ -type d -name "Library"`
Output:
/Users/bunny/Library

### Example 3: Find by size (larger than 1MB)
`find /usr -size +1M 2>/dev/null | head -5`
Output:
/usr/bin/python3.11
/usr/bin/ffmpeg

### Example 4: Find recently modified files
`find /tmp -mmin -60 2>/dev/null`
Output:
/tmp/recent_file.txt
/tmp/.cache/cache.dat

### Example 5: Combine filters
`find /etc -name "*.conf" -type f -size +1k 2>/dev/null | head -5`
Output:
/etc/ssh/sshd_config
/etc/sudoers

### Example 6: Execute command on results
`find . -name "*.log" -exec wc -l {} \;`
Output:
34 ./app.log
128 ./error.log

## Red Team Use Cases

- `find / -perm -4000 -type f 2>/dev/null` — Find SUID binaries (privilege escalation targets)
- `find / -name "*.bak" 2>/dev/null` — Find backup files (may contain passwords)
- `find / -name "id_rsa" 2>/dev/null` — Find SSH private keys
- `find / -mmin -60 -type f 2>/dev/null` — Find recently modified files (intrusion detection)
- `find / -writable -type d 2>/dev/null` — Find writable directories (for payloads)
- `find / -name "*.conf" -exec grep -l "password" {} \; 2>/dev/null` — Find files with passwords

## Practice
- `find ~ -name "*.txt" 2>/dev/null | head -10`
- `find /etc -name "*.conf" 2>/dev/null | head -10`
- `find ~ -type d -name "Library"`
- `find /usr -size +1M 2>/dev/null | head -5`
- `find /tmp -mmin -60 2>/dev/null`
- `find ~ -name "*.py" -type f 2>/dev/null | head -10`

## Key Learnings
- `find` searches by **file metadata**, not content
- For content search, use `grep`
- `2>/dev/null` to suppress "Permission denied" errors
- `-exec CMD {} \;` to run commands on each match
- Common Red Team pattern: `find / -NAME/PERM/SIZE 2>/dev/null`
- `*` = wildcard (matches anything)