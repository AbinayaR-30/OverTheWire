# Bandit Level 12 → Level 13

## Walkthrough

Step 1: Verify your current directory.

pwd

Output

/home/bandit12

This confirms you are in the `bandit12` home directory.

Step 2: Create a temporary working directory.

mktemp -d

Output (Example)

/tmp/tmp.X4A1b2C3d4

Move into the temporary directory.

cd /tmp/tmp.X4A1b2C3d4

<img width="571" height="88" alt="image" src="https://github.com/user-attachments/assets/49b1e255-5822-44a1-aff7-f3203e815c14" />


Step 3: Copy `data.txt` into the temporary directory.

cp ~/data.txt .

This creates a copy so the original file is not modified.

Step 4: Convert the hexdump back to a binary file.

xxd -r data.txt data.bin

This creates a binary file named `data.bin`.

Step 5: Check the file type.

file data.bin

Output

data.bin: gzip compressed data

Use `file` after every extraction to know the next compression format.

Step 6: Decompress the files in the correct order.

1. Gzip

**mv data.bin data.gz gzip -d data.gz**

2. Bzip2

**mv data data.bz2 bzip2 -d data.bz2**

3. Gzip

**mv data data.gz gzip -d data.gz**

4. Tar

**mv data data.tar tar -xf data.tar**

5. Tar

**mv data5.bin data5.tar tar -xf data5.tar**

6. Bzip2

mv data6.bin data6.bz2 bzip2 -d data6.bz2

7. Tar

**mv data6 data6.tar tar -xf data6.tar**

8. Gzip

**mv data8.bin data8.gz gzip -d data8.gz**

The final file becomes ASCII text.

Step 7: Read the final file.

**cat data8**

Output

**The password is <Bandit Level 13 Password>**

Copy this password. You will use it to log in to bandit13.

Step 8: Remove the temporary directory and exit.

**cd rm -r /tmp/tmp.X4A1b2C3d4 exit**

This cleans up the temporary files and returns you to Windows Command Prompt or PowerShell.

Step 9: Log in to bandit13.

ssh [bandit13@bandit.labs.overthewire.org](mailto:bandit13@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 7.

## Commands Used

pwd

Shows the current working directory.

mktemp -d

Creates a temporary working directory.

cd

Moves into the temporary directory.

cp ~/data.txt .

Copies `data.txt` into the temporary directory.

xxd -r data.txt data.bin

Converts the hexdump back into a binary file.

file

Identifies the type of the current file.

mv

Renames a file with the correct extension.

gzip -d

Decompresses a Gzip file.

bzip2 -d

Decompresses a Bzip2 file.

tar -xf

Extracts a tar archive.

cat data8

Displays the final password.

rm -r

Deletes the temporary directory.

exit

Closes the current SSH session.

ssh [bandit13@bandit.labs.overthewire.org](mailto:bandit13@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 13.

## Concept Learnt

This level teaches how to reconstruct and decompress files step by step.

* `xxd -r` converts a hexadecimal dump back into its original binary file.

* `file` identifies the current file type after each extraction.

* `gzip`, `bzip2`, and `tar` extract different compression formats.

* `mktemp -d` creates a safe temporary workspace for processing files.

## Takeaways

* Always work in a temporary directory when modifying files.

* Use `xxd -r` to convert a hexdump into a binary file.

* Use `file` after every extraction to identify the next file type.

* Rename files with the correct extension before decompressing.

* Keep extracting until the file becomes ASCII text, then use `cat` to read the password.
