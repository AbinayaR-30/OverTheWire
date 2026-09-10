# Bandit Level 7 → Level 8 (Linux Terminal)

## Level Goal

The password for Bandit Level 8 is stored in the file `data.txt`, next to the word `millionth`.

The challenge is to search for a specific word inside a text file using the `grep` command.

## Concept Learned

The `grep` command searches for a word or pattern inside a file and prints the matching line. It is one of the most commonly used Linux text-processing commands for searching text in files.

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

`grep`

|

Searches for a specific word inside a file.

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

After logging into bandit7, check your current location.

Bash

```
bandit7@bandit:~$ pwd
```

Output

```
/home/bandit7
```

This confirms that you are inside the bandit7 home directory.

### Step 2 – List Files

Display the files in the current directory.

Bash

```
bandit7@bandit:~$ ls
```

Output

```
data.txt
```

The password is stored somewhere inside `data.txt`.

### Step 3 – Search for the Word `millionth`

Use `grep` to search for the word millionth inside the file.

Bash

```
bandit7@bandit:~$ grep "millionth" data.txt
```

Output

```
millionth <next level password>
```

The text after `millionth` is the password for the next Bandit level.

> Note: `grep` prints the entire line that contains the matching word.

### Step 4 – Password for Bandit Level 8

```
<next level password>
```

Copy this password carefully. It will be used to log into bandit8.

### Step 5 – Exit the Current Session

Bash

```
bandit7@bandit:~$ exit
```

Output

```
logout
Connection to bandit.labs.overthewire.org closed.
```

### Step 6 – Log into Bandit Level 8

From your Linux terminal, connect to the next level.

Bash

```
user@ubuntu:~$ ssh bandit8@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit8@bandit.labs.overthewire.org's password:
```

Enter the password obtained from `data.txt`.

Successful Login Prompt

Bash

```
bandit8@bandit:~$
```

You are now logged into Bandit Level 8.

## Complete Command Sequence

Bash

```
bandit7@bandit:~$ pwd
bandit7@bandit:~$ ls
bandit7@bandit:~$ grep "millionth" data.txt
bandit7@bandit:~$ exit

user@ubuntu:~$ ssh bandit8@bandit.labs.overthewire.org -p 2220
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

Lists files in the current directory.

|
|

`grep "millionth" data.txt`

|

Searches `data.txt` for the word millionth and prints the matching line.

|
|

`exit`

|

Closes the current SSH session.

|
|

`ssh bandit8@bandit.labs.overthewire.org -p 2220`

|

Connects to Bandit Level 8 using SSH.

|

## Why Use `grep`?

|
Command

|

Result

|
| --- | --- |
|

`cat data.txt`

|

Displays the entire file, which contains many lines.

|
|

`grep "millionth" data.txt`

|

Displays only the line containing millionth.

|

The `grep` command makes searching large text files quick and efficient.

## Terminal Output (Example)

Bash

```
bandit7@bandit:~$ pwd
/home/bandit7

bandit7@bandit:~$ ls
data.txt

bandit7@bandit:~$ grep "millionth" data.txt
millionth <Bandit Level 8 Password>

bandit7@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

user@ubuntu:~$ ssh bandit8@bandit.labs.overthewire.org -p 2220
bandit8@bandit.labs.overthewire.org's password:
bandit8@bandit:~$
```

## Key Takeaways

* Learned how to search for text inside a file using the `grep` command.

* Used `grep` to find a specific line instead of viewing the entire file.

* Retrieved the password for Bandit Level 8 from `data.txt`.

* Logged into bandit8 using SSH from the Linux terminal.

## Result

Successfully searched `data.txt` with `grep`, found the password next to `millionth`, obtained the Bandit Level 8 password, and logged into the bandit8 account using the Linux terminal.

<img width="528" height="133" alt="image" src="https://github.com/user-attachments/assets/c0de502b-3f23-4929-8569-e83d5c2d12b3" />
