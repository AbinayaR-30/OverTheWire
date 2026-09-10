# Bandit Level 11 → Level 12

## Walkthrough

Step 1: Verify your current directory.

pwd

Output

/home/bandit11

This confirms you are in the `bandit11` home directory.

Step 2: List the files in the current directory.

ls

Output

data.txt

<img width="321" height="51" alt="image" src="https://github.com/user-attachments/assets/4c7df8a2-c6d4-4738-a727-862d10dbe7e2" />

The file contains text encoded using the ROT13 cipher.

Step 3: Decode the ROT13 text.

cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

Output

The password is <Bandit Level 12 Password>

<img width="882" height="57" alt="image" src="https://github.com/user-attachments/assets/fd2820f6-8128-4956-8566-fa6d1304596e" />
<img width="886" height="49" alt="image" src="https://github.com/user-attachments/assets/2bada0f5-4b9f-4ec3-b4e6-0ff81324f2cf" />


The decoded text contains the password for bandit12.

Step 4: Exit the current SSH session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 5: Log in to bandit12.

ssh [bandit12@bandit.labs.overthewire.org](mailto:bandit12@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 3.

## Commands Used

pwd

Shows the current working directory.

ls

Lists files in the current directory.

cat data.txt

Reads the contents of `data.txt`.

tr 'A-Za-z' 'N-ZA-Mn-za-m'

Decodes ROT13 by translating each letter 13 positions.

| (pipe)

Sends the output of `cat` to `tr`.

exit

Closes the current SSH session.

ssh [bandit12@bandit.labs.overthewire.org](mailto:bandit12@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 12.

## Concept Learnt

ROT13 is a letter substitution cipher that shifts every alphabet letter by 13 positions. The `tr` command translates characters from one set to another, making it useful for decoding ROT13 text.

## Takeaways

* ROT13 shifts letters by 13 positions.

* `tr` translates characters from one alphabet set to another.

* `cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'` decodes the file.

* Use the decoded password to log in to the next Bandit level.
