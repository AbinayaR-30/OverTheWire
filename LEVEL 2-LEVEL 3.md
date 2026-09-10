# Bandit Level 2 → Level 3

## Level Goal

The password for **Bandit Level 3** is stored in a file named **`--spaces in this filename--`** located in the home directory of `bandit2`.

The challenge is to learn how to access filenames that contain **spaces**.

---

## Concept Learned

In Linux, **spaces separate command arguments**. If a filename contains spaces, the shell treats each word as a different argument unless the filename is **quoted** or the spaces are **escaped**.

### Commands Used

| Command | Purpose                               |
| ------- | ------------------------------------- |
| `pwd`   | Shows the current working directory.  |
| `ls`    | Lists files in the current directory. |
| `cat`   | Displays the contents of the file.    |
| `ssh`   | Logs into the next Bandit level.      |

---

## Walkthrough (Windows Command Prompt)

### Step 1 – Verify Your Current Directory

After logging into **bandit2**, check your location.

```bash
pwd
```

**Output**

```text
/home/bandit2
```

---

### Step 2 – List Files

Display the files in the home directory.

```bash
ls
```

**Output**

```text
--spaces in this filename--
```

The directory contains a file whose name includes spaces.

---

### Step 3 – Read the File with Spaces

Use **double quotes** around the filename.

```bash
cat "./--spaces in this filename--"
```

**Output**

```text
<Bandit Level 3 Password>
```

This is the password for **bandit3**.

> Quotation marks tell the shell to treat the entire filename as **one argument**.

**Alternative Method (Escaping Spaces)**

```bash
cat ./--spaces\ in\ this\ filename--
```

Both commands produce the same result.

---

### Step 4 – Exit the Current Session

```bash
exit
```

---

### Step 5 – Log into Bandit Level 3

```cmd
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

When prompted, enter the password obtained from the file.

**Successful Login Prompt**

```text
bandit3@bandit:~$
```

---

## Complete Command Sequence

```bash
pwd
ls
cat "./--spaces in this filename--"
exit
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

---

## Explanation

* `pwd` confirms the current directory.
* `ls` lists the available files.
* `cat "./--spaces in this filename--"` reads the file whose name contains spaces.
* `exit` closes the current SSH session.
* `ssh` connects to the next Bandit level.

---

## Why Quotes Are Required

| Command                               | Result                                                                                 |
| ------------------------------------- | -------------------------------------------------------------------------------------- |
| `cat --spaces in this filename--`     | Interprets `--spaces`, `in`, `this`, and `filename--` as separate arguments and fails. |
| `cat "./--spaces in this filename--"` | Reads the complete filename successfully.                                              |

Quotes prevent the shell from splitting the filename at spaces.

---

## Key Takeaways

* Learned how Linux handles **filenames containing spaces**.
* Used **double quotes** to access a file with spaces in its name.
* Learned an alternative method using **backslash (`\`)** to escape spaces.
* Retrieved the password for **Bandit Level 3** and logged into the next level.

---

## Result

Successfully accessed the file **`--spaces in this filename--`**, obtained the **Bandit Level 3** password, and logged into the **bandit3** account.
<img width="641" height="316" alt="image" src="https://github.com/user-attachments/assets/707aefd1-457b-4fac-82a3-935c9daf6660" />

