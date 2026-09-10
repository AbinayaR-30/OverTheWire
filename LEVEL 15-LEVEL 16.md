# Bandit Level 15 → Level 16

## Walkthrough

Step 1: Read the current Bandit Level 15 password.

cat /etc/bandit_pass/bandit15

Output

<Bandit Level 15 Password>

Copy this password. You will send it through an SSL/TLS connection.

Step 2: Connect to port 30001 using OpenSSL.

openssl s_client -connect localhost:30001 -quiet

The terminal waits for your input after the secure connection is established.

<img width="1651" height="382" alt="image" src="https://github.com/user-attachments/assets/bd87573c-be90-4f96-bd0b-99eb1c48a7b5" />

Step 3: Paste the password and press Enter.

<Bandit Level 15 Password>

Output

Correct! <Bandit Level 16 Password>

<img width="376" height="70" alt="image" src="https://github.com/user-attachments/assets/1b341f55-7716-4af5-ad35-dc6b666e8b69" />

The second line is the password for bandit16.

Step 4: Close the OpenSSL connection.

Ctrl + C

This returns you to the Bandit terminal.

Step 5: Exit the SSH session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 6: Log in to bandit16.

ssh [bandit16@bandit.labs.overthewire.org](mailto:bandit16@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 3.

## Commands Used

cat /etc/bandit_pass/bandit15

Reads the current Bandit Level 15 password.

openssl s_client -connect localhost:30001 -quiet

Creates a secure SSL/TLS connection to port 30001.

Ctrl + C

Closes the OpenSSL connection.

exit

Closes the current SSH session.

ssh [bandit16@bandit.labs.overthewire.org](mailto:bandit16@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 16.

## Concept Learnt

SSL/TLS encrypts communication between a client and a server. `openssl s_client` acts as an SSL/TLS client, allowing you to connect securely to services that do not accept normal TCP connections.

## Takeaways

* `openssl s_client` creates a secure SSL/TLS connection.

* `-connect localhost:30001` connects to the service on port 30001.

* `-quiet` hides certificate details and shows only the interaction.

* Paste the current password after the connection is established.

* Press Ctrl + C to close the connection after receiving the next password.

* Use the received password to log in to the next Bandit level.
