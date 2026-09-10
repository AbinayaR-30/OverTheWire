# Bandit Level 3 → Level 4 (Linux Terminal)

## Level Goal

The password for Bandit Level 4 is stored in a hidden file inside the `inhere` directory.

The challenge is to learn how to view and access hidden files in Linux.

## Concept Learned

In Linux, files and directories whose names begin with a dot (`.`) are called hidden files. They are not displayed with a normal `ls` command.

To view hidden files, use the `-a` option with `ls`.

### Commands Used

|
Linux Command

|

Purpose

|
| --- | --- |
|

`pwd`

|

Shows the current working directory.

|
|

`ls`

|

Lists visible files and directories.

|
|

`cd`

|

Changes into the `inhere` directory.

|
|

`ls -a`

|

Lists all files, including hidden files.

|
|

`cat`

|

Displays the contents of the hidden file.

|
|

`exit`

|

Closes the current SSH session.

|
|

`ssh`

|

Logs into the next Bandit level.

|

## Walkthrough (Linux Terminal)

### Step 1 – Verify Your Current Directory

After logging into bandit3, check your current location.

Bash

```
bandit3@bandit:~$ pwd
```

Output

```
/home/bandit3
```

This confirms that you are inside the bandit3 home directory.

### Step 2 – List Files

Display the contents of the current directory.

Bash

```
bandit3@bandit:~$ ls
```

Output

```
inhere
```

A directory named `inhere` is present.

### Step 3 – Enter the `inhere` Directory

Move into the `inhere` directory.

Bash

```
bandit3@bandit:~$ cd inhere
```

Verify your location.

Bash

```
bandit3@bandit:~/inhere$ pwd
```

Output

```
/home/bandit3/inhere
```

### Step 4 – Display Hidden Files

A normal `ls` shows nothing because the password file is hidden.

Bash

```
bandit3@bandit:~/inhere$ ls
```

Output

```
(No output)
```

Now display all files, including hidden ones.

Bash

```
bandit3@bandit:~/inhere$ ls -a
```

Output

```
.
..
...Hiding-From-You
```

### Understanding the Output

|
File

|

Meaning

|
| --- | --- |
|

`.`

|

Current directory.

|
|

`..`

|

Parent directory.

|
|

`...Hiding-From-You`

|

Hidden file containing the password.

|

The file is hidden because its name begins with `.`.

### Step 5 – Read the Hidden File

Display the contents of the hidden file.

Bash

```
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
```

Output

```
<Bandit Level 4 Password>
```

This is the password for bandit4.

### Step 6 – Exit the Current Session

Bash

```
bandit3@bandit:~/inhere$ exit
```

Output

```
logout
Connection to bandit.labs.overthewire.org closed.
```

### Step 7 – Log into Bandit Level 4

From your Linux terminal, connect to the next level.

Bash

```
user@ubuntu:~$ ssh bandit4@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit4@bandit.labs.overthewire.org's password:
```

Enter the password obtained from the hidden file.

Successful Login Prompt

Bash

```
bandit4@bandit:~$
```

You are now logged into Bandit Level 4.

## Complete Command Sequence

Bash

```
bandit3@bandit:~$ pwd
bandit3@bandit:~$ ls
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls -a
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
bandit3@bandit:~/inhere$ exit

user@ubuntu:~$ ssh bandit4@bandit.labs.overthewire.org -p 2220
```

## Explanation

|
Command

|

Explanation

|
| --- | --- |
|

`pwd`

|

Confirms the current working directory.

|
|

`ls`

|

Shows visible files and directories only.

|
|

`cd inhere`

|

Enters the target directory.

|
|

`ls -a`

|

Displays all files, including hidden files.

|
|

`cat ...Hiding-From-You`

|

Reads the hidden file containing the password.

|
|

`exit`

|

Closes the current SSH session.

|
|

`ssh bandit4@bandit.labs.overthewire.org -p 2220`

|

Connects to Bandit Level 4 using SSH.

|

## Why `ls -a` Is Required

|
Command

|

Result

|
| --- | --- |
|

`ls`

|

Shows only visible files. Hidden files are not displayed.

|
|

`ls -a`

|

Shows all files, including hidden files (`.` and `..`), and files beginning with `.`.

|

The `-a` option stands for all.

## Terminal Output (Example)

Bash

```
bandit3@bandit:~$ pwd
/home/bandit3

bandit3@bandit:~$ ls
inhere

bandit3@bandit:~$ cd inhere

bandit3@bandit:~/inhere$ ls
# No output

bandit3@bandit:~/inhere$ ls -a
.
..
...Hiding-From-You

bandit3@bandit:~/inhere$ cat ...Hiding-From-You
<Bandit Level 4 Password>

bandit3@bandit:~/inhere$ exit
logout
Connection to bandit.labs.overthewire.org closed.

user@ubuntu:~$ ssh bandit4@bandit.labs.overthewire.org -p 2220
bandit4@bandit.labs.overthewire.org's password:
bandit4@bandit:~$
```

## Key Takeaways

* Learned that files beginning with `.` are hidden in Linux.

* Used `ls -a` to display hidden files.

* Navigated into a directory using `cd`.

* Read the password from a hidden file using `cat`.

* Logged into bandit4 using SSH from the Linux terminal.

## Result

Successfully found the hidden file `...Hiding-From-You`, obtained the Bandit Level 4 password, and logged into the bandit4 account using the Linux terminal.

<img width="454" height="256" alt="image" src="https://github.com/user-attachments/assets/54c7e2e9-2119-4c63-97ab-a3dd3c202540" />
