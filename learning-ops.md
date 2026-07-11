# Ops Learning Journal - [填写今天的日期，如 2026-06-25]

## 📌 Today's Focus（今日主题）
> 用一句话概括今天学了什么（例如：Linux file permissions and user management）

---

## 🛠️ New Commands Learned（今日新命令）
*（只记录最有用、最容易忘的3个命令）*

### 1. Command: `chmod`
- **Usage**: Change file permissions.
- **Example**: `chmod 755 script.sh`
- **My Note**: `7` means `rwx` for the owner, `5` means `r-x` for the group.

### 2. Command: `useradd`
- **Usage**: Create a new user.
- **Option**: `-m` creates the home directory.
- **Example**: `sudo useradd -m tom`

---

## 🚨 Errors & Solutions（今日踩坑记录）—— **这是面试官最爱看的！**
*（哪怕今天只碰到一个报错，也要写下来）*

- **Error Message（报错内容）**: 
  `Permission denied` when I run `./hello.sh`.
- **Why（为什么报错）**: 
  The script file does not have execute permission (`x`).
- **How I fixed（怎么解决的）**: 
  I ran `chmod +x hello.sh` to add execute permission.

---

## 💡 One Key Takeaway（今日核心领悟）
> 今天印象最深的一点：权限的数字法（755）其实就是把 `rwx` 转成二进制相加。