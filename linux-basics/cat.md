# cat — Read and Concatenate Files

## What it does
The `cat` (concatenate) command reads file contents and displays them on the terminal. It can also write and append to files.

## Syntax
`cat [OPTION]... [FILE]...`

## Key Flags

| Flag | What it does |
|---|---|
| `-n` | show line numbers |
| `-e` | show `$` at end of each line (newline marker) |
| `-t` | show `^I` for tab characters |
| `-A` | show all special characters (`-et` equivalent) |
| `-b` | number non-empty lines |

## Examples

### Example 1: Read a file
`cat /etc/hostname`
Output:
bunnys-MacBook-Air.local

### Example 2: Line numbers
`cat -n /etc/hosts`
Output:
     1  ##
     2  # Host Database
     3  #
     4  localhost
     5  255.255.255.255

### Example 3: Show special chars
`echo -e "test\tline\n" > t.txt`
`cat -et t.txt`
Output:
test^Iline$  $ 
- `^I` = TAB character
- `$` = end of line (newline)

### Example 4: Write to a file (heredoc)
`cat > demo.txt << 'EOF'`
`apple`
`banana`
`cherry`
`EOF`

After running, `cat demo.txt` shows:
apple
banana
cherry

### Example 5: Append to a file
`echo "date" >> demo.txt`
`cat demo.txt`
Output:
apple
banana
cherry
date

## Red Team Use Cases

- `cat /etc/passwd` — Read user account file
- `cat /etc/shadow` — Read password hashes (needs root)
- `cat ~/.ssh/id_rsa` — Read SSH private keys
- `cat /etc/ssh/sshd_config` — Read SSH server config
- `cat /etc/sudoers` — Check sudo permissions

## Practice
- `cat /etc/hostname`
- `cat -n /etc/passwd | head -20`
- `echo -e "a\tb\tc" > tab.txt`
- `cat -t tab.txt`
- `cat -et tab.txt`
- `cat > mytest.txt << 'EOF'` then write 3 lines, then `EOF`

## Key Learnings
- `cat file` = read
- `cat -n file` = read with line numbers
- `cat > file` = write (overwrite)
- `cat >> file` = append
- `cat -et` = reveal hidden characters (TAB as `^I`, newline as `$`)
- `<< 'EOF'` = heredoc for multi-line writing