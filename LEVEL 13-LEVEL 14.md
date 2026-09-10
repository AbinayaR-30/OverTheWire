# Bandit Level 13 → Level 14 (Linux Terminal)

## Level Goal

The password for Bandit Level 14 is stored in `/etc/bandit_pass/bandit14`, but it can only be read by the bandit14 user.

Unlike previous levels, Bandit Level 13 does not give you a password. Instead, it provides a private SSH key (`sshkey.private`) that must be used to log in as `bandit14`.

## Concept Learned

This level introduces SSH Key Authentication.

* A private SSH key can authenticate a user without entering a password.

* The `-i` option in the `ssh` command specifies which private key to use.

* The key provided in `sshkey.private` belongs to bandit14, so it allows access to that account.

### Commands Used

|
Linux Command

|

Purpose

|
| --- | --- |
|

`ls`

|

Lists files in the current directory.

|
|

`cat sshkey.private`

|

Displays the private key (optional).

|
|

`ssh -i`

|

Uses a private SSH key to log into another account.

|
|

`exit`

|

Exits the SSH session.

|

## Walkthrough (Linux Terminal)

### Step 1 – Verify the Private Key Exists

After logging into bandit13, list the files in the home directory.

Bash

```
bandit13@bandit:~$ ls
```

Output

```
sshkey.private
```

The home directory contains the private SSH key needed for the next login.

### Step 2 – (Optional) View the Private Key

You can verify that the file is an RSA private key.

Bash

```
bandit13@bandit:~$ cat sshkey.private
```

Output (Beginning of File)

```
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
```

This confirms that `sshkey.private` is an RSA private key.

> Note: You do not need to copy or edit this key. It is used directly by the `ssh` command.

### Step 3 – Log in as `bandit14` Using the Private Key

Run the SSH command with the `-i` option.

Bash

```
bandit13@bandit:~$ ssh -i sshkey.private -p 2220 bandit14@localhost
```

### Explanation of the Command

|
Command Part

|

Meaning

|
| --- | --- |
|

`ssh`

|

Starts an SSH connection.

|
|

`-i sshkey.private`

|

Uses `sshkey.private` as the authentication key.

|
|

`-p 2220`

|

Connects using Bandit's SSH port.

|
|

`bandit14@localhost`

|

Logs into the `bandit14` account on the same Bandit server.

|

> Note: If SSH asks whether you trust the host fingerprint, type `yes` and press Enter.

Successful Login Prompt

Bash

```
bandit14@bandit:~$
```

You are now logged into the bandit14 account.

### Step 4 – Read the Password File

Now that you are logged in as bandit14, read the protected password file.

Bash

```
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
```

Output

```
<next level password>
```

This is the password for Bandit Level 14.

### Step 5 – Exit the SSH Sessions

Exit from the `bandit14` session.

Bash

```
bandit14@bandit:~$ exit
```

Output

```
logout
Connection to localhost closed.
```

You will return to the `bandit13` session.

Exit once more to return to your local Linux terminal.

Bash

```
bandit13@bandit:~$ exit
```

Output

```
logout
Connection to bandit.labs.overthewire.org closed.
```

### Step 6 – Log into Bandit Level 14

From your local Linux terminal, log into bandit14 using the password you just obtained.

Bash

```
user@ubuntu:~$ ssh bandit14@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit14@bandit.labs.overthewire.org's password:
```

Enter the password obtained from `/etc/bandit_pass/bandit14`.

Successful Login Prompt

Bash

```
bandit14@bandit:~$
```

You are now logged into Bandit Level 14.

## Complete Command Sequence

Bash

```
bandit13@bandit:~$ ls
bandit13@bandit:~$ ssh -i sshkey.private -p 2220 bandit14@localhost
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
bandit14@bandit:~$ exit
bandit13@bandit:~$ exit

user@ubuntu:~$ ssh bandit14@bandit.labs.overthewire.org -p 2220
```

## Explanation

|
Command

|

Explanation

|
| --- | --- |
|

`ls`

|

Confirms the presence of `sshkey.private`.

|
|

`cat sshkey.private`

|

Displays the private key (optional verification).

|
|

`ssh -i sshkey.private -p 2220 bandit14@localhost`

|

Authenticates as `bandit14` using the private SSH key.

|
|

`cat /etc/bandit_pass/bandit14`

|

Reads the password file that only `bandit14` can access.

|
|

`exit`

|

Closes the SSH sessions and returns to the previous terminal.

|
|

`ssh bandit14@bandit.labs.overthewire.org -p 2220`

|

Logs into Bandit Level 14 using the recovered password.

|

## Common Error and Fix

### Error

If you run:

Bash

```
bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost
```

You may get:

```
Permission denied (publickey).
!!! You are trying to log into this SSH server on port 22...
```

### Reason

SSH connects to port 22 by default, but the Bandit server uses port 2220.

### Correct Command

Bash

```
bandit13@bandit:~$ ssh -i sshkey.private -p 2220 bandit14@localhost
```

Always include `-p 2220` when connecting to Bandit.

## Terminal Output (Example)

Bash

```
bandit13@bandit:~$ ls
sshkey.private

bandit13@bandit:~$ ssh -i sshkey.private -p 2220 bandit14@localhost
bandit14@bandit:~$

bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
<next level password>

bandit14@bandit:~$ exit
logout
Connection to localhost closed.

bandit13@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

user@ubuntu:~$ ssh bandit14@bandit.labs.overthewire.org -p 2220
bandit14@bandit.labs.overthewire.org's password:
bandit14@bandit:~$
```

## Key Takeaways

* Learned how SSH Key Authentication works.

* Used the `-i` option to authenticate with a private SSH key.

* Logged into another Linux user without entering a password.

* Accessed a protected file in `/etc/bandit_pass`.

* Retrieved the password for Bandit Level 14.

* Understood why port 2220 must be specified when connecting to Bandit.

## Result

Successfully used `sshkey.private` to log into bandit14, read the password from `/etc/bandit_pass/bandit14`, obtained the Bandit Level 14 password, and logged into the bandit14 account using the Linux terminal.

<img width="984" height="736" alt="image" src="https://github.com/user-attachments/assets/15f0c513-c7f8-49d7-af02-34c5b09d3fed" />
