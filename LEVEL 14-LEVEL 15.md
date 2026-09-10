# Bandit Level 14 → Level 15

## Level Goal

The password for **Bandit Level 15** can be retrieved by **submitting the current Bandit Level 14 password** to **port `30000` on `localhost`**.

The challenge is to communicate with a TCP service running on **localhost** using the **`nc` (Netcat)** command.

---

## Concept Learned

This level introduces **Netcat (`nc`)**, a networking utility used to connect to TCP or UDP ports.

* **`nc`** opens a TCP connection to a specified host and port.
* You send input through the connection and receive the server's response.
* Unlike SSH, this is a simple network service listening on **port 30000**.

### Commands Used

| Command | Purpose                                       |
| ------- | --------------------------------------------- |
| `cat`   | Reads the current level password.             |
| `nc`    | Connects to a TCP service on a specific port. |
| `exit`  | Closes the session.                           |

---

## Walkthrough (Windows Command Prompt)

### Step 1 – Log into Bandit14

From your Windows Command Prompt:

```cmd
ssh bandit14@bandit.labs.overthewire.org -p 2220
```

Enter the **Bandit Level 14 password**:

```text
<next level password>
```

**Successful Login Prompt**

```text
bandit14@bandit:~$
```

---

### Step 2 – Verify the Current Password (Optional)

The current password is stored in `/etc/bandit_pass/bandit14`.

```bash
cat /etc/bandit_pass/bandit14
```

**Output**

```text
<next level password>
```

---

### Step 3 – Connect to Port 30000 Using Netcat

Run the following command:

```bash
nc localhost 30000
```

**Explanation**

| Part        | Meaning                                |
| ----------- | -------------------------------------- |
| `nc`        | Starts a Netcat connection.            |
| `localhost` | Connects to the current Bandit server. |
| `30000`     | Connects to TCP port **30000**.        |

The terminal waits for your input.

---

### Step 4 – Submit the Password

Paste the **Bandit Level 14 password** and press **Enter**.

```text
<next level password>
```

**Output**

```text
Correct!
<next level password>
```

The second line is the password for **Bandit Level 15**.

---

### Step 5 – Password for Bandit Level 15

```text
<next level password>
```

This is the password for **bandit15**.

---

### Step 6 – Exit the Netcat Connection

After receiving the password, press:

```text
Ctrl + C
```

to close the Netcat connection.

---

### Step 7 – Log into Bandit15

```cmd
ssh bandit15@bandit.labs.overthewire.org -p 2220
```

Enter the password obtained from Netcat:

```text
<next level password>
```

**Successful Login Prompt**

```text
bandit15@bandit:~$
```

---

## Complete Command Sequence

```bash
cat /etc/bandit_pass/bandit14
nc localhost 30000
# Paste the password and press Enter
# Press Ctrl + C after receiving the response
exit
```

Then from Windows Command Prompt:

```cmd
ssh bandit15@bandit.labs.overthewire.org -p 2220
```

---

## Explanation

* `cat` reads the current level password.
* `nc localhost 30000` opens a TCP connection to the service.
* Sending the password authenticates you to the service.
* The service replies with the password for **Bandit Level 15**.

---

## Why Use `nc` Instead of `ssh`?

| Command              | Purpose                                              |
| -------------------- | ---------------------------------------------------- |
| `ssh`                | Logs into a remote machine using SSH.                |
| `nc localhost 30000` | Connects to a TCP service running on port **30000**. |

`nc` is a general networking tool and is commonly used for testing ports and interacting with network services.

---

## Key Takeaways

* Learned how to use **Netcat (`nc`)** to connect to a TCP port.
* Sent input to a network service and received its response.
* Retrieved the password for **Bandit Level 15**.
* Logged into **bandit15** using SSH.

---

## Result

Successfully connected to **localhost:30000** using Netcat, submitted the **Bandit Level 14** password, obtained the **Bandit Level 15** password **`<next level password>`**, and logged into the **bandit15** account.
<img width="371" height="126" alt="image" src="https://github.com/user-attachments/assets/35fead64-8951-40bb-8443-4d14f258ac2a" />
