# file — Determine File Type

## What it does
The `file` command tests each file and reports its type (text, binary, image, executable, etc.). It does NOT rely on file extension.

## Syntax
`file [OPTION]... FILE...`

## Key Flags

| Flag | What it does |
|---|---|
| `-b` | brief mode (don't show filename) |
| `-i` | show MIME type |
| `-z` | check inside compressed files |
| `-L` | follow symlinks |

## Examples

### Example 1: Identify common file types
`file /etc/passwd`
Output:
/etc/passwd: ASCII text

`file /bin/ls`
Output:
/bin/ls: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV)

`file image.png`
Output:
image.png: PNG image data, 1920 x 1080, 8-bit/color RGBA, non-interlaced

### Example 2: Brief mode
`file -b /etc/passwd`
Output:
ASCII text

### Example 3: MIME type
`file -i /etc/passwd`
Output:
/etc/passwd: text/plain; charset=us-ascii

### Example 4: Check multiple files
`file /etc/passwd /etc/hosts /bin/ls`
Output:
/etc/passwd: ASCII text
/etc/hosts: ASCII text
/bin/ls:    ELF 64-bit LSB shared object, x86-64

### Example 5: Check inside compressed file
`file archive.tar.gz`
Output:
archive.tar.gz: gzip compressed data

`file -z archive.tar.gz`
Output:
archive.tar.gz: POSIX tar archive

## Red Team Use Cases

- `file /tmp/suspicious_file` — Identify suspicious binaries
- `file /usr/local/bin/script.sh` — Verify shell scripts
- `file -z backup.tar.gz` — Check uploaded files for hidden content
- `file /usr/bin/passwd` — Identify a binary before analyzing
- `file *.exe` — Check Windows executables in Linux

## Practice
- `file /etc/passwd`
- `file /bin/ls`
- `file /usr/share/man/man1/ls.1.gz`
- `file -b /etc/hosts`
- `file -i /etc/passwd`
- `file ~/Pictures/*.jpg 2>/dev/null | head -5`

## Key Learnings
- `file` doesn't trust file extension
- It examines file's "magic bytes" (first few bytes)
- `-z` to check inside compressed files
- `-i` for MIME type (useful for web)
- Common types: ASCII text, ELF binary, gzip data, PNG image