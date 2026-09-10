# Bandit Level 8 → Level 9 (Linux Terminal)

## Level Goal

The password for Bandit Level 9 is stored in the file `data.txt` and is the only line that appears exactly once.

The challenge is to use `sort` and `uniq` together through a pipe (`|`) to find the unique line.

## Concept Learned

This level introduces piping (`|`), which sends the output of one command as the input to another command.

* `sort` arranges all lines in alphabetical order.

* `uniq` removes or filters duplicate lines.

* `uniq -u` prints only lines that occur exactly once.

### Commands Used

| Linux Command | Purpose | |---------------|---------| | `pwd` | Shows the current working directory. | | `ls` | Lists files in the current directory. | | `sort` | Sorts the contents of a file alphabetically. | | `uniq -u` | Displays only unique (non-repeated) lines. | | `|` (pipe) | Sends output from one command to another. | | `exit` | Closes the current SSH session. | | `ssh` | Logs into the next Bandit level. |

## Walkthrough (Linux Terminal)

### Step 1 – Verify Your Current Directory

After logging into bandit8, check your current location.

Bash

```
bandit8@bandit:~$ pwd
```

Output

```
/home/bandit8
```

This confirms that you are inside the bandit8 home directory.

### Step 2 – List Files

Display the files in the current directory.

Bash

```
bandit8@bandit:~$ ls
```

Output

```
data.txt
```

The password is hidden among many repeated lines inside `data.txt`.

### Step 3 – Find the Only Unique Line

Run the following command:

Bash

```
bandit8@bandit:~$ sort data.txt | uniq -u
```

### Explanation of the Command

| Command Part | Meaning | |--------------|---------| | `sort data.txt` | Sorts all lines in `data.txt` alphabetically. | | `|` | Sends the sorted output to the next command. | | `uniq -u` | Prints only the line that appears exactly once. |

Output

```
<Bandit Level 9 Password>
```

This unique line is the password for bandit9.

### Step 4 – Password for Bandit Level 9

```
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```

Copy this password carefully. It will be used to log into bandit9.

### Step 5 – Exit the Current Session

Bash

```
bandit8@bandit:~$ exit
```

Output

```
logout
Connection to bandit.labs.overthewire.org closed.
```

### Step 6 – Log into Bandit Level 9

From your Linux terminal, connect to the next level.

Bash

```
user@ubuntu:~$ ssh bandit9@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit9@bandit.labs.overthewire.org's password:
```

Enter the password obtained from the unique line.

Successful Login Prompt

Bash

```
bandit9@bandit:~$
```

You are now logged into Bandit Level 9.

## Complete Command Sequence

Bash

```
bandit8@bandit:~$ pwd
bandit8@bandit:~$ ls
bandit8@bandit:~$ sort data.txt | uniq -u
bandit8@bandit:~$ exit

user@ubuntu:~$ ssh bandit9@bandit.labs.overthewire.org -p 2220
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

`sort data.txt`

|

Sorts all lines alphabetically so duplicates are grouped together.

|
|

`uniq -u`

|

Displays only the line that appears exactly once.

|
|

`sort data.txt \| uniq -u`

|

Combines both commands using a pipe to find the unique line.

|
|

`exit`

|

Closes the current SSH session.

|
|

`ssh bandit9@bandit.labs.overthewire.org -p 2220`

|

Connects to Bandit Level 9 using SSH.

|

## Why `sort` Is Required Before `uniq`

`uniq` only compares adjacent lines. If duplicate lines are scattered throughout the file, it cannot identify them correctly.

|
Command

|

Result

|
| --- | --- |
|

`uniq -u data.txt`

|

May not work correctly because duplicate lines are not next to each other.

|
|

`sort data.txt \| uniq -u`

|

Groups duplicate lines together, allowing `uniq` to identify the single unique line.

|

So, sorting is an essential first step before using `uniq`.

## Terminal Output (Example)

Bash

```
bandit8@bandit:~$ pwd
/home/bandit8

bandit8@bandit:~$ ls
data.txt

bandit8@bandit:~$ sort data.txt | uniq -u
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

bandit8@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

user@ubuntu:~$ ssh bandit9@bandit.labs.overthewire.org -p 2220
bandit9@bandit.labs.overthewire.org's password:
bandit9@bandit:~$
```

## Key Takeaways

* Learned how to use pipes (`|`) in Linux.

* Combined `sort` and `uniq -u` to process text efficiently.

* Understood that `uniq` works only on adjacent duplicate lines.

* Retrieved the password for Bandit Level 9 from the unique line.

* Logged into bandit9 using SSH from the Linux terminal.

## Result

Successfully found the only unique line in `data.txt`, obtained the Bandit Level 9 password, and logged into the bandit9 account using the Linux terminal.

<img width="447" height="130" alt="image" src="https://github.com/user-attachments/assets/c6d3a3fe-ca29-44bc-aa2b-a5cd2bc82e5b" />
