# Bandit Level 1 → Level 2

## Walkthrough

Step 1: Verify your current directory.

pwd

Output

/home/bandit1

This confirms you are in the `bandit1` home directory.

Step 2: List the files in the current directory.

ls

Output

-

The directory contains a file named `-`.

Step 3: Read the file named `-`.

cat ./-

Output

<Bandit Level 2 Password>

<img width="540" height="66" alt="image" src="https://github.com/user-attachments/assets/143a5d0e-d1e5-4564-8ecd-24df6259be6b" />


Copy this password. You will use it to log in to bandit2.

Step 4: Exit the current SSH session.

exit

<img width="887" height="200" alt="image" src="https://github.com/user-attachments/assets/f68ae552-9216-4dab-9ba3-97c1c831b525" />


This returns you to Windows Command Prompt or PowerShell.

Step 5: Log in to bandit2.

ssh [bandit2@bandit.labs.overthewire.org](mailto:bandit2@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 3.

## Commands Used

pwd

Shows the current working directory.

ls

Lists files in the current directory.

cat ./-

Reads the contents of the file named `-`.

exit

Closes the current SSH session.

ssh [bandit2@bandit.labs.overthewire.org](mailto:bandit2@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 2.

## Concept Learnt

In Linux, `-` is a special character that usually represents standard input (stdin). To read a file whose actual name is `-`, use `./-`. The `./` tells Linux to look for a file with that name in the current directory.

## Takeaways

* `-` can be treated as a special input symbol in Linux.

* Use `./` before special filenames to access them correctly.

* `cat ./-` reads the file named `-`.

* Use the retrieved password to log in to the next Bandit level.
