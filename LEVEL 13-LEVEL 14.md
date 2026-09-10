# Bandit Level 13 → Level 14

## Walkthrough

Step 1: Verify that the private SSH key exists.

ls

Output

sshkey.private

<img width="400" height="75" alt="image" src="https://github.com/user-attachments/assets/bfeec039-8acd-44d1-ad66-8ff5fb91adb5" />


The `sshkey.private` file is used to log in as bandit14.

Step 2: Log in as `bandit14` using the private SSH key.

ssh -i sshkey.private -p 2220 bandit14@localhost

<img width="1362" height="617" alt="image" src="https://github.com/user-attachments/assets/5418850e-f05c-4165-a857-bfdb156eed63" />
<img width="1267" height="491" alt="image" src="https://github.com/user-attachments/assets/43971750-8ad1-4d21-8654-be077ed32cf6" />



Output

bandit14@bandit:~$

You are now logged in as bandit14.

Step 3: Read the password file.

cat /etc/bandit_pass/bandit14

Output

<Bandit Level 14 Password>

Copy this password. You will use it to log in to bandit14 directly.

Step 4: Exit the `bandit14` session.

exit

This returns you to the `bandit13` session.

Step 5: Exit the `bandit13` session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 6: Log in to bandit14 using the password you obtained.

ssh [bandit14@bandit.labs.overthewire.org](mailto:bandit14@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 3.

## Commands Used

ls

Lists files in the current directory.

ssh -i sshkey.private -p 2220 bandit14@localhost

Uses the private SSH key to log in as bandit14.

cat /etc/bandit_pass/bandit14

Displays the password stored in the protected file.

exit

Closes the current SSH session.

ssh [bandit14@bandit.labs.overthewire.org](mailto:bandit14@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 14 using the recovered password.

## Concept Learnt

SSH Key Authentication allows you to log in using a private key instead of a password. The `-i` option tells SSH which private key file to use. The key in `sshkey.private` belongs to bandit14, so it authenticates that user.

## Takeaways

* `-i` specifies the private SSH key for authentication.

* `sshkey.private` is used instead of a password.

* Always include `-p 2220` when connecting to Bandit.

* Read `/etc/bandit_pass/bandit14` only after logging in as `bandit14`.

* Use the retrieved password to log in to the next Bandit level.
