# Bandit Level 12 → Level 13

## Level Goal

The password for **Bandit Level 13** is stored in the file **`data.txt`**. The file is a **hexdump** of another file that has been **compressed multiple times** using different compression formats (`gzip`, `bzip2`, `tar`, etc.).

The challenge is to reconstruct the original binary file from the hexdump and repeatedly decompress it until the password is revealed.

---

## Concept Learned

This level introduces several important Linux file utilities:

* **`xxd -r`** converts a hexadecimal dump back into its original binary file.
* **`file`** identifies the type of a file.
* **`mv`** renames files so decompression tools recognize the correct extension.
* **`gzip`**, **`bzip2`**, and **`tar`** extract compressed files.
* **`mktemp -d`** creates a secure temporary working directory.

This is the longest Bandit level so far and teaches how to inspect and decompress files step by step.

### Commands Used

| Command     | Purpose                                         |
| ----------- | ----------------------------------------------- |
| `mktemp -d` | Creates a temporary directory.                  |
| `cp`        | Copies `data.txt` into the temporary directory. |
| `mv`        | Renames files with the correct extension.       |
| `xxd -r`    | Reverses a hexadecimal dump into binary data.   |
| `file`      | Detects the current file type.                  |
| `gzip -d`   | Decompresses a Gzip file.                       |
| `bzip2 -d`  | Decompresses a Bzip2 file.                      |
| `tar -xf`   | Extracts a tar archive.                         |
| `cat`       | Displays the password.                          |
| `ssh`       | Logs into the next Bandit level.                |

---

## Walkthrough (Windows Command Prompt)

### Step 1 – Verify Your Current Directory

After logging into **bandit12**, check your location.

```bash
pwd
```

**Output**

```text
/home/bandit12
```

---

### Step 2 – Create a Temporary Working Directory

Create a secure temporary directory.

```bash
mktemp -d
```

**Output (Example)**

```text
/tmp/tmp.X4A1b2C3d4
```

Copy the output path because it will be different every time.

Move into that directory.

```bash
cd /tmp/tmp.X4A1b2C3d4
```

---

### Step 3 – Copy `data.txt` to the Temporary Directory

```bash
cp ~/data.txt .
```

**Output**

```text
(No output)
```

The file is now available in the temporary directory.

---

### Step 4 – Convert the Hexdump into a Binary File

```bash
xxd -r data.txt data.bin
```

**Output**

```text
(No output)
```

`data.bin` now contains the original binary data.

---

### Step 5 – Identify the File Type

```bash
file data.bin
```

**Output**

```text
data.bin: gzip compressed data
```

The file is a Gzip archive.

---

## Step-by-Step Decompression Process

Follow this exact sequence.

### 1. Gzip

Rename the file with a `.gz` extension and decompress it.

```bash
mv data.bin data.gz
gzip -d data.gz
```

Check the new file.

```bash
file data
```

**Output**

```text
data: bzip2 compressed data
```

---

### 2. Bzip2

```bash
mv data data.bz2
bzip2 -d data.bz2
```

Check again.

```bash
file data
```

**Output**

```text
data: gzip compressed data
```

---

### 3. Gzip Again

```bash
mv data data.gz
gzip -d data.gz
```

Check again.

```bash
file data
```

**Output**

```text
data: POSIX tar archive
```

---

### 4. Tar Archive

```bash
mv data data.tar
tar -xf data.tar
```

List the extracted files.

```bash
ls
```

**Output**

```text
data5.bin
```

Check its type.

```bash
file data5.bin
```

**Output**

```text
data5.bin: POSIX tar archive
```

---

### 5. Second Tar Archive

```bash
mv data5.bin data5.tar
tar -xf data5.tar
```

List files.

```bash
ls
```

**Output**

```text
data6.bin
```

Check the file type.

```bash
file data6.bin
```

**Output**

```text
data6.bin: bzip2 compressed data
```

---

### 6. Bzip2 Again

```bash
mv data6.bin data6.bz2
bzip2 -d data6.bz2
```

Check again.

```bash
file data6
```

**Output**

```text
data6: POSIX tar archive
```

---

### 7. Third Tar Archive

```bash
mv data6 data6.tar
tar -xf data6.tar
```

List files.

```bash
ls
```

**Output**

```text
data8.bin
```

Check the file type.

```bash
file data8.bin
```

**Output**

```text
data8.bin: gzip compressed data
```

---

### 8. Final Gzip Extraction

```bash
mv data8.bin data8.gz
gzip -d data8.gz
```

Check the final file.

```bash
file data8
```

**Output**

```text
data8: ASCII text
```

The file is finally readable.

---

### Step 6 – Read the Password

```bash
cat data8
```

**Output**

```text
The password is gDtCV3zbQRqkl7b3rgQiAAA9fYuydxMZ
```

---

### Step 7 – Password for Bandit Level 13

```text
gDtCV3zbQRqkl7b3rgQiAAA9fYuydxMZ
```

This is the password for **bandit13**.

---

### Step 8 – Exit the Temporary Directory

```bash
cd
rm -r /tmp/tmp.X4A1b2C3d4
exit
```

---

### Step 9 – Log into Bandit Level 13

```cmd
ssh bandit13@bandit.labs.overthewire.org -p 2220
```

Enter the password above.

**Successful Login Prompt**

```text
bandit13@bandit:~$
```

---

## Complete Command Sequence

```bash
mktemp -d
cd /tmp/tmp.X4A1b2C3d4
cp ~/data.txt .
xxd -r data.txt data.bin

mv data.bin data.gz
gzip -d data.gz

mv data data.bz2
bzip2 -d data.bz2

mv data data.gz
gzip -d data.gz

mv data data.tar
tar -xf data.tar

mv data5.bin data5.tar
tar -xf data5.tar

mv data6.bin data6.bz2
bzip2 -d data6.bz2

mv data6 data6.tar
tar -xf data6.tar

mv data8.bin data8.gz
gzip -d data8.gz

cat data8
exit
ssh bandit13@bandit.labs.overthewire.org -p 2220
```

---

## Explanation

* `mktemp -d` creates a safe temporary workspace.
* `cp` copies `data.txt` so the original remains unchanged.
* `xxd -r` reconstructs the original binary file from the hexdump.
* `file` identifies each compression format.
* `mv` renames files with the correct extension before decompression.
* `gzip`, `bzip2`, and `tar` are used repeatedly until the final file becomes ASCII text.
* `cat` displays the password stored in the final text file.

---

## Why Use `file` After Every Extraction?

| Command                            | Result                                                          |
| ---------------------------------- | --------------------------------------------------------------- |
| `file data.bin`                    | Identifies whether the file is gzip, bzip2, tar, or ASCII text. |
| `gzip -d` / `bzip2 -d` / `tar -xf` | Uses the correct tool based on the file type.                   |

Checking the file type after each extraction ensures you always know the next decompression step.

---

## Key Takeaways

* Learned how to reverse a **hexdump** using `xxd -r`.
* Used `mktemp -d` to create a temporary working directory.
* Identified file formats using `file`.
* Worked with **gzip**, **bzip2**, and **tar** archives.
* Performed multiple decompression steps to recover the original text.
* Retrieved the password for **Bandit Level 13** and logged into the next level.

---

## Result

Successfully reconstructed and decompressed the hexdump file, obtained the **Bandit Level 13** password **`gDtCV3zbQRqkl7b3rgQiAAA9fYuydxMZ`**, and logged into the **bandit13** account.

<img width="657" height="187" alt="image" src="https://github.com/user-attachments/assets/d416591a-626f-4a64-8e6b-77ff3c078b15" />
