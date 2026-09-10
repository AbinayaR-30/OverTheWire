# Bandit Level 2 → Level 3 (Linux Terminal)

## Level Goal

The password for Bandit Level 3 is stored in a file named `--spaces in this filename--` located in the home directory of `bandit2`.

The challenge is to learn how to access filenames that contain spaces.

## Concept Learned

In Linux, spaces separate command arguments. If a filename contains spaces, the shell treats each word as a different argument unless the filename is quoted or the spaces are escaped.

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

Lists files in the current directory.

|
|

`cat`

|

Displays the contents of the file.

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

After logging into bandit2, check your current location.

Bash

```
bandit2@bandit:~$ pwd
```

Output

```
/home/bandit2
```

This confirms that you are inside the bandit2 home directory.

### Step 2 – List Files

Display the files in the current directory.

Bash

```
bandit2@bandit:~$ ls
```

Output

```
--spaces in this filename--
```

The directory contains a file whose name includes spaces.

### Step 3 – Read the File with Spaces

Use double quotes around the filename.

Bash

```
bandit2@bandit:~$ cat "./--spaces in this filename--"
```

Output

```
<Bandit Level 3 Password>
```

This is the password for bandit3.

> Note: Quotation marks tell the shell to treat the entire filename as one argument.

### Alternative Method (Escaping Spaces)

You can also escape each space using a backslash (`\`).

Bash

```
bandit2@bandit:~$ cat ./--spaces\ in\ this\ filename--
```

Both commands produce the same output.

### Step 4 – Exit the Current Session

Bash

```
bandit2@bandit:~$ exit
```

Output

```
logout
Connection to bandit.labs.overthewire.org closed.
```

### Step 5 – Log into Bandit Level 3

From your Linux terminal, connect to the next level.

Bash

```
user@ubuntu:~$ ssh bandit3@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit3@bandit.labs.overthewire.org's password:
```

Enter the password obtained from the file.

Successful Login Prompt

Bash

```
bandit3@bandit:~$
```

You are now logged into Bandit Level 3.

## Complete Command Sequence

Bash

```
bandit2@bandit:~$ pwd
bandit2@bandit:~$ ls
bandit2@bandit:~$ cat "./--spaces in this filename--"
bandit2@bandit:~$ exit

user@ubuntu:~$ ssh bandit3@bandit.labs.overthewire.org -p 2220
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

Lists the files available in the directory.

|
|

`cat "./--spaces in this filename--"`

|

Reads the file whose name contains spaces.

|
|

`cat ./--spaces\ in\ this\ filename--`

|

Reads the same file by escaping each space.

|
|

`exit`

|

Closes the current SSH session.

|
|

`ssh bandit3@bandit.labs.overthewire.org -p 2220`

|

Connects to Bandit Level 3 using SSH.

|

## Why Quotes Are Required

|
Command

|

Result

|
| --- | --- |
|

`cat --spaces in this filename--`

|

Treats `--spaces`, `in`, `this`, and `filename--` as separate arguments and fails.

|
|

`cat "./--spaces in this filename--"`

|

Reads the complete filename successfully.

|

Quotes prevent the shell from splitting the filename at spaces.

## Terminal Output (Example)

Bash

```
bandit2@bandit:~$ pwd
/home/bandit2

bandit2@bandit:~$ ls
--spaces in this filename--

bandit2@bandit:~$ cat "./--spaces in this filename--"
<Bandit Level 3 Password>

bandit2@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

user@ubuntu:~$ ssh bandit3@bandit.labs.overthewire.org -p 2220
bandit3@bandit.labs.overthewire.org's password:
bandit3@bandit:~$
```

## Key Takeaways

* Learned how Linux handles filenames containing spaces.

* Used double quotes to access a file with spaces in its name.

* Learned an alternative method using backslash (`\`) to escape spaces.

* Retrieved the password for Bandit Level 3.

* Logged into bandit3 using SSH from the Linux terminal.

## Result

Successfully accessed the file `--spaces in this filename--`, obtained the Bandit Level 3 password, and logged into the bandit3 account using the Linux terminal.

<img width="641" height="316" alt="image" src="https://github.com/user-attachments/assets/707aefd1-457b-4fac-82a3-935c9daf6660" />
