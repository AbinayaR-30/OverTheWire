# Bandit Level 4 → Level 5

## Walkthrough

Step 1: Verify your current directory.

pwd

Output

/home/bandit4

This confirms you are in the `bandit4` home directory.

Step 2: List the files in the current directory.

ls

Output

inhere

The `inhere` directory contains the password file.

Step 3: Move into the `inhere` directory.

cd inhere

Verify your location.

pwd

Output

/home/bandit4/inhere

Step 4: List all files inside the directory.

ls

Output

file00 file01 file02 file03 file04 file05 file06 file07 file08 file09

There are multiple files, but only one is human-readable.

Step 5: Identify the human-readable file.

file ./*

Output (Example)

./file00: data ./file01: data ./file02: data ./file03: ASCII text ./file04: data

<img width="940" height="313" alt="image" src="https://github.com/user-attachments/assets/4d76f719-1f56-45b9-a85b-d9665d074fa8" />


Find the file marked ASCII text (for example, `file03`).

Step 6: Read the human-readable file.

cat ./file03

Output

<Bandit Level 5 Password>

<img width="591" height="70" alt="image" src="https://github.com/user-attachments/assets/53d2cc6f-cfd0-4f0e-b8bc-58c0e2d9375b" />


Copy this password. You will use it to log in to bandit5.

Step 7: Exit the current SSH session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 8: Log in to bandit5.

ssh [bandit5@bandit.labs.overthewire.org](mailto:bandit5@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 6.

## Commands Used

pwd

Shows the current working directory.

ls

Lists files in the current directory.

cd inhere

Moves into the `inhere` directory.

file ./*

Checks the type of every file in the directory.

cat ./file03

Displays the contents of the human-readable file.

exit

Closes the current SSH session.

ssh [bandit5@bandit.labs.overthewire.org](mailto:bandit5@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 5.

## Concept Learnt

The `file` command identifies the type of a file without opening it. It helps distinguish ASCII text files from binary or unreadable files, making it easy to find the correct file.

## Takeaways

* Use `file` to identify file types.

* `file ./*` checks all files in the current directory at once.

* Look for the file marked ASCII text.

* Use `cat` to read the human-readable file and get the password for the next level.
