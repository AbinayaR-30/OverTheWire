# Bandit Level 4 → Level 5 (Windows Command Prompt / PowerShell)

## Level Goal

The password for Bandit Level 5 is stored in the only human-readable file inside the `inhere` directory.

The challenge is to identify a human-readable file among several files containing binary or non-readable data while connected to the remote Linux server from Windows Command Prompt or PowerShell.

## Concept Learned

Linux provides the `file` command to identify the type of a file. Instead of opening every file manually, `file` tells whether a file is ASCII text, binary data, executable, image, archive, and more.

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

Lists files in the current directory.

|
|

`cd`

|

Changes into the `inhere` directory.

|
|

`file`

|

Identifies the type of each file.

|
|

`cat`

|

Displays the contents of the human-readable file.

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

After logging into bandit4 from Windows Command Prompt or PowerShell, check your current location on the remote server.

Bash

```
bandit4@bandit:~$ pwd
```

Output

```
/home/bandit4
```

This confirms that you are inside the bandit4 home directory.

### Step 2 – List Files

Display the contents of the current directory.

Bash

```
bandit4@bandit:~$ ls
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
bandit4@bandit:~$ cd inhere
```

Verify your location.

Bash

```
bandit4@bandit:~/inhere$ pwd
```

Output

```
/home/bandit4/inhere
```

### Step 4 – List All Files

Display all files inside the directory.

Bash

```
bandit4@bandit:~/inhere$ ls
```

Output

```
file00
file01
file02
file03
file04
file05
file06
file07
file08
file09
```

There are multiple files, but only one contains readable text.

### Step 5 – Identify the Human-Readable File

Run the `file` command on all files.

Bash

```
bandit4@bandit:~/inhere$ file ./*
```

Output (Example)

```
./file00: data
./file01: data
./file02: data
./file03: ASCII text
./file04: data
./file05: data
./file06: data
./file07: data
./file08: data
./file09: data
```

The only ASCII text file is `file03`.

> Note: The filename may vary, but only one file will be identified as ASCII text.

### Step 6 – Read the Human-Readable File

Display the contents of the ASCII text file.

Bash

```
bandit4@bandit:~/inhere$ cat ./file03
```

Output

```
<Bandit Level 5 Password>
```

This is the password for bandit5.

### Step 7 – Exit the Current SSH Session

Bash

```
bandit4@bandit:~/inhere$ exit
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

### Step 8 – Log into Bandit Level 5

From Windows Command Prompt or PowerShell, connect to the next Bandit level.

PowerShell

```
C:\Users\YourUsername> ssh bandit5@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit5@bandit.labs.overthewire.org's password:
```

Enter the password obtained from the human-readable file.

Successful Login Prompt

Bash

```
bandit5@bandit:~$
```

You are now logged into Bandit Level 5.

## Complete Command Sequence

PowerShell

```
# Inside the Bandit server
pwd
ls
cd inhere
file ./*
cat ./file03
exit

# Back in Windows Command Prompt / PowerShell
ssh bandit5@bandit.labs.overthewire.org -p 2220
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

Lists files in the current directory.

|
|

`cd inhere`

|

Enters the directory containing multiple files.

|
|

`file ./*`

|

Checks the type of every file in the directory.

|
|

`cat ./file03`

|

Displays the contents of the human-readable file.

|
|

`exit`

|

Closes the current SSH session and returns to Windows Command Prompt or PowerShell.

|
|

`ssh bandit5@bandit.labs.overthewire.org -p 2220`

|

Connects to Bandit Level 5 using SSH.

|

## Why Use the `file` Command?

|
Command

|

Result

|
| --- | --- |
|

`cat file00`

|

May display unreadable or binary characters.

|
|

`file file00`

|

Identifies whether the file is binary, text, executable, archive, or another format.

|
|

`file ./*`

|

Checks every file at once and quickly identifies the correct one.

|

The `file` command is useful when you do not know the contents or format of a file.

## Terminal Output (Example)

```
C:\Users\YourUsername> ssh bandit4@bandit.labs.overthewire.org -p 2220
bandit4@bandit.labs.overthewire.org's password:

bandit4@bandit:~$ pwd
/home/bandit4

bandit4@bandit:~$ ls
inhere

bandit4@bandit:~$ cd inhere

bandit4@bandit:~/inhere$ ls
file00  file01  file02  file03  file04
file05  file06  file07  file08  file09

bandit4@bandit:~/inhere$ file ./*
./file00: data
./file01: data
./file02: data
./file03: ASCII text
./file04: data
./file05: data
./file06: data
./file07: data
./file08: data
./file09: data

bandit4@bandit:~/inhere$ cat ./file03
<Bandit Level 5 Password>

bandit4@bandit:~/inhere$ exit
logout
Connection to bandit.labs.overthewire.org closed.

C:\Users\YourUsername> ssh bandit5@bandit.labs.overthewire.org -p 2220
bandit5@bandit.labs.overthewire.org's password:

bandit5@bandit:~$
```

## Key Takeaways

* Learned how to identify file types using the `file` command.

* Distinguished ASCII text files from binary files.

* Used `file ./*` to inspect multiple files at once.

* Used `cat` only on the human-readable file.

* Retrieved the password for Bandit Level 5.

* Logged into bandit5 using SSH from Windows Command Prompt / PowerShell.

## Result

Successfully identified the only human-readable (ASCII text) file in the `inhere` directory, obtained the Bandit Level 5 password, and logged into the bandit5 account using Windows Command Prompt / PowerShell.
