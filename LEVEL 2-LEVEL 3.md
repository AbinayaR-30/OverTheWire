# Bandit Level 2 → Level 3

## Walkthrough

Step 1: Verify your current directory.

pwd

Output

/home/bandit2

This confirms you are in the `bandit2` home directory.

Step 2: List the files in the current directory.

ls

Output

--spaces in this filename--

<img width="438" height="75" alt="image" src="https://github.com/user-attachments/assets/1f8a36bf-1353-4804-b8b1-3538e68b12b8" />


The directory contains a file whose name includes spaces.

Step 3: Read the file with spaces in its name.

cat "./--spaces in this filename--"

Output

<Bandit Level 3 Password>

<img width="1097" height="75" alt="image" src="https://github.com/user-attachments/assets/6b0b1945-a1ad-4048-a571-5c5d91720fbe" />


Copy this password. You will use it to log in to bandit3.

Step 4: Exit the current SSH session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 5: Log in to bandit3.

ssh [bandit3@bandit.labs.overthewire.org](mailto:bandit3@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 3.

## Commands Used

pwd

Shows the current working directory.

ls

Lists files in the current directory.

cat "./--spaces in this filename--"

Reads the file whose name contains spaces.

exit

Closes the current SSH session.

ssh [bandit3@bandit.labs.overthewire.org](mailto:bandit3@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 3.

<img width="867" height="327" alt="image" src="https://github.com/user-attachments/assets/a17be8aa-2d4e-4423-ba20-ca6d27bc8b98" />


## Concept Learnt

In Linux, spaces separate command arguments. If a filename contains spaces, the shell treats each word as a different argument. Use double quotes around the filename so Linux reads it as one complete filename.

## Takeaways

* Filenames can contain spaces in Linux.

* Use double quotes to access filenames with spaces.

* `cat "./--spaces in this filename--"` reads the file correctly.

* Use the retrieved password to log in to the next Bandit level.
