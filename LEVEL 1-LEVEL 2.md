# Bandit Level 1 → Level 2 (Windows Command Prompt / PowerShell)

## Level Goal

The password for Bandit Level 2 is stored in a file named `-` (a single dash) located in the home directory of `bandit1`.

The challenge is to learn how to access files whose names begin with special characters while connected to the remote Linux server from Windows Command Prompt or PowerShell.

## Concept Learned

In Linux, `-` is normally interpreted as standard input (stdin) or as an option by many commands. To access a file literally named `-`, you must specify its path explicitly.

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

`cat ./-`

|

Reads the contents of a file named `-`.

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

After logging into bandit1 from Windows Command Prompt or PowerShell, check your current location on the remote server.

Bash

```
bandit1@bandit:~$ pwd
```

Output

```
/home/bandit1
```

This confirms that you are inside the bandit1 home directory.

### Step 2 – List Files

Display the files in the current directory.

Bash

```
bandit1@bandit:~$ ls
```

Output

```
-
```

The directory contains a file whose name is a single dash (`-`).

### Step 3 – Read the File Named `-`

A normal `cat -` will not work because `-` is treated as standard input.

Correct command

Bash

```
bandit1@bandit:~$ cat ./-
```

Output

```
<Bandit Level 2 Password>
```

This is the password for bandit2.

> Note: `./-` tells Linux to read the file named `-` from the current directory (`.`), instead of interpreting `-` as standard input.

### Step 4 – Exit the Current SSH Session

After copying the password, exit the current SSH session.

Bash

```
bandit1@bandit:~$ exit
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

### Step 5 – Log into Bandit Level 2

From Windows Command Prompt or PowerShell, connect to the next Bandit level.

PowerShell

```
C:\Users\YourUsername> ssh bandit2@bandit.labs.overthewire.org -p 2220
```

When prompted, enter the password obtained from `cat ./-`.

Password Prompt

```
bandit2@bandit.labs.overthewire.org's password:
```

Type the password and press Enter.

Successful Login Prompt

Bash

```
bandit2@bandit:~$
```

You are now logged into Bandit Level 2.

## Complete Command Sequence

PowerShell

```
# Inside the Bandit server
pwd
ls
cat ./-
exit

# Back in Windows Command Prompt / PowerShell
ssh bandit2@bandit.labs.overthewire.org -p 2220
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

Lists the files available in the directory.

|
|

`cat ./-`

|

Reads the file named `-` using its relative path.

|
|

`exit`

|

Closes the current SSH session and returns to Windows Command Prompt or PowerShell.

|
|

`ssh bandit2@bandit.labs.overthewire.org -p 2220`

|

Connects to the next Bandit level using SSH.

|

## Why `cat -` Does Not Work

<table class="_6IUVGW_Table" data-d-column-sizing="auto" data-d-dividers="" style="table-layout: auto;"><tbody><tr data-d-component="table-row"><td data-d-component="table-cell" data-d-has-width="" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text"><span class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-default-strong="" data-d-inline="">Command</span></p></td><td data-d-component="table-cell" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text"><span class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-default-strong="" data-d-inline="">Meaning</span></p></td></tr><tr data-d-component="table-row"><td data-d-component="table-cell" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-whitespace="preserve">cat -</p></td><td data-d-component="table-cell" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text">Reads input from the keyboard (<span class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-default-strong="" data-d-inline="">stdin</span>), not a file.</p></td></tr><tr data-d-component="table-row"><td data-d-component="table-cell" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-whitespace="preserve">cat ./-</p></td><td data-d-component="table-cell" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text">Reads the file named <code class="er4J8W_Code" data-d-component="code">-</code> in the current directory.</p></td></tr></tbody></table>

Adding `./` removes the ambiguity and forces Linux to treat `-` as a filename.

## Terminal Output (Example)

```
C:\Users\YourUsername> ssh bandit1@bandit.labs.overthewire.org -p 2220
bandit1@bandit.labs.overthewire.org's password:

bandit1@bandit:~$ pwd
/home/bandit1

bandit1@bandit:~$ ls
-

bandit1@bandit:~$ cat ./-
<Bandit Level 2 Password>

bandit1@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

C:\Users\YourUsername> ssh bandit2@bandit.labs.overthewire.org -p 2220
bandit2@bandit.labs.overthewire.org's password:

bandit2@bandit:~$
```

## Key Takeaways

* Learned how Linux treats `-` as a special filename.

* Used a relative path (`./`) to access a file with a special name.

* Retrieved the password for Bandit Level 2.

* Logged into bandit2 using SSH from Windows Command Prompt / PowerShell.

## Result

Successfully accessed the file named `-`, obtained the Bandit Level 2 password, and logged into the bandit2 account using Windows Command Prompt / PowerShell.

<img width="887" height="200" alt="image" src="https://github.com/user-attachments/assets/6b6dc09c-c07a-4612-9b9c-7cd0bf7dda1e" />
