# Bandit Level 14 → Level 15

## Walkthrough

Step 1: Read the current Bandit Level 14 password.

cat /etc/bandit_pass/bandit14

Output

<Bandit Level 14 Password>

Copy this password. You will send it to a network service.

Step 2: Connect to port 30000 using Netcat.

nc localhost 30000

The terminal waits for your input.

Step 3: Paste the password and press Enter.

<Bandit Level 14 Password>

Output

Correct! <Bandit Level 15 Password>

<img width="636" height="58" alt="image" src="https://github.com/user-attachments/assets/a70acddb-ef99-4125-a8ea-507fe7b2694d" />


The second line is the password for bandit15.

Step 4: Close the Netcat connection.

Ctrl + C

This returns you to the Bandit terminal.

Step 5: Exit the SSH session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 6: Log in to bandit15.

ssh [bandit15@bandit.labs.overthewire.org](mailto:bandit15@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 3.

## Commands Used

cat /etc/bandit_pass/bandit14

Reads the current Bandit Level 14 password.

nc localhost 30000

Connects to the TCP service running on port 30000.

Ctrl + C

Closes the Netcat connection.

exit

Closes the current SSH session.

ssh [bandit15@bandit.labs.overthewire.org](mailto:bandit15@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 15.

## Concept Learnt

Netcat (`nc`) is a networking tool used to connect to TCP or UDP ports. In this level, it connects to a service on localhost:30000, sends the current password, and receives the password for the next level.

## Takeaways

* `nc` connects to a network service on a specific port.

* `localhost` means the current Bandit server.

* Paste the current password after connecting.

* Press Ctrl + C to close the Netcat session.

* Use the received password to log in to the next Bandit level.
