# Bandit Level 14 → Level 15 (Linux Terminal)

## Level Goal

The password for Bandit Level 15 can be retrieved by submitting the current Bandit Level 14 password to port `30000` on `localhost`.

The challenge is to communicate with a TCP service running on localhost using the `nc` (Netcat) command.

## Concept Learned

This level introduces Netcat (`nc`), a networking utility used to connect to TCP or UDP ports.

* `nc` opens a TCP connection to a specified host and port.

* You send input through the connection and receive the server's response.

* Unlike SSH, this is a simple network service listening on port 30000.

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

Reads the current level password.

|
|

`nc`

|

Connects to a TCP service on a specific port.

|
|

`Ctrl + C`

|

Closes the Netcat connection.

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

### Step 1 – Log into Bandit Level 14

From your Linux terminal, connect to bandit14.

Bash

```
user@ubuntu:~$ ssh bandit14@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit14@bandit.labs.overthewire.org's password:
```

Enter the Bandit Level 14 password.

Successful Login Prompt

Bash

```
bandit14@bandit:~$
```

### Step 2 – Verify the Current Password (Optional)

The current password is stored in `/etc/bandit_pass/bandit14`.

Bash

```
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
```

Output

```
<next level password>
```

This is the password that must be sent to the service running on port 30000.

### Step 3 – Connect to Port 30000 Using Netcat

Run the following command:

Bash

```
bandit14@bandit:~$ nc localhost 30000
```

### Explanation of the Command

|
Command Part

|

Meaning

|
| --- | --- |
|

`nc`

|

Starts a Netcat connection.

|
|

`localhost`

|

Connects to the current Bandit server.

|
|

`30000`

|

Connects to TCP port 30000.

|

After running the command, the terminal waits for your input.

### Step 4 – Submit the Password

Paste the Bandit Level 14 password and press Enter.

```
<next level password>
```

Output

```
Correct!
<next level password>
```

* `Correct!` confirms the password is valid.

* The second line is the password for Bandit Level 15.

### Step 5 – Password for Bandit Level 15

```
<next level password>
```

Copy this password carefully. It will be used to log into bandit15.

### Step 6 – Exit the Netcat Connection

After receiving the password, close the Netcat session by pressing:

```
Ctrl + C
```

This returns you to the Bandit terminal prompt.

Bash

```
bandit14@bandit:~$
```

### Step 7 – Exit the SSH Session

Exit the current Bandit session.

Bash

```
bandit14@bandit:~$ exit
```

Output

```
logout
Connection to bandit.labs.overthewire.org closed.
```

### Step 8 – Log into Bandit Level 15

From your local Linux terminal, connect to the next level.

Bash

```
user@ubuntu:~$ ssh bandit15@bandit.labs.overthewire.org -p 2220
```

Password Prompt

```
bandit15@bandit.labs.overthewire.org's password:
```

Enter the password obtained from Netcat.

Successful Login Prompt

Bash

```
bandit15@bandit:~$
```

You are now logged into Bandit Level 15.

## Complete Command Sequence

Bash

```
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
bandit14@bandit:~$ nc localhost 30000
# Paste the password and press Enter
# Press Ctrl + C after receiving the response
bandit14@bandit:~$ exit

user@ubuntu:~$ ssh bandit15@bandit.labs.overthewire.org -p 2220
```

## Explanation

|
Command

|

Explanation

|
| --- | --- |
|

`cat /etc/bandit_pass/bandit14`

|

Reads the current level password.

|
|

`nc localhost 30000`

|

Opens a TCP connection to the service running on port 30000.

|
|

`Ctrl + C`

|

Terminates the Netcat connection after receiving the response.

|
|

`exit`

|

Closes the current SSH session.

|
|

`ssh bandit15@bandit.labs.overthewire.org -p 2220`

|

Connects to Bandit Level 15 using SSH.

|

## Why Use `nc` Instead of `ssh`?

|
Command

|

Purpose

|
| --- | --- |
|

`ssh`

|

Logs into a remote machine using the SSH protocol.

|
|

`nc localhost 30000`

|

Connects directly to a TCP service running on port 30000.

|

Netcat is a general-purpose networking tool commonly used to test ports, send data, and interact with network services.

## Terminal Output (Example)

Bash

```
user@ubuntu:~$ ssh bandit14@bandit.labs.overthewire.org -p 2220
bandit14@bandit.labs.overthewire.org's password:
bandit14@bandit:~$

bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
<current level password>

bandit14@bandit:~$ nc localhost 30000
<current level password>
Correct!
<next level password>

^C

bandit14@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

user@ubuntu:~$ ssh bandit15@bandit.labs.overthewire.org -p 2220
bandit15@bandit.labs.overthewire.org's password:
bandit15@bandit:~$
```

## Key Takeaways

* Learned how to use Netcat (`nc`) to connect to a TCP port.

* Connected to a service running on `localhost:30000`.

* Sent the current Bandit password through the TCP connection.

* Received the password for Bandit Level 15 from the service.

* Logged into bandit15 using SSH from the Linux terminal.

## Result

Successfully connected to `localhost:30000` using Netcat, submitted the Bandit Level 14 password, obtained the Bandit Level 15 password, and logged into the bandit15 account using the Linux terminal.
<img width="371" height="126" alt="image" src="https://github.com/user-attachments/assets/35fead64-8951-40bb-8443-4d14f258ac2a" />
