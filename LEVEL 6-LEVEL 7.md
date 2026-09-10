# Bandit Level 6 → Level 7 (Linux Terminal)

## Level Goal

The password for Bandit Level 7 is stored somewhere on the server. The correct file has all of the following properties:

* Owned by user: `bandit7`

* Owned by group: `bandit6`

* Exactly 33 bytes in size.

The challenge is to search the entire server using file ownership, group ownership, and file size.

## Concept Learned

The `find` command can search files across the entire filesystem using properties like owner, group, and size.

Since many directories cannot be accessed by `bandit6`, the search produces Permission denied errors. These errors can be hidden using `2>/dev/null`.

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

`find`

|

Searches the entire server for a matching file.

|
|

`cat`

|

Displays the contents of the located file.

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

After logging into bandit6, check your current location.

Bash

```
bandit6@bandit:~$ pwd
```

Output

```
/home/bandit6
```

This confirms that you are inside the bandit6 home directory.

### Step 2 – Search the Entire Server

Run the following command:

Bash

```
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

### Explanation of the Command

|
Option

|

Meaning

|
| --- | --- |
|

`/`

|

Start searching from the root directory (entire server).

|
|

`-user bandit7`

|

Find files owned by bandit7.

|
|

`-group bandit6`

|

Find files belonging to the bandit6 group.

|
|

`-size 33c`

|

Find files that are exactly 33 bytes (`c` = bytes).

|
|

`2>/dev/null`

|

Hide Permission denied error messages.

|

Output

```
/var/lib/dpkg/info/bandit7.password
```

The matching file is located in `/var/lib/dpkg/info/`.

### Step 3 – Read the Password File

Display the contents of the file.

Bash

```
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
```

Output

```
<Bandit Level 7 Password>
```

This is the password for bandit7.

### Step 4 – Exit the Current Session

Bash

```
bandit6@bandit:~$ exit
```

Output

```
logout
Connection to bandit.labs.overthewire.org closed.
```

### Step 5 – Log into Bandit Level 7

From your Linux terminal, connect to the next level.

Bash

```
user@ubuntu:~$ ssh bandit7@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit7@bandit.labs.overthewire.org's password:
```

Enter the password obtained from `bandit7.password`.

Successful Login Prompt

Bash

```
bandit7@bandit:~$
```

You are now logged into Bandit Level 7.

## Complete Command Sequence

Bash

```
bandit6@bandit:~$ pwd
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ exit

user@ubuntu:~$ ssh bandit7@bandit.labs.overthewire.org -p 2220
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

`find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`

|

Searches the entire filesystem for a file matching the required owner, group, and size.

|
|

`cat /var/lib/dpkg/info/bandit7.password`

|

Reads the password stored in the located file.

|
|

`exit`

|

Closes the current SSH session.

|
|

`ssh bandit7@bandit.labs.overthewire.org -p 2220`

|

Connects to Bandit Level 7 using SSH.

|

## Why `2>/dev/null` Is Used

Searching from `/` accesses many protected directories that `bandit6` cannot read.

|
Command

|

Result

|
| --- | --- |
|

`find / -user bandit7 -group bandit6 -size 33c`

|

Displays many Permission denied messages along with the result.

|
|

`find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`

|

Displays only the matching file, making the output clean.

|

### What `2>/dev/null` Means

* `2` → Standard Error (stderr).

* `>` → Redirect output.

* `/dev/null` → A special Linux file that discards anything sent to it.

So, `2>/dev/null` sends all error messages to `/dev/null`, hiding them from the terminal.

## Terminal Output (Example)

Bash

```
bandit6@bandit:~$ pwd
/home/bandit6

bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password

bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
<Bandit Level 7 Password>

bandit6@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

user@ubuntu:~$ ssh bandit7@bandit.labs.overthewire.org -p 2220
bandit7@bandit.labs.overthewire.org's password:
bandit7@bandit:~$
```

## Key Takeaways

* Learned how to search the entire Linux filesystem using `find`.

* Filtered files by owner, group, and size simultaneously.

* Used `2>/dev/null` to suppress permission error messages.

* Retrieved the password for Bandit Level 7 from `/var/lib/dpkg/info/bandit7.password`.

* Logged into bandit7 using SSH from the Linux terminal.

## Result

Successfully located `/var/lib/dpkg/info/bandit7.password`, obtained the Bandit Level 7 password, and logged into the bandit7 account using the Linux terminal.

<img width="847" height="281" alt="image" src="https://github.com/user-attachments/assets/28968ddf-34c8-414e-b739-ecd4ff2e92a6" />
