# SSH Login Format for Bandit (Windows Command Prompt / PowerShell)

Use this login command for all Bandit levels. Only change the level number and password.

## Level 0 Login

Step 1: Open Command Prompt or PowerShell.

Step 2: Connect to Bandit Level 0.

ssh [bandit0@bandit.labs.overthewire.org](mailto:bandit0@bandit.labs.overthewire.org) -p 2220

Step 3: Enter the password.

bandit0

Successful Login

bandit0@bandit:~$

## Levels 1 to 33 Login

For every level, replace `n` with the Bandit level number.

Login Command

ssh [banditn@bandit.labs.overthewire.org](mailto:banditn@bandit.labs.overthewire.org) -p 2220

Examples

ssh [bandit1@bandit.labs.overthewire.org](mailto:bandit1@bandit.labs.overthewire.org) -p 2220 ssh [bandit5@bandit.labs.overthewire.org](mailto:bandit5@bandit.labs.overthewire.org) -p 2220 ssh [bandit16@bandit.labs.overthewire.org](mailto:bandit16@bandit.labs.overthewire.org) -p 2220 ssh [bandit33@bandit.labs.overthewire.org](mailto:bandit33@bandit.labs.overthewire.org) -p 2220

After entering the correct password, you will see:

banditn@bandit:~$

`n` is the Bandit level you logged into.

## Commands Used

ssh [banditn@bandit.labs.overthewire.org](mailto:banditn@bandit.labs.overthewire.org) -p 2220

Connects to the Bandit server on port 2220.

## Concept Learnt

SSH (Secure Shell) is used to securely connect to the Bandit server. Every Bandit level uses the same SSH command; only the username and password change.

## Takeaways

* Use the same SSH command for every Bandit level.

* Replace `n` with the required level number.

* Always include `-p 2220` because Bandit uses port 2220.

* Enter the password obtained from the previous level.
