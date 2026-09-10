# Bandit Level 10 → Level 11

## Walkthrough

Step 1: Verify your current directory.

pwd

Output

/home/bandit10

This confirms you are in the `bandit10` home directory.

Step 2: List the files in the current directory.

ls

Output

data.txt

<img width="441" height="72" alt="image" src="https://github.com/user-attachments/assets/38adc479-32ee-4e61-a18d-2f046ee01e0c" />


The file contains Base64-encoded text.

Step 3: Decode the Base64 data.

base64 -d data.txt

Output

The password is <Bandit Level 11 Password>

<img width="808" height="52" alt="image" src="https://github.com/user-attachments/assets/9922be29-45fa-4b5f-bcfb-5be8701c46b9" />


The decoded text contains the password for bandit11.

Step 4: Exit the current SSH session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 5: Log in to bandit11.

ssh [bandit11@bandit.labs.overthewire.org](mailto:bandit11@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 3.

## Commands Used

pwd

Shows the current working directory.

ls

Lists files in the current directory.

base64 -d data.txt

Decodes the Base64-encoded contents of `data.txt`.

exit

Closes the current SSH session.

ssh [bandit11@bandit.labs.overthewire.org](mailto:bandit11@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 11.

## Concept Learnt

Base64 is an encoding method that converts data into readable ASCII characters. The `base64 -d` command decodes the encoded text back to its original form.

## Takeaways

* Base64 stores data in an encoded format.

* `base64 -d` decodes encoded data into readable text.

* The decoded output contains the password.

* Use the decoded password to log in to the next Bandit level.
