# Bandit Level 7 → Level 8

## Walkthrough

Step 1: Verify your current directory.

pwd

Output

/home/bandit7

This confirms you are in the `bandit7` home directory.

Step 2: List the files in the current directory.

ls

Output

data.txt

<img width="321" height="54" alt="image" src="https://github.com/user-attachments/assets/698163ce-5d7a-48fe-8354-a0008de4f6c9" />


The password is stored somewhere inside `data.txt`.

Step 3: Search for the word `millionth` in the file.

grep "millionth" data.txt

Output

millionth <Bandit Level 8 Password>

<img width="679" height="55" alt="image" src="https://github.com/user-attachments/assets/28b3717c-dfbd-47cd-be46-f9250c4e7809" />


The text after `millionth` is the password for bandit8.

Step 4: Exit the current SSH session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 5: Log in to bandit8.

ssh [bandit8@bandit.labs.overthewire.org](mailto:bandit8@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 3.

## Commands Used

pwd

Shows the current working directory.

ls

Lists files in the current directory.

grep "millionth" data.txt

Searches `data.txt` for the word millionth and prints the matching line.

exit

Closes the current SSH session.

ssh [bandit8@bandit.labs.overthewire.org](mailto:bandit8@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 8.

## Concept Learnt

The `grep` command searches for a word or pattern inside a file and prints only the matching line. It is useful for finding specific information in large text files without reading the entire file.

## Takeaways

* `grep` searches for text inside files.

* It prints only the lines that contain the matching word.

* `grep "millionth" data.txt` quickly finds the password.

* Use the retrieved password to log in to the next Bandit level.
