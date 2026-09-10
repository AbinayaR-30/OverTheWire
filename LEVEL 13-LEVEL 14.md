# Bandit Level 13 → Level 14

## Level Goal

The password for **Bandit Level 14** is stored in **`/etc/bandit_pass/bandit14`**, but it can only be read by the **bandit14** user.

Unlike previous levels, **Bandit Level 13 does not give you a password**. Instead, it provides a **private SSH key (`sshkey.private`)** that must be used to log in as `bandit14`. <Cite ref={["turn0search0","turn0search3"]}/>

---

## Concept Learned

This level introduces **SSH Key Authentication**.

* A **private SSH key** can authenticate a user without entering a password.
* The **`-i`** option in the `ssh` command specifies which private key to use.
* The key provided in `sshkey.private` belongs to **bandit14**, so it allows access to that account. <Cite ref={["turn0search0","turn0search3"]}/>

### Commands Used

| Command  | Purpose                                             |
| -------- | --------------------------------------------------- |
| `ls`     | Lists files in the current directory.               |
| `cat`    | Displays the private key (optional).                |
| `ssh -i` | Uses a private SSH key to log into another account. |
| `exit`   | Exits the SSH session.                              |

---

## Walkthrough (Windows Command Prompt)

### Step 1 – Verify the Private Key Exists

After logging into **bandit13**, list the files.

```bash
ls
```

**Output**

```text
sshkey.private
```

The home directory contains the private SSH key needed for the next login.

---

### Step 2 – (Optional) View the Private Key

```bash
cat sshkey.private
```

**Output (Beginning of File)**

```text
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
```

This confirms that `sshkey.private` is an RSA private key.

---

### Step 3 – Log in as `bandit14` Using the Private Key

Run the SSH command with the **`-i`** option.

```bash
ssh -i sshkey.private -p 2220 bandit14@localhost
```

### Explanation of the Command

| Part                 | Meaning                                               |
| -------------------- | ----------------------------------------------------- |
| `ssh`                | Starts an SSH connection.                             |
| `-i sshkey.private`  | Uses `sshkey.private` as the authentication key.      |
| `-p 2220`            | Connects using Bandit's SSH port.                     |
| `bandit14@localhost` | Logs into the `bandit14` account on the same machine. |

> **Note:** If asked to trust the host fingerprint, type `yes` and press **Enter**.

**Successful Login Prompt**

```text
bandit14@bandit:~$
```

---

### Step 4 – Read the Password File

Now that you are logged in as **bandit14**, read the password file.

```bash
cat /etc/bandit_pass/bandit14
```

**Output**

```text
<next level password>
```

This is the password for **Bandit Level 14**. <Cite ref={["turn0search3","turn0search8"]}/>

---

### Step 5 – Exit the Session

```bash
exit
```

You will return to the `bandit13` session.

Exit once more if you want to return to your local Command Prompt.

```bash
exit
```

---

### Step 6 – Log into Bandit Level 14 from Windows

```cmd
ssh bandit14@bandit.labs.overthewire.org -p 2220
```

When prompted, enter the password:

```text
<next level password>
```

**Successful Login Prompt**

```text
bandit14@bandit:~$
```

---

## Complete Command Sequence

```bash
ls
ssh -i sshkey.private -p 2220 bandit14@localhost
cat /etc/bandit_pass/bandit14
exit
exit
```

Then from Windows Command Prompt:

```cmd
ssh bandit14@bandit.labs.overthewire.org -p 2220
```

---

## Explanation

* `ls` confirms the presence of `sshkey.private`.
* `ssh -i` authenticates using the private key instead of a password.
* `cat /etc/bandit_pass/bandit14` reads the password that only `bandit14` can access.
* `exit` closes the SSH sessions and returns to your local terminal.

---

## Common Error and Fix (2026 Update)

If you run:

```bash
ssh -i sshkey.private bandit14@localhost
```

and get:

```text
Permission denied (publickey).
!!! You are trying to log into this SSH server on port 22...
```

**Reason:** SSH defaults to **port 22**.

**Correct command:**

```bash
ssh -i sshkey.private -p 2220 bandit14@localhost
```

The Bandit server runs on **port 2220**, not port 22. <Cite ref={["turn0reddit10","turn0reddit15"]}/>

---

## Key Takeaways

* Learned how **SSH key authentication** works.
* Used the **`-i`** option to authenticate with a private key.
* Logged into another Linux user without using a password.
* Accessed a protected file in `/etc/bandit_pass`.
* Retrieved the password for **Bandit Level 14**.

---

## Result

Successfully used `sshkey.private` to log into **bandit14**, read the password from `/etc/bandit_pass/bandit14`, obtained the **Bandit Level 14** password **`<next level password>`**, and logged into the **bandit14** account.
<img width="984" height="736" alt="image" src="https://github.com/user-attachments/assets/15f0c513-c7f8-49d7-af02-34c5b09d3fed" />
