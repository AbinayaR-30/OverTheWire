# Bandit Level 5 → Level 6 

## Level Goal

The password for Bandit Level 6 is stored in a file somewhere inside the `inhere` directory. The correct file has all of the following properties:

* Human-readable

* Exactly 1033 bytes in size

* Not executable

The challenge is to use the `find` command with multiple conditions to locate a specific file while connected to the remote Linux server from Windows Command Prompt or PowerShell.

## Walkthrough (Windows Command Prompt / PowerShell)

### Step 1 – Verify Your Current Directory

After logging into bandit5 from Windows Command Prompt or PowerShell, check your current location on the remote server.

Bash

```
bandit5@bandit:~$ pwd
```

Output

```
/home/bandit5
```

This confirms that you are inside the bandit5 home directory.

### Step 2 – Enter the `inhere` Directory

List the directory contents and move into it.

Bash

```
bandit5@bandit:~$ ls
```

<img width="357" height="69" alt="image" src="https://github.com/user-attachments/assets/317330d7-a686-4143-855e-f1361541d8a5" />


Output

```
inhere
```

Enter the directory.

Bash

```
bandit5@bandit:~$ cd inhere
```

Verify your location.

Bash

```
bandit5@bandit:~/inhere$ pwd
```

Output

```
/home/bandit5/inhere
```

### Step 3 – Find the Required File

Run the following command:

Bash

```
bandit5@bandit:~/inhere$ find . -type f -size 1033c ! -executable
```

### Explanation of the Command

|
Option

|

Meaning

|
| --- | --- |
|

`.`

|

Search from the current directory.

|
|

`-type f`

|

Search only for files.

|
|

`-size 1033c`

|

Find files that are exactly 1033 bytes (`c` = bytes).

|
|

`! -executable`

|

Exclude executable files.

|

Output

```
./maybehere07/.file2
```

The file matching all the required conditions is `.file2` inside the `maybehere07` directory.

### Step 4 – Read the Password File

Display the contents of the file returned by `find`.

Bash

```
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
```

<img width="682" height="61" alt="image" src="https://github.com/user-attachments/assets/49b1095f-7b0d-42e4-8121-986e39b6b476" />


Output

```
<Bandit Level 6 Password>
```

This is the password for bandit6.

### Step 5 – Exit the Current SSH Session

Bash

```
bandit5@bandit:~/inhere$ exit
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

### Step 6 – Log into Bandit Level 6

From Windows Command Prompt or PowerShell, connect to the next Bandit level.

PowerShell

```
C:\Users\YourUsername> ssh bandit6@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit6@bandit.labs.overthewire.org's password:
```

Enter the password obtained from `.file2`.

Successful Login Prompt

Bash

```
bandit6@bandit:~$
```

You are now logged into Bandit Level 6.

## Complete Command Sequence

PowerShell

```
# Inside the Bandit server
pwd
ls
cd inhere
find . -type f -size 1033c ! -executable
cat ./maybehere07/.file2
exit

# Back in Windows Command Prompt / PowerShell
ssh bandit6@bandit.labs.overthewire.org -p 2220
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

Lists files and directories in the current location.

|
|

`cd inhere`

|

Enters the directory containing many subdirectories and files.

|
|

`find . -type f -size 1033c ! -executable`

|

Searches recursively for files that match the required properties.

|
|

`cat ./maybehere07/.file2`

|

Reads the password stored in the located file.

|
|

`exit`

|

Closes the current SSH session and returns to Windows Command Prompt or PowerShell.

|
|

`ssh bandit6@bandit.labs.overthewire.org -p 2220`

|

Connects to Bandit Level 6 using SSH.

|

## Why Use `find`?

|
Command

|

Result

|
| --- | --- |
|

`ls`

|

Shows only files in the current directory.

|
|

`find .`

|

Searches recursively through all subdirectories.

|
|

`find . -type f -size 1033c ! -executable`

|

Finds only the file matching the required properties.

|

The `find` command is much faster than checking hundreds of files manually.

## Terminal Output (Example)

```
C:\Users\YourUsername> ssh bandit5@bandit.labs.overthewire.org -p 2220
bandit5@bandit.labs.overthewire.org's password:

bandit5@bandit:~$ pwd
/home/bandit5

bandit5@bandit:~$ ls
inhere

bandit5@bandit:~$ cd inhere

bandit5@bandit:~/inhere$ find . -type f -size 1033c ! -executable
./maybehere07/.file2

bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
<Bandit Level 6 Password>

bandit5@bandit:~/inhere$ exit
logout
Connection to bandit.labs.overthewire.org closed.

C:\Users\YourUsername> ssh bandit6@bandit.labs.overthewire.org -p 2220
bandit6@bandit.labs.overthewire.org's password:

bandit6@bandit:~$
```

## Key Takeaways

* Learned how to use the `find` command with multiple search conditions.

* Searched recursively inside subdirectories.

* Filtered files by type, size, and permissions.

* Located the required hidden file `./maybehere07/.file2`.

* Retrieved the password for Bandit Level 6.

* Logged into bandit6 using SSH from Windows Command Prompt / PowerShell.

## Result

Successfully located the file `./maybehere07/.file2`, obtained the Bandit Level 6 password, and logged into the bandit6 account using Windows Command Prompt / PowerShell.
