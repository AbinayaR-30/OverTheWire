# Bandit Level 3 → Level 4

## Walkthrough

Step 1: Verify your current directory.

pwd

Output

/home/bandit3

This confirms you are in the `bandit3` home directory.

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

/home/bandit3/inhere

Step 4: Display all files, including hidden files.

A normal `ls` will not show the hidden file.

ls -a

Output

. .. ...Hiding-From-You

<img width="1029" height="138" alt="image" src="https://github.com/user-attachments/assets/005444f3-424e-41ba-ba64-642ae5d7755c" />


The hidden file is `...Hiding-From-You`.

Step 5: Read the hidden file.

cat ...Hiding-From-You

Output

<Bandit Level 4 Password>

<img width="895" height="62" alt="image" src="https://github.com/user-attachments/assets/54f80bd1-a787-4bbe-8898-662f1ada8703" />


Copy this password. You will use it to log in to bandit4.

Step 6: Exit the current SSH session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 7: Log in to bandit4.

ssh [bandit4@bandit.labs.overthewire.org](mailto:bandit4@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 5.

## Commands Used

pwd

Shows the current working directory.

ls

Lists visible files and directories.

cd inhere

Moves into the `inhere` directory.

ls -a

Lists all files, including hidden files.

cat ...Hiding-From-You

Displays the contents of the hidden file.

exit

Closes the current SSH session.

ssh [bandit4@bandit.labs.overthewire.org](mailto:bandit4@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 4.

## Concept Learnt

In Linux, files and directories whose names start with a dot (`.`) are hidden files. A normal `ls` does not display them. Use `ls -a` to view all files, including hidden ones.

## Takeaways

* Hidden files begin with `.` in Linux.

* `ls` shows only visible files.

* `ls -a` shows both visible and hidden files.

* Use `cat` to read the hidden file and get the password for the next level.
