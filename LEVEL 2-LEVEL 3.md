# Bandit Level 2 → Level 3 

## Level Goal

The password for Bandit Level 3 is stored in a file named `--spaces in this filename--` located in the home directory of `bandit2`.

The challenge is to learn how to access filenames that contain spaces while connected to the remote Linux server from Windows Command Prompt or PowerShell.

## Concept Learned

In Linux, spaces separate command arguments. If a filename contains spaces, the shell treats each word as a different argument unless the filename is quoted or the spaces are escaped.

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

## Walkthrough (Windows Command Prompt / PowerShell)

### Step 1 – Verify Your Current Directory

After logging into bandit2 from Windows Command Prompt or PowerShell, check your current location on the remote server.

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

### Step 4 – Exit the Current SSH Session

Bash

```
bandit2@bandit:~$ exit
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

### Step 5 – Log into Bandit Level 3

From Windows Command Prompt or PowerShell, connect to the next Bandit level.

PowerShell

```
C:\Users\YourUsername> ssh bandit3@bandit.labs.overthewire.org -p 2220
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

PowerShell

```
# Inside the Bandit server
pwd
ls
cat "./--spaces in this filename--"
exit

# Back in Windows Command Prompt / PowerShell
ssh bandit3@bandit.labs.overthewire.org -p 2220
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

Closes the current SSH session and returns to Windows Command Prompt or PowerShell.

|
|

`ssh bandit3@bandit.labs.overthewire.org -p 2220`

|

Connects to Bandit Level 3 using SSH.

|

## Why Quotes Are Required

<table class="_6IUVGW_Table" data-d-column-sizing="auto" data-d-dividers="" style="table-layout: auto;"><tbody><tr data-d-component="table-row"><td data-d-component="table-cell" data-d-has-width="" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text"><span class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-default-strong="" data-d-inline="">Command</span></p></td><td data-d-component="table-cell" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text"><span class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-default-strong="" data-d-inline="">Result</span></p></td></tr><tr data-d-component="table-row"><td data-d-component="table-cell" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-whitespace="preserve">cat --spaces in this filename--</p></td><td data-d-component="table-cell" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text">Treats <code class="er4J8W_Code" data-d-component="code">--spaces</code>, <code class="er4J8W_Code" data-d-component="code">in</code>, <code class="er4J8W_Code" data-d-component="code">this</code>, and <code class="er4J8W_Code" data-d-component="code">filename--</code> as separate arguments and fails.</p></td></tr><tr data-d-component="table-row"><td data-d-component="table-cell" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-whitespace="preserve">cat "./--spaces in this filename--"</p></td><td data-d-component="table-cell" data-d-valign="start">Reads the complete filename successfully.</td></tr></tbody></table>

Quotes prevent the shell from splitting the filename at spaces.

## Terminal Output (Example)

```
C:\Users\YourUsername> ssh bandit2@bandit.labs.overthewire.org -p 2220
bandit2@bandit.labs.overthewire.org's password:

bandit2@bandit:~$ pwd
/home/bandit2

bandit2@bandit:~$ ls
--spaces in this filename--

bandit2@bandit:~$ cat "./--spaces in this filename--"
<Bandit Level 3 Password>

bandit2@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

C:\Users\YourUsername> ssh bandit3@bandit.labs.overthewire.org -p 2220
bandit3@bandit.labs.overthewire.org's password:

bandit3@bandit:~$
```

## Key Takeaways

* Learned how Linux handles filenames containing spaces.

* Used double quotes to access a file with spaces in its name.

* Learned an alternative method using backslash (`\`) to escape spaces.

* Retrieved the password for Bandit Level 3.

* Logged into bandit3 using SSH from Windows Command Prompt / PowerShell.

## Result

Successfully accessed the file `--spaces in this filename--`, obtained the Bandit Level 3 password, and logged into the bandit3 account using Windows Command Prompt / PowerShell.

<img width="1232" height="167" alt="image" src="https://github.com/user-attachments/assets/92fa683c-0d03-43e0-960a-b5f0bff43d9a" />
