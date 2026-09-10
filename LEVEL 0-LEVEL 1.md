# Bandit Level 0 → Level 1 (Windows Command Prompt / PowerShell)

## Level Goal

The password for Bandit Level 1 is stored in a file named `readme` located in the home directory of `bandit0`.

The objective is to:

1. Locate the `readme` file.

2. Display its contents.

3. Use the retrieved password to log in as bandit1.

## Concept Learned

This level introduces basic Linux file operations while accessing a remote Linux server from Windows Command Prompt or PowerShell.

### Commands Used

|
Command

|

Purpose

|
| --- | --- |
|

`ls`

|

Lists files and directories in the current directory.

|
|

`cat`

|

Displays the contents of a file.

|
|

`pwd`

|

Shows the current working directory.

|
|

`exit`

|

Closes the current SSH session.

|
|

`ssh`

|

Logs into the next Bandit level using the new password.

|

## Walkthrough (Windows Command Prompt / PowerShell)

### Step 1 – Verify Your Current Directory

After logging into bandit0 from Windows Command Prompt or PowerShell, check where you are on the remote server.

Bash

```
bandit0@bandit:~$ pwd
```

Output

```
/home/bandit0
```

This is the home directory for `bandit0` on the remote Linux server.

### Step 2 – List Files in the Home Directory

Use the `ls` command.

Bash

```
bandit0@bandit:~$ ls
```

Output

```
readme
```

The directory contains a file named `readme`.

### Step 3 – Read the Password from the File

Use `cat` to display the contents.

Bash

```
bandit0@bandit:~$ cat readme
```

Output

```
<Bandit Level 1 Password>
```

This string is the password for bandit1.

> Note: Copy this password into a local text file (such as Notepad) because you will need it to log in to the next level.

### Step 4 – Exit the Current SSH Session

Leave the `bandit0` session.

Bash

```
bandit0@bandit:~$ exit
```

You will return to your Windows Command Prompt or PowerShell prompt.

Example:

cmd

```
C:\Users\YourUsername>
```

### Step 5 – Log into Bandit Level 1

From Windows Command Prompt or PowerShell, use SSH with the next username.

PowerShell

```
C:\Users\YourUsername> ssh bandit1@bandit.labs.overthewire.org -p 2220
```

When prompted, paste the password obtained from the `readme` file.

```
bandit1@bandit.labs.overthewire.org's password:
```

After entering the correct password, you will see the Bandit Level 1 shell prompt.

Bash

```
bandit1@bandit:~$
```

You are now logged into Bandit Level 1.

## Complete Command Sequence

PowerShell

```
# Inside the Bandit server
pwd
ls
cat readme
exit

# Back in Windows Command Prompt / PowerShell
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

## Explanation

* `pwd` confirms the current location on the remote Linux server.

* `ls` lists the available files.

* `cat readme` prints the contents of the `readme` file.

* `exit` closes the current SSH session and returns to Windows Command Prompt or PowerShell.

* `ssh` establishes a new connection as `bandit1`.

## Key Takeaways

* Learned how to list files using `ls`.

* Learned how to read file contents using `cat`.

* Retrieved the password stored inside a file.

* Exited the current SSH session using `exit`.

* Logged into the next Bandit level from Windows Command Prompt / PowerShell using SSH.

## Result

Successfully obtained the Bandit Level 1 password from the `readme` file and logged into the `bandit1` account using Windows Command Prompt / PowerShell.

<img width="1245" height="249" alt="image" src="https://github.com/user-attachments/assets/f8060949-d291-40ef-a9a9-ed8c68cdf809" />
