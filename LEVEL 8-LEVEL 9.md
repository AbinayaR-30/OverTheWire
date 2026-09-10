# Bandit Level 8 → Level 9

## Level Goal

The password for **Bandit Level 9** is stored in the file **`data.txt`** and is the **only line that appears exactly once**.

The challenge is to use **`sort`** and **`uniq`** together through a **pipe (`|`)** to find the unique line.

---

## Concept Learned

This level introduces **piping** (`|`), which sends the output of one command as the input to another command.

* **`sort`** arranges all lines in alphabetical order.
* **`uniq`** removes or filters duplicate lines.
* **`uniq -u`** prints only lines that occur **once**.

### Commands Used

| Command   | Purpose                                      |                                           |
| --------- | -------------------------------------------- | ----------------------------------------- |
| `pwd`     | Shows the current working directory.         |                                           |
| `ls`      | Lists files in the current directory.        |                                           |
| `sort`    | Sorts the contents of a file alphabetically. |                                           |
| `uniq -u` | Displays only unique (non-repeated) lines.   |                                           |
| `         | `                                            | Pipes output from one command to another. |
| `ssh`     | Logs into the next Bandit level.             |                                           |

---

## Walkthrough (Windows Command Prompt)

### Step 1 – Verify Your Current Directory

After logging into **bandit8**, check your location.

```bash
pwd
```

**Output**

```text
/home/bandit8
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

The password is hidden among many repeated lines inside `data.txt`.

---

### Step 3 – Find the Only Unique Line

Run the following command:

```bash
sort data.txt | uniq -u
```

### Explanation of the Command

| Part            | Meaning                                         |                                              |
| --------------- | ----------------------------------------------- | -------------------------------------------- |
| `sort data.txt` | Sorts all lines in `data.txt`.                  |                                              |
| `               | `                                               | Sends the sorted output to the next command. |
| `uniq -u`       | Prints only the line that appears exactly once. |                                              |

**Output**

```text
<next level password>
```

This unique line is the password for **bandit9**.

---

### Step 4 – Password for Bandit Level 9

```text
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```

---

### Step 5 – Exit the Current Session

```bash
exit
```

---

### Step 6 – Log into Bandit Level 9

```cmd
ssh bandit9@bandit.labs.overthewire.org -p 2220
```

When prompted, enter the password above.

**Successful Login Prompt**

```text
bandit9@bandit:~$
```

---

## Complete Command Sequence

```bash
pwd
ls
sort data.txt | uniq -u
exit
ssh bandit9@bandit.labs.overthewire.org -p 2220
```

---

## Explanation

* `sort` arranges all identical lines together.
* `uniq -u` prints only the line that occurs once.
* The pipe (`|`) connects the output of `sort` directly to `uniq`.
* `ssh` logs into **bandit9** using the retrieved password.

---

## Why `sort` Is Required Before `uniq`

| Command                    | Result                                                                               |
| -------------------------- | ------------------------------------------------------------------------------------ |
| `uniq -u data.txt`         | May not work correctly because duplicate lines are not adjacent.                     |
| `sort data.txt \| uniq -u` | Groups duplicate lines together, allowing `uniq` to identify the single unique line. |

`uniq` only compares **adjacent** lines, so sorting is an important first step.

---

## Key Takeaways

* Learned how to use **pipes (`|`)** in Linux.
* Combined **`sort`** and **`uniq -u`** to process text efficiently.
* Found the only unique line in a large file.
* Retrieved the password for **Bandit Level 9** and logged into the next level.

---

## Result

Successfully found the only unique line in `data.txt`, obtained the **Bandit Level 9** password `<next level password>`, and logged into the **bandit9** account.
<img width="447" height="130" alt="image" src="https://github.com/user-attachments/assets/c6d3a3fe-ca29-44bc-aa2b-a5cd2bc82e5b" />

