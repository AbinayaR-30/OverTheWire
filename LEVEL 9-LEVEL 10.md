# Bandit Level 9 → Level 10

## Walkthrough

Step 1: Verify your current directory.

pwd

Output

/home/bandit9

This confirms you are in the `bandit9` home directory.

Step 2: List the files in the current directory.

ls

Output

data.txt

<img width="319" height="67" alt="image" src="https://github.com/user-attachments/assets/6f34b32b-ede4-4812-82fe-3dc89dc52431" />


The password is hidden inside a binary file.

Step 3: Extract readable text and search for the password.

strings data.txt | grep "=="

Output

========== <Bandit Level 10 Password>

<img width="703" height="27" alt="image" src="https://github.com/user-attachments/assets/520dc1d0-9e28-433b-b65b-594012ef77c1" />
<img width="1312" height="457" alt="image" src="https://github.com/user-attachments/assets/2ace8d84-7d6b-4c1c-92ae-43b09bf202b0" />



The text after the `=` characters is the password for bandit10.

Step 4: Exit the current SSH session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 5: Log in to bandit10.

ssh [bandit10@bandit.labs.overthewire.org](mailto:bandit10@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 3.

## Commands Used

pwd

Shows the current working directory.

ls

Lists files in the current directory.

strings data.txt

Extracts readable text from a binary file.

grep "=="

Searches for lines containing `==`.

| (pipe)

Sends the output of `strings` to `grep`.

exit

Closes the current SSH session.

ssh [bandit10@bandit.labs.overthewire.org](mailto:bandit10@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 10.

## Concept Learnt

The `strings` command extracts human-readable text from a binary file. Using a pipe (`|`), the output is sent to `grep`, which filters only the line containing the `=` characters where the password is stored.

## Takeaways

* `strings` extracts readable text from binary files.

* `grep` filters specific patterns from the output.

* `|` connects two commands together.

* `strings data.txt | grep "=="` quickly finds the password.

* Use the extracted password to log in to the next Bandit level.
