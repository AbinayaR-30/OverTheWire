# Bandit Level 9 → Level 10

## Level Goal

The password for **Bandit Level 10** is stored in the file **`data.txt`** in one of the few **human-readable strings**, preceded by several **`=`** characters.

The challenge is to extract readable text from a binary file and search for the password.

---

## Concept Learned

This level introduces the **`strings`** command.

* **`strings`** extracts human-readable text from a binary file.
* **`grep`** filters the extracted text and finds the line containing a specific pattern (`=` characters).

### Commands Used

| Command   | Purpose                                                   |                                           |
| --------- | --------------------------------------------------------- | ----------------------------------------- |
| `pwd`     | Shows the current working directory.                      |                                           |
| `ls`      | Lists files in the current directory.                     |                                           |
| `strings` | Extracts readable strings from a binary file.             |                                           |
| `grep`    | Searches for a specific pattern in the extracted strings. |                                           |
| `         | `                                                         | Pipes output from one command to another. |
| `ssh`     | Logs into the next Bandit level.                          |                                           |

---

## Walkthrough (Windows Command Prompt)

### Step 1 – Verify Your Current Directory

After logging into **bandit9**, check your location.

```bash
pwd
```

**Output**

```text
/home/bandit9
```

---

### Step 2 – List Files

Display the files in the home directory.

```bash
ls
```

**Output**

```text
data.txt
```

The file contains mostly binary data, so `cat` will display unreadable characters.

---

### Step 3 – Extract Readable Strings and Search for `=`

Run the following command:

```bash
strings data.txt | grep "=="
```

### Explanation of the Command

| Part               | Meaning                                                   |                                                  |
| ------------------ | --------------------------------------------------------- | ------------------------------------------------ |
| `strings data.txt` | Extracts all human-readable strings from the binary file. |                                                  |
| `                  | `                                                         | Sends the extracted strings to the next command. |
| `grep "=="`        | Finds lines containing multiple `=` characters.           |                                                  |

**Output**

```text
========== B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
```

The text after the `=` characters is the password.

---

### Step 4 – Password for Bandit Level 10

```text
<lvl 10 password>
```

This is the password for **bandit10**.

---

### Step 5 – Exit the Current Session

```bash
exit
```

---

### Step 6 – Log into Bandit Level 10

```cmd
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

When prompted, enter the password above.

**Successful Login Prompt**

```text
bandit10@bandit:~$
```

---

## Complete Command Sequence

```bash
pwd
ls
strings data.txt | grep "=="
exit
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

---

## Explanation

* `strings` extracts readable text from a binary file.
* `grep "=="` filters only the lines containing several `=` characters.
* The password appears immediately after the `=` symbols.
* `ssh` logs into **bandit10** using the retrieved password.

---

## Why Use `strings`?

| Command                         | Result                                                   |
| ------------------------------- | -------------------------------------------------------- |
| `cat data.txt`                  | Displays unreadable binary characters.                   |
| `strings data.txt`              | Displays only readable text inside the binary file.      |
| `strings data.txt \| grep "=="` | Displays only the readable line containing the password. |

`strings` is useful for extracting hidden text from binary files.

---

## Key Takeaways

* Learned how to extract readable text using **`strings`**.
* Combined **`strings`** and **`grep`** using a pipe.
* Searched for a specific pattern (`=` characters).
* Retrieved the password for **Bandit Level 10** and logged into the next level.

---

## Result

Successfully extracted the readable string from `data.txt`, obtained the **Bandit Level 10** password `<lvl 10 password>`, and logged into the **bandit10** account.
<img width="456" height="143" alt="image" src="https://github.com/user-attachments/assets/e97ec14e-4e05-44d4-8d07-7c3f54e949a4" />

