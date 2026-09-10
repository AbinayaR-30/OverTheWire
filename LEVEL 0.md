WHAT IS SSH?
SSH (Secure Shell) is a cryptographic network protocol used to securely connect to remote systems over unsecured networks.
It provides encrypted communication, authentication, and data integrity, making it the standard for remote server administration, file transfers, and secure tunneling.
It operates over TCP port 22 and replaces older insecure protocols like Telnet and rsh by encrypting all transmitted data, preventing eavesdropping and on-path attacks.

# Bandit Level 0 – Login using SSH

## Level Goal

The objective of **Level 0** is to connect to the OverTheWire Bandit server using **SSH (Secure Shell)**. This is the starting point of the Bandit wargame.

* **Host:** `bandit.labs.overthewire.org`
* **Port:** `2220`
* **Username:** `bandit0`
* **Password:** `bandit0`

After logging in successfully, you will be connected to the Linux server and can begin solving the next level.

---

## Concept Learned

### What is SSH?

**SSH (Secure Shell)** is a secure network protocol used to remotely access another computer over an encrypted connection. It allows you to execute Linux commands on a remote machine from your own computer.

**SSH Syntax**

```bash
ssh username@hostname -p port_number
```

Where:

* `ssh` → Starts an SSH connection.
* `username@hostname` → User account and server address.
* `-p` → Specifies a custom port number.

---

## Walkthrough (Windows Command Prompt)

### Step 1 – Open Command Prompt

* Press **Windows + R**.
* Type `cmd`.
* Press **Enter**.

A Command Prompt window will open.

---

### Step 2 – Connect to the Bandit Server

Type the following command:

```cmd
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Press **Enter**.

---

### Step 3 – Accept the Server Fingerprint

The first time you connect, Windows will display a message similar to:

```text
The authenticity of host 'bandit.labs.overthewire.org' can't be established.
ED25519 key fingerprint is SHA256:...
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Type:

```text
yes
```

Press **Enter**.

This stores the server's fingerprint on your computer.

---

### Step 4 – Enter the Password

You will see:

```text
bandit0@bandit.labs.overthewire.org's password:
```

Type:

```text
bandit0
```

> **Note:** Nothing appears on the screen while typing the password. This is normal behavior in Linux and SSH terminals.

Press **Enter**.

---

### Step 5 – Successful Login

If the login is successful, you will see the Bandit welcome message and a prompt similar to:

```text
bandit0@bandit:~$
```

You are now logged into the remote Linux machine.

---

## Verify Your Login

Run a simple command:

```bash
pwd
```

**Output**

```text
/home/bandit0
```

This confirms that you are inside the **bandit0** home directory.

You can also list the files in the current directory:

```bash
ls
```

Output:

```text
readme
```

This file contains the password for **Level 1**, which will be solved in the next walkthrough.
<img width="1146" height="280" alt="image" src="https://github.com/user-attachments/assets/d3f6701c-615a-43c6-b35b-55fd363e904c" />

---

## Commands Used in This Level

| Command                                           | Purpose                                  |
| ------------------------------------------------- | ---------------------------------------- |
| `ssh bandit0@bandit.labs.overthewire.org -p 2220` | Connects to the Bandit server using SSH. |
| `pwd`                                             | Displays the current working directory.  |
| `ls`                                              | Lists files in the current directory.    |

---

## Key Takeaways

* Learned how to use **SSH** to connect to a remote Linux server.
* Connected using a **custom port (2220)**.
* Accepted the server fingerprint for the first connection.
* Logged into the Bandit Linux environment successfully.
* Verified the current directory using `pwd` and listed files using `ls`.

---

## Result

Successfully logged into **Bandit Level 0** using Windows Command Prompt and reached the Linux home directory `/home/bandit0`, ready to continue to **Level 1**.

