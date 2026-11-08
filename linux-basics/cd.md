
# cd — Change Directory

## What it does
The `cd` command changes the current working directory. It is built into the shell (no separate binary).

## Syntax
`cd [directory]`

## Special Symbols

| Symbol | Meaning |
|---|---|
| `/` | root directory |
| `~` | home directory |
| `.` | current directory |
| `..` | parent directory |
| `-` | previous directory |

## Examples

### Example 1: Absolute path
`cd /etc`
Output (verify with pwd):
```
/etc
```

### Example 2: Relative path
`cd Documents` (from home directory)
Output (verify with pwd):
```
/Users/bunny/Documents
```

### Example 3: Go up one level
`cd ..`
Output:
```
(returns to parent directory)
```

### Example 4: Home directory
`cd ~` or just `cd`
Output:
```
/Users/bunny
```

### Example 5: Previous directory (toggle)
`cd -`
Output:
```
(returns to the directory you were in before)
```

## Red Team Use Cases

- `cd ~/.ssh/` — Navigate to SSH folder
- `cd /var/log/` — Navigate to log folder
- `cd /home/targetuser/` — Navigate to target's home (post-compromise)
- `cd /etc/` — Move to system config directory
- `cd /tmp/` — Common staging area for payloads

## Practice
- `cd /tmp && pwd`
- `cd ~ && pwd`
- `cd /etc && cd - && pwd`
- `cd .. && pwd`
- `cd . && pwd` (no change)

## Key Learnings
- `cd` alone = go to home
- `cd -` = toggle between two directories
- `cd ..` = go up one level
- Absolute path starts with `/`
- Relative path does NOT start with `/`
- Use `pwd` to verify where you are
