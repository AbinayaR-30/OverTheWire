# Bandit Level 10 → Level 11 (Linux Terminal)

## Level Goal

The password for Bandit Level 11 is stored in the file `data.txt`, which contains Base64 encoded data.

The challenge is to decode the Base64-encoded content and retrieve the original password.

## Concept Learned

This level introduces the `base64` command.

* Base64 is an encoding scheme that converts binary or text data into ASCII characters.

* `base64 -d` decodes Base64-encoded data back to its original form.

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

`cat data.txt`

|

Displays the contents of `data.txt`.

|
|

`base64 -d data.txt`

|

Decodes Base64-encoded data.

|
|

`base64 -d data.txt \| cat`

|

Example of using a pipe (`\|`) with `base64`.

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

> Pipe (`|`) sends the output of one command as the input to another command.

## Walkthrough (Linux Terminal)

### Step 1 – Verify Your Current Directory

After logging into bandit10, check your current location.

Bash

```
bandit10@bandit:~$ pwd
```

Output

```
/home/bandit10
```

This confirms that you are inside the bandit10 home directory.

### Step 2 – List Files

Display the files in the current directory.

Bash

```
bandit10@bandit:~$ ls
```

Output

```
data.txt
```

The file `data.txt` contains Base64-encoded text.

### Step 3 – View the Encoded Data (Optional)

Display the contents of the file before decoding.

Bash

```
bandit10@bandit:~$ cat data.txt
```

Output (Example)

```
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTU2cyUlducE5WajNxUnI=
```

This is Base64-encoded content and is not directly readable.

### Step 4 – Decode the Base64 Data

Run the following command:

Bash

```
bandit10@bandit:~$ base64 -d data.txt
```

Output

```
The password is <next level password>
```

The decoded text contains the password for the next Bandit level.

### Step 5 – Password for Bandit Level 11

```
<next level password>
```

Copy this password carefully. It will be used to log into bandit11.

### Step 6 – Exit the Current Session

Bash

```
bandit10@bandit:~$ exit
```

Output

```
logout
Connection to bandit.labs.overthewire.org closed.
```

### Step 7 – Log into Bandit Level 11

From your Linux terminal, connect to the next level.

Bash

```
user@ubuntu:~$ ssh bandit11@bandit.labs.overthewire.org -p 2220
```

When prompted, enter the decoded password.

Password Prompt

```
bandit11@bandit.labs.overthewire.org's password:
```

Type the password and press Enter.

Successful Login Prompt

Bash

```
bandit11@bandit:~$
```

You are now logged into Bandit Level 11.

## Complete Command Sequence

Bash

```
bandit10@bandit:~$ pwd
bandit10@bandit:~$ ls
bandit10@bandit:~$ cat data.txt
bandit10@bandit:~$ base64 -d data.txt
bandit10@bandit:~$ exit

user@ubuntu:~$ ssh bandit11@bandit.labs.overthewire.org -p 2220
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

`cat data.txt`

|

Displays the encoded Base64 content.

|
|

`base64 -d data.txt`

|

Decodes the Base64 data into readable text.

|
|

`exit`

|

Closes the current SSH session.

|
|

`ssh bandit11@bandit.labs.overthewire.org -p 2220`

|

Connects to Bandit Level 11 using SSH.

|

## Why Use `base64 -d`?

<table class="_6IUVGW_Table" data-d-column-sizing="auto" data-d-dividers="" style="table-layout: auto;"><tbody><tr data-d-component="table-row"><td data-d-component="table-cell" data-d-has-width="" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text"><span class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-default-strong="" data-d-inline="">Command</span></p></td><td data-d-component="table-cell" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text"><span class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-default-strong="" data-d-inline="">Result</span></p></td></tr><tr data-d-component="table-row"><td data-d-component="table-cell" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-whitespace="preserve">cat data.txt</p></td><td data-d-component="table-cell" data-d-valign="start">Displays the encoded Base64 text.</td></tr><tr data-d-component="table-row"><td data-d-component="table-cell" data-d-valign="start"><p class="w6asjq_TextBase _85PZeG_Text" data-d-component="text" data-d-whitespace="preserve">base64 -d data.txt</p></td><td data-d-component="table-cell" data-d-valign="start">Decodes the Base64 text into its original readable form.</td></tr></tbody></table>

The `-d` option stands for decode.

## Terminal Output (Example)

Bash

```
bandit10@bandit:~$ pwd
/home/bandit10

bandit10@bandit:~$ ls
data.txt

bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTU2cyUlducE5WajNxUnI=

bandit10@bandit:~$ base64 -d data.txt
The password is <next level password>

bandit10@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

user@ubuntu:~$ ssh bandit11@bandit.labs.overthewire.org -p 2220
bandit11@bandit.labs.overthewire.org's password:
bandit11@bandit:~$
```

## Key Takeaways

* Learned what Base64 encoding is.

* Used `base64 -d` to decode encoded text.

* Retrieved the password from the decoded output.

* Logged into bandit11 using SSH from the Linux terminal.

## Result

Successfully decoded the Base64 data in `data.txt`, obtained the Bandit Level 11 password, and logged into the bandit11 account using the Linux terminal.

## Screenshot (GitHub Markdown Syntax)

Add your terminal screenshot at the end of the README using this syntax:

Markdown

```
![Bandit Level 10 to Level 11 Output](PASTE_YOUR_GITHUB_IMAGE_LINK_HERE)
```

Example

Markdown

```
![Bandit Level 10 to Level 11 Output](https://github.com/user-attachments/assets/your-image-id)
```
<img width="726" height="164" alt="image" src="https://github.com/user-attachments/assets/40e7dfa4-2afc-487c-8af7-4c143ac54a73" />
