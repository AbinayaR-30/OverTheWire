# Bandit Level 10 → Level 11

## Level Goal

The password for **Bandit Level 11** is stored in the file **`data.txt`**, which contains **Base64 encoded data**.

The challenge is to decode the Base64-encoded content and retrieve the original password.

---

## Concept Learned

This level introduces the **`base64`** command.

* **Base64** is an encoding scheme that converts binary or text data into ASCII characters.
* **`base64 -d`** decodes Base64-encoded data back to its original form.

### Commands Used

| Command     | Purpose                               |                                           |
| ----------- | ------------------------------------- | ----------------------------------------- |
| `pwd`       | Shows the current working directory.  |                                           |
| `ls`        | Lists files in the current directory. |                                           |
| `cat`       | Displays the contents of `data.txt`.  |                                           |
| `base64 -d` | Decodes Base64-encoded data.          |                                           |
| `           | `                                     | Pipes output from one command to another. |
| `ssh`       | Logs into the next Bandit level.      |                                           |

---

## Walkthrough (Windows Command Prompt)

### Step 1 – Verify Your Current Directory

After logging into **bandit10**, check your location.

```bash
pwd
```

**Output**

```text
/home/bandit10
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

The file contains Base64-encoded text.

---

### Step 3 – View the Encoded Data (Optional)

```bash
cat data.txt
```

**Output (Example)**

```text
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTU2cyUlducE5WajNxUnI=
```

This is Base64-encoded content.

---

### Step 4 – Decode the Base64 Data

Run the following command:

```bash
base64 -d data.txt
```

**Output**

```text
The password is <next level password>
```

The decoded text contains the password.

---

### Step 5 – Password for Bandit Level 11

```text
<next level password>
```

This is the password for **bandit11**.

---

### Step 6 – Exit the Current Session

```bash
exit
```

---

### Step 7 – Log into Bandit Level 11

```cmd
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

When prompted, enter the password above.

**Successful Login Prompt**

```text
bandit11@bandit:~$
```

---

## Complete Command Sequence

```bash
pwd
ls
cat data.txt
base64 -d data.txt
exit
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

---

## Explanation

* `cat data.txt` displays the encoded content.
* `base64 -d data.txt` decodes the file and prints the original text.
* The decoded output contains the password for the next level.
* `ssh` logs into **bandit11** using the decoded password.

---

## Why Use `base64 -d`?

| Command              | Result                                                   |
| -------------------- | -------------------------------------------------------- |
| `cat data.txt`       | Displays encoded Base64 text.                            |
| `base64 -d data.txt` | Decodes the Base64 text into its original readable form. |

The `-d` option stands for **decode**.

---

## Key Takeaways

* Learned what **Base64 encoding** is.
* Used **`base64 -d`** to decode encoded text.
* Retrieved the password from the decoded output.
* Logged into **bandit11** using SSH.

---

## Result

Successfully decoded the Base64 data in `data.txt`, obtained the **Bandit Level 11** password `<next level password>`, and logged into the **bandit11** account.
<img width="726" height="164" alt="image" src="https://github.com/user-attachments/assets/40e7dfa4-2afc-487c-8af7-4c143ac54a73" />

