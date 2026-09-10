# WHAT IS SSH?

SSH (Secure Shell) is a cryptographic network protocol used to securely connect to remote systems over unsecured networks.

It provides encrypted communication, authentication, and data integrity, making it the standard protocol for remote server administration, file transfers, and secure tunneling.

SSH operates over TCP port 22 by default, but servers can use custom ports (such as Bandit's 2220). It replaces older insecure protocols like Telnet and rsh by encrypting all transmitted data, preventing eavesdropping and man-in-the-middle attacks.

# Bandit Level 0 – Login using SSH (Linux Terminal)

## Level Goal

The objective of Level 0 is to connect to the OverTheWire Bandit server using SSH (Secure Shell). This is the starting point of the Bandit wargame.

* Host: `bandit.labs.overthewire.org`

* Port: `2220`

* Username: `bandit0`

* Password: `bandit0`

After logging in successfully, you will be connected to the Linux server and can begin solving the next level.

## Concept Learned

### What is SSH?

SSH (Secure Shell) is a secure network protocol used to remotely access another computer over an encrypted connection. It allows you to execute Linux commands on a remote machine from your own Linux terminal.

### SSH Syntax

Bash

```
ssh username@hostname -p port_number
```

Where:

* `ssh` → Starts an SSH connection.

* `username@hostname` → User account and server address.

* `-p` → Specifies a custom port number.

## Walkthrough (Linux Terminal)

### Step 1 – Open the Linux Terminal

Open your Linux terminal using Ctrl + Alt + T (or open the Terminal application from the applications menu).

A terminal window will open with a prompt similar to:

Bash

```
user@ubuntu:~$
```

### Step 2 – Connect to the Bandit Server

Type the following command:

Bash

```
user@ubuntu:~$ ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Press Enter.

### Step 3 – Accept the Server Fingerprint

The first time you connect, Linux will display a message similar to:

```
The authenticity of host 'bandit.labs.overthewire.org (176.9.9.172)' can't be established.
ED25519 key fingerprint is SHA256:...
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Type:

Bash

```
yes
```

Press Enter.

This stores the server's fingerprint in the known_hosts file so future connections can be verified automatically.

### Step 4 – Enter the Password

You will see:

```
bandit0@bandit.labs.overthewire.org's password:
```

Type:

Bash

```
bandit0
```

> Note: Nothing appears on the screen while typing the password—not even dots or asterisks. This is normal behavior in Linux terminals.

Press Enter.

### Step 5 – Successful Login

If the login is successful, you will see the Bandit welcome message and a Linux prompt similar to:

Bash

```
bandit0@bandit:~$
```

You are now logged into the remote Linux machine.

## Verify Your Login

Run a simple command:

Bash

```
bandit0@bandit:~$ pwd
```

Output

```
/home/bandit0
```

This confirms that you are inside the bandit0 home directory.

You can also list the files in the current directory:

Bash

```
bandit0@bandit:~$ ls
```

Output

```
readme
```

This file contains the password for Bandit Level 1, which will be solved in the next walkthrough.

## Commands Used in This Level

|
Linux Command

|

Purpose

|
| --- | --- |
|

ssh [bandit0@bandit.labs.overthewire.org](mailto:bandit0@bandit.labs.overthewire.org) -p 2220

| Connects to the Bandit server using SSH. |
|

pwd

| Displays the current working directory. |
|

ls

| Lists files in the current directory. |

## Key Takeaways

* Learned how to use SSH to connect to a remote Linux server.

* Connected to the Bandit server using a custom SSH port (2220).

* Accepted the server fingerprint on the first connection.

* Logged into the Bandit Linux environment successfully.

* Verified the current directory using `pwd`.

* Listed files in the home directory using `ls`.

## Result

Successfully logged into Bandit Level 0 using the Linux Terminal and reached the Linux home directory `/home/bandit0`, ready to continue to Bandit Level 1.
