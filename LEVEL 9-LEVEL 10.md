# Bandit Level 9 → Level 10 (Linux Terminal)

## Level Goal

The password for Bandit Level 10 is stored in the file `data.txt` in one of the few human-readable strings, preceded by several `=` characters.

The challenge is to extract readable text from a binary file and search for the password.

## Concept Learned

This level introduces the `strings` command.

* `strings` extracts human-readable text from a binary file.

* `grep` filters the extracted text and finds the line containing a specific pattern (`=` characters).

* A pipe (`|`) sends the output of `strings` directly to `grep`.

### Commands Used

| Linux Command | Purpose | |---------------|---------| | `pwd` | Shows the current working directory. | | `ls` | Lists files in the current directory. | | `strings` | Extracts readable strings from a binary file. | | `grep` | Searches for a specific pattern in the extracted strings. | | `|` (pipe) | Sends output from one command to another. | | `exit` | Closes the current SSH session. | | `ssh` | Logs into the next Bandit level. |

## Walkthrough (Linux Terminal)

### Step 1 – Verify Your Current Directory

After logging into bandit9, check your current location.

Bash

```
bandit9@bandit:~$ pwd
```

Output

```
/home/bandit9
```

This confirms that you are inside the bandit9 home directory.

### Step 2 – List Files

Display the files in the current directory.

Bash

```
bandit9@bandit:~$ ls
```

Output

```
data.txt
```

The file contains mostly binary data, so viewing it with `cat` would display unreadable characters.

### Step 3 – Extract Readable Strings and Search for `=`

Run the following command:

Bash

```
bandit9@bandit:~$ strings data.txt | grep "=="
```

### Explanation of the Command

| Command Part | Meaning | |--------------|---------| | `strings data.txt` | Extracts all human-readable strings from the binary file. | | `|` | Sends the extracted strings to the next command. | | `grep "=="` | Finds lines containing multiple `=` characters. |

Output

```
========== <Bandit Level 10 Password>
```

The text after the `=` characters is the password for the next level.

### Step 4 – Password for Bandit Level 10

```
<Bandit Level 10 Password>
```

Copy this password carefully. It will be used to log into bandit10.

### Step 5 – Exit the Current Session

Bash

```
bandit9@bandit:~$ exit
```

Output

```
logout
Connection to bandit.labs.overthewire.org closed.
```

### Step 6 – Log into Bandit Level 10

From your Linux terminal, connect to the next level.

Bash

```
user@ubuntu:~$ ssh bandit10@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit10@bandit.labs.overthewire.org's password:
```

Enter the password obtained from `strings` and `grep`.

Successful Login Prompt

Bash

```
bandit10@bandit:~$
```

You are now logged into Bandit Level 10.

## Complete Command Sequence

Bash

```
bandit9@bandit:~$ pwd
bandit9@bandit:~$ ls
bandit9@bandit:~$ strings data.txt | grep "=="
bandit9@bandit:~$ exit

user@ubuntu:~$ ssh bandit10@bandit.labs.overthewire.org -p 2220
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

`strings data.txt`

|

Extracts readable text from the binary file.

|
|

`grep "=="`

|

Filters only the lines containing multiple `=` characters.

|
|

`strings data.txt \| grep "=="`

|

Combines both commands to locate the password.

|
|

`exit`

|

Closes the current SSH session.

|
|

`ssh bandit10@bandit.labs.overthewire.org -p 2220`

|

Connects to Bandit Level 10 using SSH.

|

## Why Use `strings`?

|
Command

|

Result

|
| --- | --- |
|

`cat data.txt`

|

Displays unreadable binary characters.

|
|

`strings data.txt`

|

Displays only readable text inside the binary file.

|
|

`strings data.txt \| grep "=="`

|

Displays only the readable line containing the password.

|

The `strings` command is useful for extracting hidden or readable text from binary files.

## Terminal Output (Example)

Bash

```
bandit9@bandit:~$ pwd
/home/bandit9

bandit9@bandit:~$ ls
data.txt

bandit9@bandit:~$ strings data.txt | grep "=="
========== <Bandit Level 10 Password>

bandit9@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

user@ubuntu:~$ ssh bandit10@bandit.labs.overthewire.org -p 2220
bandit10@bandit.labs.overthewire.org's password:
bandit10@bandit:~$
```

## Key Takeaways

* Learned how to extract readable text from a binary file using `strings`.

* Combined `strings` and `grep` using a pipe (`|`).

* Searched for a specific pattern (`=` characters) to locate the password.

* Retrieved the password for Bandit Level 10.

* Logged into bandit10 using SSH from the Linux terminal.

## Result

Successfully extracted the readable string from `data.txt`, obtained the Bandit Level 10 password, and logged into the bandit10 account using the Linux terminal.

<img width="456" height="143" alt="image" src="https://github.com/user-attachments/assets/e97ec14e-4e05-44d4-8d07-7c3f54e949a4" />
