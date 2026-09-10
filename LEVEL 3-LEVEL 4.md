# Bandit Level 3 → Level 4 (Windows Command Prompt / PowerShell)

## Level Goal

The password for Bandit Level 4 is stored in a hidden file inside the `inhere` directory.

The challenge is to learn how to view and access hidden files in Linux while connected to the remote server from Windows Command Prompt or PowerShell.

## Concept Learned

In Linux, files and directories whose names begin with a dot (`.`) are called hidden files. They are not displayed with a normal `ls` command.

To view hidden files, use the `-a` option with `ls`.

### Commands Used

|
Command

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

## Walkthrough (Windows Command Prompt / PowerShell)

### Step 1 – Verify Your Current Directory

After logging into bandit3 from Windows Command Prompt or PowerShell, check your current location on the remote server.

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

### Step 6 – Exit the Current SSH Session

Bash

```
bandit3@bandit:~/inhere$ exit
```

Output

```
logout
Connection to bandit.labs.overthewire.org closed.
```

You will return to your Windows Command Prompt or PowerShell prompt.

Example:

cmd

```
C:\Users\YourUsername>
```

### Step 7 – Log into Bandit Level 4

From Windows Command Prompt or PowerShell, connect to the next Bandit level.

PowerShell

```
C:\Users\YourUsername> ssh bandit4@bandit.labs.overthewire.org -p 2220
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

PowerShell

```
# Inside the Bandit server
pwd
ls
cd inhere
ls -a
cat ...Hiding-From-You
exit

# Back in Windows Command Prompt / PowerShell
ssh bandit4@bandit.labs.overthewire.org -p 2220
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

Confirms the current working directory on the remote Linux server.

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

Closes the current SSH session and returns to Windows Command Prompt or PowerShell.

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

Shows all files, including hidden files (`.` and `..`) and files beginning with `.`.

|

The `-a` option stands for all.

## Terminal Output (Example)

```
C:\Users\YourUsername> ssh bandit3@bandit.labs.overthewire.org -p 2220
bandit3@bandit.labs.overthewire.org's password:

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

C:\Users\YourUsername> ssh bandit4@bandit.labs.overthewire.org -p 2220
bandit4@bandit.labs.overthewire.org's password:

bandit4@bandit:~$
```

## Key Takeaways

* Learned that files beginning with `.` are hidden in Linux.

* Used `ls -a` to display hidden files.

* Navigated into a directory using `cd`.

* Read the password from a hidden file using `cat`.

* Logged into bandit4 using SSH from Windows Command Prompt / PowerShell.

## Result

Successfully found the hidden file `...Hiding-From-You`, obtained the Bandit Level 4 password, and logged into the bandit4 account using Windows Command Prompt / PowerShell.
<img width="309" height="58" alt="image" src="https://github.com/user-attachments/assets/1fe91cd0-e476-4b00-a3d7-9abe424ee8d7" />
<img width="538" height="57" alt="image" src="https://github.com/user-attachments/assets/770fcff6-7ff9-4ee2-a31c-b4ff1db99250" />
<img width="1029" height="138" alt="image" src="https://github.com/user-attachments/assets/4121563d-aad4-4260-a702-9cb593979fa7" />
<img width="688" height="36" alt="image" src="https://github.com/user-attachments/assets/7a92a657-716e-46e4-a8a7-9bc7a541802c" />
<img width="685" height="60" alt="image" src="https://github.com/user-attachments/assets/d1cf3437-ba8c-4129-9da5-789e24581a03" />
