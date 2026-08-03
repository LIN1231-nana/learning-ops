# Ops Learning Journal - [2026-07-12]

## Today's Focus
> The basic operation of VMware, such as the installation of VMware, the creation of virtual machines.

---

## Problems & Solutions

- **Problem**: 
  Can't find the installation package of CentOS 7 in the official website.
- **Why**: 
  It's known that official has stopped maintenance
- **How I fixed**: 
  Download the installation package from https://mirrors.huaweicloud.com/home
  New Learning Plan: Rocky Linux / Ubuntu Server

---

## One Key Takeaway
> I should keep up-to-date with industry trends and the latest news.

---




# Ops Learning Journal - [2026-07-13]

## Today's Focus
> Linux directory structure and related tools, like Xshell, Xftp and FinalShell

---




# Ops Learning Journal - [2026-07-14]

## Today's Focus
> Common Linux commands, including help, shutdown, systemctl and some file directory commands.

---

## New Commands Learned
man, help, shutdown, systemctl, pwd, ls, cd, mkdir, touch, cp, rm, mv, cat, more, less, head, tail, echo, >, >>, ln, history.

### 1. Command: `pwd`
- **Usage**: Print working directory.
- **Example**: `pwd` --> `/root/test`
- **My Note**: show the absolute path.

### 2. Command: `ls`
- **Usage**: list, print all files and folds in current directory.
- **Option**: `-a` display the hidden files.
- **Option**: `-l` display detailed information.
- **My Note**: `ls -l` = `ll`

### 3. Command: `cp`
- **Usage**: copy, copy the source file to the target file.
- **Option**: `-r` recursive copy of the entire directory.
- **Example**: `cp -r source dest`
- **My Note**: `\cp` force overwrite the same name files.

---

## One Key Takeaway
> mv can rename files, like `mv OldNameFile NewNameFile`, and .bak usually refers to discarded files.

---




# Ops Learning Journal - [2026-07-15]

## Today's Focus
> vim editor

---

## New Commands Learned

### 1. Command: `:wq`
- **Usage**: :w save and :q exit.
- **Option**: `:wq!` sava and exit forcelly.

### 2. Command: `:set nu`
- **Usage**: display line number.
- **My Note**: `:set nonu` disable line number.

### 3. Command: `vim /etc/hostname`
- **Usage**: change the hostname.
- **My Note**: `hostname` check the hostname.

---

## One Key Takeaway
> In case of abnormal exit from vim editor (like: forcibly closing without saving), `ls -a` find `.swp` in file directory and `rm` delete it.

---




# Ops Learning Journal - [2026-07-16]

## Today's Focus
> Some management commands and file permission-related commands.

---

## New Commands Learned
date, useradd, id, su, sudo, groupadd, usermod, chmod, chown.

### 1. Command: `usermod`
- **Usage**: Move the user's group.
- **Example**: `usermod -g user group`
- **My Note**: `cat /etc/group` show which group have been created.

### 2. Command: `chmod`
- **Usage**: Change file permissions.
- **Example**: `chmod u=rwx filename`, `chmod 753 filename`.
- **My Note**: rwx=421, ugo

### 3. Command: `chown`
- **Usage**: Change the owner of the file or directory.
- **Option**: `-R` Recursively change the owner and group of files or directories.
- **Example**: `chown -R finalusr:finalgroup filename`
- **My Note**: `chgrp finaluser filename` change the group of files or directories.

---

## One Key Takeaway
> `vim /etc/sudoers`
\## Allow root to run any commands anywhere
root ALL=(ALL) ALL
username ALL=(ALL) ALL #use `sudo` need passwd
username ALL=(ALL) NOPASSWD=ALL #use `sudo` don't need passwd

---




# Ops Learning Journal - [2026-07-18]

## Today's Focus
> The first week test: Reinstall Linux independently, and use `ls -l /` to view the structure of /.

---

## Problems & Solutions
What is KDUMP?

- **Answer**: 
  When the Linux kernel crashes due to a serious error, Kdump immediately saves the information (mainly the data) at the moment, so that technicians can analyze the cause later.

---



# Ops Learning Journal - [2026-07-21]

## Today's Focus
> Search and filter commands

---

## New Commands Learned
bash, find, grep.

### 1. Command: `find`
- **Usage**: Search for a file through name, user and size.
- **Example**: `find directory -name "filename"`

### 2. Command: `|`
- **Usage**: Outputs the result of the previous command to the next command.
- **My Note**: Usually used with grep. 

---

## One Key Takeaway
> Users need to have execution permissions to read the files within the directory.

---




# Ops Learning Journal - [2027-07-22]

## Today's Focus
> Some compression commands, scheduled task commands, etc.

---

## New Commands Learned
gzip, zip, tar, df, fdisk, mount, ps, kill, crontab

### 1. Command: `tar`
- **Usage**: Package the directory.(.tar.gz)
- **Option**: `-z` compress and package.
- **Option**: `-c` creates a file(.tar).
- **Option**: `-v` show detailed information.
- **Option**: `-f` specifies the compressed file.
- **Option**: `-x` unpacks the file(.tar).
- **My Note**: usually use `-zcvf` compress and `-zxvf` decompress.

### 2. Command: `crontab`
- **Usage**: Set up a scheduled task.
- **Option**: `-e` edit scheduled tasks.
- **Option**: `-l` query tasks.
- **Option**: `-f` deletes all tasks of current user.

---

## Errors & Solutions

- **Error Message**: 
  `crontab: usage error: unrecognized option` when I run `crontab -f`.
- **Why**: 
  This version of crontab does not support the `-f`.
- **How I fixed**: 
  According to the prompt provided by the error message, replace `-f` with `-r`.

---




# Ops Learning Journal - [2026-07-23]

## Today's Focus
> Learn RPM and YUM, install JDK and MySQL in Linux.

---

## New Commands Learned
rpm, yum.

### 1. Command: `rpm`
- **Usage**: RPM query command.
- **Option**: `-qa` query all the installed software packages.
- **Option**: `-ql servername` check the installation location.
- **Option**: `-e SoftwarePackage` uninstall the software.
- **Option**: `-ivh RPMpackage` install the software.
- **My Note**: `rpm -e --nodeps SoftwarePackage` means uninstall the software without checking dependencies.

### 2. Command: `yum`
- **Option**: `-y` answer "yes" to all questions.
- **Example**: `yum -y install SoftwarePackage`

---

## Errors & Solutions

- **Error Message**: 
  `Could not retrieve mirrorlist http://mirrorlist.centos.org/?release=7&arch=x86_64&repo=os&infra=stock error was 14: curl#6 - "Could not resolve host: mirrorlist.centos.org; "` when I run `yum list`.
- **Why**: 
  The official image source of CentOS 7 has stopped maintenance, the mirrorlist.centos.org cannot be resolved.
- **How I fixed**: 
  1.Change to a domestic available mirror source
    `vi /etc/yum.repos.d/CentOS-Base.repo`
    Replace file content
    [base]
    name=CentOS-$releasever - Base - mirrors.aliyun.com
    baseurl=http://mirrors.aliyun.com/centos/$releasever/os/$basearch/
    gpgcheck=1
    gpgkey=http://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-7

    [updates]
    name=CentOS-$releasever - Updates - mirrors.aliyun.com
    baseurl=http://mirrors.aliyun.com/centos/$releasever/updates/$basearch/
    gpgcheck=1
    gpgkey=http://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-7

    [extras]
    name=CentOS-$releasever - Extras - mirrors.aliyun.com
    baseurl=http://mirrors.aliyun.com/centos/$releasever/extras/$basearch/
    gpgcheck=1
    gpgkey=http://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-7
      I ran `chmod +x hello.sh` to add execute permission.
    Save and then execute
    `yum clean all`
    `yum makecache`
      `Determining fastest mirrors http://mirrors.aliyun.com/centos/7/os/x86_64/repodata/repomd.xml: [Errno 14] curl#6 - "Could not resolve host: mirrors.aliyun.com;` when I run `yum makecache`.
      1.Check network connectivity
        `ping 8.8.8.8`
        The network is connected. 
      2.Fix the DNS settings.
        Check current DNS settings
        `cat /etc/resolv.conf`
        Temporary repair
        `echo "nameserver 8.8.8.8" > /etc/resolv.conf`
        `echo "nameserver 114.114.114.114" >> /etc/resolv.conf`
        Verify
        `ping mirrors.aliyun.com`
        DNS has been restored.
      3.Rebuild the yum cache
        `yum clean all`
        `yum makecache`

---

- **Error Message**: 
  `-bash: /opt/java/jdk-26.0.2/bin/java: 无法执行二进制文件` when I run `java -version`.
- **Why**: 
  The JDK version does not match the system architecture.
- **How I fixed**: 
  1.Clean up environment variables
  `vim /etc/profile.d/my_env.sh`
  2.Delete the directory and reinstall.
  `rm -rf /opt/java/jdk-26.0.2`

---

- **Error Message**: 
  `ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)` when I run `mysql -uroot -p"tiSs#Mg-D5jS"`.
- **Why**: 
  The MySQL service is not running, or the location of socket file is incorrect.
- **How I fixed**: 
  1.Check the status of MySQL
  `systemctl status mysqld`
  2.Show inactive(dead).
  `systemctl start mysqld`

---




# Ops Learning Journal - [2026-07-24]

## Today's Focus
> Introduction to Shell Scripts, Variables and Special Variables.

---

## New Commands Learned
sh, bash, $, []

### 1. Command: `sh`
- **Usage**: Execute file(.sh).
- **Example**: `sh file.sh`
- **My Note**: `sh` = `bash`

---

## One Key Takeaway
> $n, $0 represents the script name, and ${10} for values above 10.

---




# Ops Learning Journal - [2026-07-25]

## Today's Focus
> Create three different users and create a file named "test.txt". Set its permissions to 755, 644, and 600 respectively, and `ls -l`verify; then transfer the ownership of the file.

---

## Problems & Solutions
How to view the members of a group?

- **Answer**: 
  Can't view all members at once, but can query which group the user belongs to.
  `groups username`

---




# Ops Learning Journal - [2026-07-27]

## Today's Focus
> `if` condition judgment and `while` loop

---

## New Commands Learned
if, case, while

---

## Errors & Solutions


- **Error Message**: `-bash: ./while.sh: /bon/bash: 坏的解释器: 没有那个文件或目录` when I run `./while.sh`.
- **Why**: 
  The first line is incorrect.
- **How I fixed**: 
  Correct `#!/bon/bash` to `#!/bin/bash`

---




# Ops Learning Journal - [2026-07-28]

## Today's Focus
> Regular expressions and the system functions, custom functions and some tools of the Shell.

---

## New Commands Learned
basename, dirname, cut, awk, sort, wc.

### 1. Command: `awk`
- **Usage**: Read the file line by line and then analyze and process it.
- **Example**: `awk -F ":" '/mysql/{print $1}' passwd`
- **My Note**: `BEGIN{print "xxx"}` Execute before reading all the data, `END{print "xxx"}` Execute after reading all the data.

### 2. Command: `wc`
- **Usage**: Word count.
- **Option**: `-l` count the number of lines in the file.
- **Option**: `-w` count the number of words in the file.
- **Option**: `-m` count the number of characters in the file.
- **Option**: `-c` count the number of bytes in the file.
- **Example**: `wc -l passwd`

---

## Errors & Solutions

- **Error Message**: 
  `./func.sh:行14: func: 未找到命令` when I run `./func.sh`.
- **Why**: 
  When using custom functions in the shell, you should declare first and then call. The function name is not `func`.
- **How I fixed**: 
  Correct `func $X $Y` to `SUM $X $Y`

---

## One Key Takeaway
> Regular expressions are used to search for and replace text that matches a certain pattern.

---




# Ops Learning Journal - [2026-07-29]

## Today's Focus
> the basic knowledge of AliyunECS, the installation and use of the Ubuntu system.

---

## New Learned

### 1. How to initiate a remote connection
- `sudo apt install openssh-server`
- `sudo service ssh start`
- `sudo vim /etc/ssh/sshd_config`
    Replace `#PermitRootLogin prohibit-passwd` with `PermitRootLogin yes`

---

## One Key Takeaway
> Some basic functions of Ubuntu require installation.

---





# Ops Learning Journal - [2026-07-31]

## Today's Focus
> Create a new user named `devops` and grant it sudo privileges; use `Vim` to edit `/etc/hosts` and add a record; start the background process by executing `sleep 1000 &`, then use `ps` to find the PID and use `kill` to terminate it.

---

## Problems & Solutions

### 1. How to start the background process: sleep 1000 &
- **Answer**: 
  `sleep 1000 &`

### 2. Can't find `sleep 1000 &`
- **Error Message**: `ps -ef | grep "sleep 1000 &" | grep -v grep`.
- **Why**: Using `&` as part of `grep`, but `&` has a special meaning in the shell (indicating background execution), so it was interpreted by the shell.
- **How I fixed**: `ps -ef | grep sleep | grep -v grep`

---




