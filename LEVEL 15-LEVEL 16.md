# Bandit Level 15 → Level 16 (Linux Terminal)

## Level Goal

The password for Bandit Level 16 can be retrieved by submitting the Bandit Level 15 password to port `30001` on `localhost` using SSL/TLS encryption.

Unlike Level 14, a normal `nc` connection will not work because the service expects an encrypted SSL/TLS connection.

## Concept Learned

This level introduces OpenSSL's `s_client` command.

* SSL/TLS encrypts communication between a client and a server.

* `openssl s_client` creates a secure TLS connection to a server.

* After the secure connection is established, you send the password and receive the next level's password.

### Commands Used

|
Linux Command

|

Purpose

|
| --- | --- |
|

`cat`

|

Displays the current level password.

|
|

`openssl s_client`

|

Creates an SSL/TLS encrypted connection.

|
|

`Ctrl + C`

|

Closes the SSL/TLS connection.

|
|

`exit`

|

Closes the SSH session.

|
|

`ssh`

|

Logs into the next Bandit level.

|

## Walkthrough (Linux Terminal)

### Step 1 – Log into Bandit Level 15

From your Linux terminal, connect to bandit15.

Bash

```
user@ubuntu:~$ ssh bandit15@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit15@bandit.labs.overthewire.org's password:
```

Enter the Bandit Level 15 password.

Successful Login Prompt

Bash

```
bandit15@bandit:~$
```

### Step 2 – Verify the Current Password (Optional)

Display the current level password.

Bash

```
bandit15@bandit:~$ cat /etc/bandit_pass/bandit15
```

Output

```
<next level password>
```

This is the password that must be submitted to the SSL/TLS service.

### Step 3 – Connect to Port 30001 Using SSL/TLS

Run the following command:

Bash

```
bandit15@bandit:~$ openssl s_client -connect localhost:30001 -quiet
```

### Explanation of the Command

|
Command Part

|

Meaning

|
| --- | --- |
|

`openssl`

|

OpenSSL command-line tool.

|
|

`s_client`

|

Starts an SSL/TLS client connection.

|
|

`-connect localhost:30001`

|

Connects securely to port 30001.

|
|

`-quiet`

|

Hides certificate information and shows only the interaction.

|

After running the command, the terminal waits for your input.

### Step 4 – Submit the Password

Paste the Bandit Level 15 password and press Enter.

```
<next level password>
```

Output

```
Correct!
<next level password>
```

* `Correct!` confirms the password is valid.

* The second line is the password for Bandit Level 16.

### Step 5 – Password for Bandit Level 16

```
<next level password>
```

Copy this password carefully. It will be used to log into bandit16.

### Step 6 – Exit the SSL/TLS Connection

After receiving the password, close the OpenSSL connection by pressing:

```
Ctrl + C
```

This returns you to the Bandit terminal prompt.

Bash

```
bandit15@bandit:~$
```

### Step 7 – Exit the SSH Session

Exit the current Bandit session.

Bash

```
bandit15@bandit:~$ exit
```

Output

```
logout
Connection to bandit.labs.overthewire.org closed.
```

### Step 8 – Log into Bandit Level 16

From your local Linux terminal, connect to the next level.

Bash

```
user@ubuntu:~$ ssh bandit16@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit16@bandit.labs.overthewire.org's password:
```

Enter the password obtained from the SSL/TLS service.

Successful Login Prompt

Bash

```
bandit16@bandit:~$
```

You are now logged into Bandit Level 16.

## Complete Command Sequence

Bash

```
bandit15@bandit:~$ cat /etc/bandit_pass/bandit15

bandit15@bandit:~$ openssl s_client -connect localhost:30001 -quiet
# Paste the password and press Enter
# Press Ctrl + C after receiving the response

bandit15@bandit:~$ exit

user@ubuntu:~$ ssh bandit16@bandit.labs.overthewire.org -p 2220
```

## Explanation

|
Command

|

Explanation

|
| --- | --- |
|

`cat /etc/bandit_pass/bandit15`

|

Reads the current level password.

|
|

`openssl s_client -connect localhost:30001 -quiet`

|

Creates a secure SSL/TLS connection to the service.

|
|

`Ctrl + C`

|

Terminates the SSL/TLS connection after receiving the response.

|
|

`exit`

|

Closes the current SSH session.

|
|

`ssh bandit16@bandit.labs.overthewire.org -p 2220`

|

Connects to Bandit Level 16 using SSH.

|

## Why `nc` Does Not Work Here

|
Command

|

Result

|
| --- | --- |
|

`nc localhost 30001`

|

Opens a TCP connection, but communication fails because the service requires TLS encryption.

|
|

`openssl s_client -connect localhost:30001 -quiet`

|

Establishes a secure encrypted connection and returns the password.

|

The service on port 30001 accepts only SSL/TLS-encrypted connections.

## Common Output Messages

When connecting with OpenSSL, you may see messages like:

```
DONE
RENEGOTIATING
KEYUPDATE
```

These are part of the TLS protocol and can be ignored. The important step is to paste the password after the secure connection is established.

## Terminal Output (Example)

Bash

```
user@ubuntu:~$ ssh bandit15@bandit.labs.overthewire.org -p 2220
bandit15@bandit.labs.overthewire.org's password:
bandit15@bandit:~$

bandit15@bandit:~$ cat /etc/bandit_pass/bandit15
<current level password>

bandit15@bandit:~$ openssl s_client -connect localhost:30001 -quiet
<current level password>
Correct!
<next level password>

^C

bandit15@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

user@ubuntu:~$ ssh bandit16@bandit.labs.overthewire.org -p 2220
bandit16@bandit.labs.overthewire.org's password:
bandit16@bandit:~$
```

## Key Takeaways

* Learned how to use `openssl s_client` to create an SSL/TLS connection.

* Understood the difference between a normal TCP connection (`nc`) and an encrypted TLS connection.

* Submitted the current Bandit password over an encrypted channel.

* Retrieved the password for Bandit Level 16.

* Logged into bandit16 using SSH from the Linux terminal.

## Result

Successfully connected to `localhost:30001` using SSL/TLS, submitted the Bandit Level 15 password, obtained the Bandit Level 16 password, and logged into the bandit16 account using the Linux terminal.

<img width="379" height="132" alt="image" src="https://github.com/user-attachments/assets/4e34a786-1620-41d0-b5bf-e94269fa364b" />
