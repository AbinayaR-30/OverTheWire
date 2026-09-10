# Bandit Level 0 → Level 1

## Walkthrough

Step 1: Verify your current directory after logging into `bandit0`.

pwd

Output

/home/bandit0

This confirms you are in the `bandit0` home directory.

Step 2: List the files in the current directory.

ls

Output

readme

The `readme` file contains the password for the next level.

Step 3: Display the contents of the `readme` file.

cat readme

Output

<Bandit Level 1 Password>

<img width="1245" height="249" alt="image" src="https://github.com/user-attachments/assets/4c8bb197-ddf7-4c95-a3b4-232823ccdcb9" />


Copy this password. You will use it to log in to bandit1.

Step 4: Exit the current SSH session.

exit

This returns you to your Windows Command Prompt or PowerShell.

Step 5: Log in to bandit1 using the password from `readme`.

ssh [bandit1@bandit.labs.overthewire.org](mailto:bandit1@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 3.

## Commands Used

pwd

Shows the current working directory.

ls

Lists files in the current directory.

cat readme

Displays the contents of the `readme` file.

exit

Closes the current SSH session.

ssh [bandit1@bandit.labs.overthewire.org](mailto:bandit1@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 1.

## Concept Learnt

This level teaches basic Linux file operations.

* `pwd` tells you where you are in the file system.

* `ls` shows the files in the current directory.

* `cat` reads and displays the contents of a file.

* `exit` closes the SSH connection.

## Takeaways

* Check your location using `pwd`.

* Use `ls` to find files in a directory.

* Use `cat` to read a file's contents.

* Exit the current session before logging into the next Bandit level.

* Use the retrieved password to connect as the next user.
