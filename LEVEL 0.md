# Bandit Level 0 → Level 1

## Walkthrough

Step 1: Open Command Prompt or PowerShell.

Step 2: Connect to the Bandit server.

ssh [bandit0@bandit.labs.overthewire.org](mailto:bandit0@bandit.labs.overthewire.org) -p 2220

Step 3: If asked to verify the server, type:

yes

<img width="905" height="332" alt="image" src="https://github.com/user-attachments/assets/231ab545-da9d-4594-ab9d-623b6dc978c0" />


Step 4: Enter the password.

bandit0

Step 5: Check the current directory.

pwd

Output:

/home/bandit0

Step 6: List the files.

ls

Output:

readme

## Commands Used

ssh [bandit0@bandit.labs.overthewire.org](mailto:bandit0@bandit.labs.overthewire.org) -p 2220

Connects to the Bandit server using SSH on port 2220.

pwd

Shows the current working directory.

ls

Lists files in the current directory.

## Concept Learnt

SSH (Secure Shell) is a secure protocol used to connect to a remote Linux server from Windows. The `-p` option specifies the custom port number (2220 for Bandit).

## Takeaways

* SSH is used to connect to a remote Linux server securely.

* Type `yes` only during the first connection.

* Passwords are hidden while typing.

* `pwd` shows your current directory.

* `ls` lists files in the current directory.

