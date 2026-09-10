# Bandit Level 12 → Level 13 (Linux Terminal)

## Level Goal

The password for Bandit Level 13 is stored in the file `data.txt`. The file is a hexdump of another file that has been compressed multiple times using different compression formats (`gzip`, `bzip2`, `tar`, etc.).

The challenge is to reconstruct the original binary file from the hexdump and repeatedly decompress it until the password is revealed.

## Concept Learned

This level introduces several important Linux file utilities:

* `xxd -r` converts a hexadecimal dump back into its original binary file.

* `file` identifies the type of a file.

* `mv` renames files so decompression tools recognize the correct extension.

* `gzip`, `bzip2`, and `tar` extract compressed files.

* `mktemp -d` creates a secure temporary working directory.

This is the longest Bandit level so far and teaches how to inspect and decompress files step by step.

### Commands Used

|
Linux Command

|

Purpose

|
| --- | --- |
|

`pwd`

|

Shows the current working directory.

|
|

`mktemp -d`

|

Creates a secure temporary directory.

|
|

`cd`

|

Moves into the temporary directory.

|
|

`cp`

|

Copies `data.txt` into the temporary directory.

|
|

`xxd -r`

|

Converts a hexadecimal dump back into binary data.

|
|

`file`

|

Detects the current file type.

|
|

`mv`

|

Renames files with the correct extension.

|
|

`gzip -d`

|

Decompresses a Gzip file.

|
|

`bzip2 -d`

|

Decompresses a Bzip2 file.

|
|

`tar -xf`

|

Extracts a tar archive.

|
|

`ls`

|

Lists extracted files.

|
|

`cat`

|

Displays the password.

|
|

`rm -r`

|

Removes the temporary directory.

|
|

`exit`

|

Closes the current SSH session.

|
|

`ssh`

|

Logs into the next Bandit level.

|

## Walkthrough (Linux Terminal)

### Step 1 – Verify Your Current Directory

After logging into bandit12, check your current location.

Bash

```
bandit12@bandit:~$ pwd
```

Output

```
/home/bandit12
```

This confirms that you are inside the bandit12 home directory.

### Step 2 – Create a Temporary Working Directory

Create a secure temporary directory.

Bash

```
bandit12@bandit:~$ mktemp -d
```

Output (Example)

```
/tmp/tmp.X4A1b2C3d4
```

> Note: The directory name will be different every time.

Move into the temporary directory.

Bash

```
bandit12@bandit:~$ cd /tmp/tmp.X4A1b2C3d4
```

### Step 3 – Copy `data.txt` to the Temporary Directory

Copy the original file into the temporary workspace.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ cp ~/data.txt .
```

Output

```
(No output)
```

The file is now available inside the temporary directory.

### Step 4 – Convert the Hexdump into a Binary File

Reconstruct the original binary file.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ xxd -r data.txt data.bin
```

Output

```
(No output)
```

`data.bin` now contains the original binary data.

### Step 5 – Identify the File Type

Check what type of file `data.bin` is.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ file data.bin
```

Output

```
data.bin: gzip compressed data
```

The file is identified as a Gzip archive.

# Step-by-Step Decompression Process

Follow these steps exactly.

## 1. First Gzip Extraction

Rename the file with a `.gz` extension and decompress it.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data.bin data.gz
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ gzip -d data.gz
```

Check the new file type.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ file data
```

Output

```
data: bzip2 compressed data
```

## 2. First Bzip2 Extraction

Rename and decompress the Bzip2 file.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data data.bz2
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ bzip2 -d data.bz2
```

Check the file type again.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ file data
```

Output

```
data: gzip compressed data
```

## 3. Second Gzip Extraction

Rename and decompress again.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data data.gz
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ gzip -d data.gz
```

Check the file type.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ file data
```

Output

```
data: POSIX tar archive
```

## 4. First Tar Extraction

Rename and extract the tar archive.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data data.tar
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ tar -xf data.tar
```

List the extracted files.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ ls
```

Output

```
data5.bin
data.tar
data.txt
```

Check the extracted file type.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ file data5.bin
```

Output

```
data5.bin: POSIX tar archive
```

## 5. Second Tar Extraction

Rename and extract the second tar archive.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data5.bin data5.tar
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ tar -xf data5.tar
```

List the files again.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ ls
```

Output

```
data5.tar
data6.bin
data.tar
data.txt
```

Check the new file type.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ file data6.bin
```

Output

```
data6.bin: bzip2 compressed data
```

## 6. Second Bzip2 Extraction

Rename and decompress.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data6.bin data6.bz2
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ bzip2 -d data6.bz2
```

Check the file type.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ file data6
```

Output

```
data6: POSIX tar archive
```

## 7. Third Tar Extraction

Rename and extract the archive.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data6 data6.tar
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ tar -xf data6.tar
```

List the files.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ ls
```

Output

```
data8.bin
data6.tar
data5.tar
data.tar
data.txt
```

Check the file type.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ file data8.bin
```

Output

```
data8.bin: gzip compressed data
```

## 8. Final Gzip Extraction

Rename and decompress the final archive.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data8.bin data8.gz
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ gzip -d data8.gz
```

Check the final file.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ file data8
```

Output

```
data8: ASCII text
```

The file is now plain text and can be read.

### Step 6 – Read the Password

Display the contents of the final file.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ cat data8
```

Output

```
The password is <next level password>
```

This is the password for Bandit Level 13.

### Step 7 – Password for Bandit Level 13

```
<next level password>
```

Copy this password carefully.

### Step 8 – Exit the Temporary Directory and Clean Up

Return to your home directory and remove the temporary folder.

Bash

```
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ cd
bandit12@bandit:~$ rm -r /tmp/tmp.X4A1b2C3d4
bandit12@bandit:~$ exit
```

Output

```
logout
Connection to bandit.labs.overthewire.org closed.
```

### Step 9 – Log into Bandit Level 13

From your Linux terminal, connect to the next level.

Bash

```
user@ubuntu:~$ ssh bandit13@bandit.labs.overthewire.org -p 2220
```

When prompted, enter the password obtained from `cat data8`.

Password Prompt

```
bandit13@bandit.labs.overthewire.org's password:
```

Successful Login Prompt

Bash

```
bandit13@bandit:~$
```

You are now logged into Bandit Level 13.

## Complete Command Sequence

Bash

```
bandit12@bandit:~$ mktemp -d
bandit12@bandit:~$ cd /tmp/tmp.X4A1b2C3d4
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ cp ~/data.txt .
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ xxd -r data.txt data.bin

bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data.bin data.gz
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ gzip -d data.gz

bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data data.bz2
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ bzip2 -d data.bz2

bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data data.gz
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ gzip -d data.gz

bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data data.tar
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ tar -xf data.tar

bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data5.bin data5.tar
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ tar -xf data5.tar

bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data6.bin data6.bz2
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ bzip2 -d data6.bz2

bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data6 data6.tar
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ tar -xf data6.tar

bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ mv data8.bin data8.gz
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ gzip -d data8.gz

bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ cat data8
bandit12@bandit:/tmp/tmp.X4A1b2C3d4$ exit

user@ubuntu:~$ ssh bandit13@bandit.labs.overthewire.org -p 2220
```

## Explanation

|
Command

|

Explanation

|
| --- | --- |
|

`mktemp -d`

|

Creates a secure temporary workspace.

|
|

`cp ~/data.txt .`

|

Copies `data.txt` into the temporary directory.

|
|

`xxd -r data.txt data.bin`

|

Reconstructs the original binary file from the hexadecimal dump.

|
|

`file data.bin`

|

Identifies the current file type after each extraction.

|
|

`mv`

|

Renames files with the correct extension so decompression tools recognize them.

|
|

`gzip -d`

|

Decompresses Gzip-compressed files.

|
|

`bzip2 -d`

|

Decompresses Bzip2-compressed files.

|
|

`tar -xf`

|

Extracts files from a tar archive.

|
|

`cat data8`

|

Displays the password stored in the final text file.

|
|

`ssh bandit13@bandit.labs.overthewire.org -p 2220`

|

Logs into Bandit Level 13 using the recovered password.

|

## Why Use `file` After Every Extraction?

|
Command

|

Result

|
| --- | --- |
|

`file data.bin`

|

Identifies whether the file is gzip, bzip2, tar, or ASCII text.

|
|

`gzip -d`, `bzip2 -d`, `tar -xf`

|

Uses the correct extraction tool based on the detected file type.

|

Checking the file type after every extraction ensures you always know the next decompression step.

## Terminal Output Summary

```
data.bin  → gzip compressed data
data      → bzip2 compressed data
data      → gzip compressed data
data      → POSIX tar archive
data5.bin → POSIX tar archive
data6.bin → bzip2 compressed data
data6     → POSIX tar archive
data8.bin → gzip compressed data
data8     → ASCII text
```

The compression formats are removed one by one until the final file becomes readable text.

## Key Takeaways

* Learned how to reverse a hexdump using `xxd -r`.

* Used `mktemp -d` to create a secure temporary working directory.

* Identified file formats using the `file` command.

* Worked with gzip, bzip2, and tar compression formats.

* Performed multiple decompression steps in the correct order.

* Retrieved the password for Bandit Level 13 and logged into the next level.

## Result

Successfully reconstructed and decompressed the hexdump file, obtained the Bandit Level 13 password, and logged into the bandit13 account using the Linux terminal.

<img width="657" height="187" alt="image" src="https://github.com/user-attachments/assets/d416591a-626f-4a64-8e6b-77ff3c078b15" />
