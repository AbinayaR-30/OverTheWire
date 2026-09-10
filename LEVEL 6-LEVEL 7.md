# Bandit Level 6 → Level 7 (Windows Command Prompt / PowerShell)

## Level Goal

The password for Bandit Level 7 is stored somewhere on the server. The correct file has all of the following properties:

* Owned by user: `bandit7`

* Owned by group: `bandit6`

* Exactly 33 bytes in size

The challenge is to search the entire server using file ownership, group ownership, and file size while connected to the remote Linux server from Windows Command Prompt or PowerShell.

## Concept Learned

The `find` command can search the entire Linux filesystem using multiple conditions such as owner, group, and file size. Since some directories are protected, permission errors can be hidden using `2>/dev/null`.

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

`find`

|

Searches the filesystem for files matching specific conditions.

|
|

`cat`

|

Displays the contents of the located password file.

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

After logging into bandit6 from Windows Command Prompt or PowerShell, check your current location on the remote server.

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

### Step 4 – Exit the Current SSH Session

Bash

```
bandit6@bandit:~$ exit
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

### Step 5 – Log into Bandit Level 7

From Windows Command Prompt or PowerShell, connect to the next Bandit level.

PowerShell

```
C:\Users\YourUsername> ssh bandit7@bandit.labs.overthewire.org -p 2220
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

PowerShell

```
# Inside the Bandit server
pwd
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
exit

# Back in Windows Command Prompt / PowerShell
ssh bandit7@bandit.labs.overthewire.org -p 2220
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

Closes the current SSH session and returns to Windows Command Prompt or PowerShell.

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

```
C:\Users\YourUsername> ssh bandit6@bandit.labs.overthewire.org -p 2220
bandit6@bandit.labs.overthewire.org's password:

bandit6@bandit:~$ pwd
/home/bandit6

bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password

bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
<Bandit Level 7 Password>

bandit6@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

C:\Users\YourUsername> ssh bandit7@bandit.labs.overthewire.org -p 2220
bandit7@bandit.labs.overthewire.org's password:

bandit7@bandit:~$
```

## Key Takeaways

* Learned how to search the entire Linux filesystem using `find`.

* Filtered files by owner, group, and size simultaneously.

* Used `2>/dev/null` to suppress permission error messages.

* Retrieved the password for Bandit Level 7 from `/var/lib/dpkg/info/bandit7.password`.

* Logged into bandit7 using SSH from Windows Command Prompt / PowerShell.

## Result

Successfully located `/var/lib/dpkg/info/bandit7.password`, obtained the Bandit Level 7 password, and logged into the bandit7 account using Windows Command Prompt / PowerShell.
