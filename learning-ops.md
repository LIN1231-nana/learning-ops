# Ops Learning Journal - [2026-07-08]

## Today's Focus
> nginx

---

## New Commands Learned
keepalived 

### 1. Command: `keepalived`
- **Usage**: Change file permissions.
- **Example**: `chmod 755 script.sh`
- **My Note**: `7` means `rwx` for the owner, `5` means `r-x` for the group.

### 2. Command: `useradd`
- **Usage**: Create a new user.
- **Option**: `-m` creates the home directory.
- **Example**: `sudo useradd -m tom`

---

## Errors & Solutions
my sql

- **Error Message**: 
  `Permission denied` when I run `./hello.sh`.
- **Why**: 
  The script file does not have execute permission (`x`).
- **How I fixed**: 
  I ran `chmod +x hello.sh` to add execute permission.

---

## One Key Takeaway
> 今天印象最深的一点：权限的数字法（755）其实就是把 `rwx` 转成二进制相加。