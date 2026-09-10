# Bandit Level 8 → Level 9

## Walkthrough

Step 1: Verify your current directory.

pwd

Output

/home/bandit8

This confirms you are in the `bandit8` home directory.

Step 2: List the files in the current directory.

ls

Output

data.txt

<img width="685" height="72" alt="image" src="https://github.com/user-attachments/assets/a92901ae-7049-45be-8b7e-8b00da485c01" />


The password is hidden among many repeated lines in `data.txt`.

Step 3: Find the only line that appears exactly once.

sort data.txt | uniq -u

Output

<Bandit Level 9 Password>

<img width="1115" height="95" alt="image" src="https://github.com/user-attachments/assets/39e85688-d39f-4f91-9e35-f38e38dc624f" />


The unique line is the password for bandit9.

Step 4: Exit the current SSH session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 5: Log in to bandit9.

ssh [bandit9@bandit.labs.overthewire.org](mailto:bandit9@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 3.

## Commands Used

pwd

Shows the current working directory.

ls

Lists files in the current directory.

sort data.txt

Sorts all lines in the file alphabetically.

uniq -u

Prints only the lines that appear exactly once.

| (pipe)

Sends the output of one command as the input to another command.

exit

Closes the current SSH session.

ssh [bandit9@bandit.labs.overthewire.org](mailto:bandit9@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 9.

## Concept Learnt

A pipe (`|`) connects two commands together. Here, `sort` groups identical lines together, and `uniq -u` prints only the line that occurs exactly once. `uniq` works correctly only when duplicate lines are adjacent, so sorting is required first.

## Takeaways

* `sort` arranges lines alphabetically.

* `|` passes the output of one command to another.

* `uniq -u` finds lines that appear only once.

* Always use `sort` before `uniq` when duplicates are scattered in a file.

* Use the unique line as the password for the next Bandit level.
