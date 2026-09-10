# Bandit Level 11 → Level 12

## Level Goal

The password for **Bandit Level 12** is stored in the file **`data.txt`**, where all lowercase (`a-z`) and uppercase (`A-Z`) letters have been **rotated by 13 positions (ROT13)**.

The challenge is to decode the ROT13-encoded text using the **`tr`** command.

---

## Concept Learned

This level introduces the **`tr` (translate)** command.

* **ROT13** is a simple substitution cipher that shifts every letter by **13 positions**.
* Applying **ROT13 twice** returns the original text.
* The `tr` command replaces characters from one set with another.

### Commands Used

| Command | Purpose                                      |                                           |
| ------- | -------------------------------------------- | ----------------------------------------- |
| `pwd`   | Shows the current working directory.         |                                           |
| `ls`    | Lists files in the current directory.        |                                           |
| `cat`   | Displays the contents of `data.txt`.         |                                           |
| `tr`    | Translates (rotates) characters using ROT13. |                                           |
| `       | `                                            | Pipes output from one command to another. |
| `ssh`   | Logs into the next Bandit level.             |                                           |

---

## Walkthrough (Windows Command Prompt)

### Step 1 – Verify Your Current Directory

After logging into **bandit11**, check your location.

```bash
pwd
```

**Output**

```text
/home/bandit11
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

The file contains text encoded using **ROT13**.

---

### Step 3 – View the Encoded Text (Optional)

```bash
cat data.txt
```

**Output (Example)**

```text
Gur cnffjbeq vf ...
```

The text is not readable because it is encoded with ROT13.

---

### Step 4 – Decode the ROT13 Text

Run the following command:

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

### Explanation of the Command

| Part                         | Meaning                                                          |                                       |
| ---------------------------- | ---------------------------------------------------------------- | ------------------------------------- |
| `cat data.txt`               | Reads the contents of the file.                                  |                                       |
| `                            | `                                                                | Sends the output to the next command. |
| `tr 'A-Za-z' 'N-ZA-Mn-za-m'` | Rotates uppercase and lowercase letters by 13 positions (ROT13). |                                       |

**Output**

```text
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

The decoded text contains the password.

---

### Step 5 – Password for Bandit Level 12

```text
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

This is the password for **bandit12**.

---

### Step 6 – Exit the Current Session

```bash
exit
```

---

### Step 7 – Log into Bandit Level 12

```cmd
ssh bandit12@bandit.labs.overthewire.org -p 2220
```

When prompted, enter the password above.

**Successful Login Prompt**

```text
bandit12@bandit:~$
```

---

## Complete Command Sequence

```bash
pwd
ls
cat data.txt
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
exit
ssh bandit12@bandit.labs.overthewire.org -p 2220
```

---

## Explanation

* `cat data.txt` reads the encoded text.
* `tr 'A-Za-z' 'N-ZA-Mn-za-m'` applies the **ROT13 cipher**.
* The decoded output reveals the password for the next level.
* `ssh` logs into **bandit12** using the decoded password.

---

## Why Use `tr`?

| Command                                      | Result                                     |
| -------------------------------------------- | ------------------------------------------ |
| `cat data.txt`                               | Displays ROT13-encoded text.               |
| `cat data.txt \| tr 'A-Za-z' 'N-ZA-Mn-za-m'` | Decodes the ROT13 text into readable text. |

`tr` is commonly used for character translation and substitution in Linux.

---

## Key Takeaways

* Learned what the **ROT13 cipher** is.
* Used the **`tr`** command for character translation.
* Combined `cat` and `tr` using a **pipe (`|`)**.
* Retrieved the password for **Bandit Level 12** and logged into the next level.

---

## Result

Successfully decoded the ROT13 text in `data.txt`, obtained the **Bandit Level 12** password `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`, and logged into the **bandit12** account.
<img width="940" height="205" alt="image" src="https://github.com/user-attachments/assets/05cd8743-a39b-44b9-8b6f-fea0ecb46f6f" />

