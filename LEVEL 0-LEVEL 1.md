# Bandit Level 0 → Level 1

## Level Goal
The password for **Bandit Level 1** is stored in a file named **`readme`** located in the home directory of `bandit0`.

The objective is to:

1. Locate the `readme` file.
2. Display its contents.
3. Use the retrieved password to log in as **bandit1**.

---

## Concept Learned

This level introduces basic Linux file operations.

### Commands Used

| Command | Purpose                                                 |
| ------- | ------------------------------------------------------- |
| `ls`    | Lists files and directories in the current directory.   |
| `cat`   | Displays the contents of a file.                        |
| `pwd`   | Shows the current working directory.                    |
| `ssh`   | Logs into the next Bandit level using the new password. |

---

## Walkthrough (Windows Command Prompt)

### Step 1 – Verify Your Current Directory

After logging into **bandit0**, check where you are.

```bash
pwd
```

**Output**

```text
/home/bandit0
```

This is the home directory for `bandit0`.

---

### Step 2 – List Files in the Home Directory

Use the `ls` command.

```bash
ls
```

**Output**

```text
readme
```

The directory contains a file named `readme`.

---

### Step 3 – Read the Password from the File

Use `cat` to display the contents.

```bash
cat readme
```

**Output**

```text
<Bandit Level 1 Password>
```

This string is the password for **bandit1**.

> Save this password in a local notes file because Bandit does not store previous passwords for you.

---

### Step 4 – Exit the Current Session

Leave the `bandit0` session.

```bash
exit
```

---

### Step 5 – Log into Bandit Level 1

Use SSH with the next username.

```cmd
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

When prompted, paste the password obtained from the `readme` file.

```text
bandit1@bandit.labs.overthewire.org's password:
```

After entering the correct password, you will see the Bandit Level 1 shell prompt.

```text
bandit1@bandit:~$
```

---

## Complete Command Sequence

```bash
pwd
ls
cat readme
exit
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

---

## Explanation

* `pwd` confirms the current location.
* `ls` lists the available files.
* `cat readme` prints the contents of the `readme` file.
* `exit` closes the current SSH session.
* `ssh` establishes a new connection as `bandit1`.

---

## Key Takeaways

* Learned how to list files using `ls`.
* Learned how to read file contents using `cat`.
* Retrieved the password stored inside a file.
* Logged into the next Bandit level using SSH.

---

## Result

Successfully obtained the **Bandit Level 1** password from the `readme` file and logged into the **bandit1** account.
<img width="972" height="252" alt="image" src="https://github.com/user-attachments/assets/4d4039a8-2f6c-4086-8188-8fefd1a8c81d" />

