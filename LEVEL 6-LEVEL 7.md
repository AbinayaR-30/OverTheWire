# Bandit Level 6 → Level 7

## Walkthrough

Step 1: Verify your current directory.

pwd

Output

/home/bandit6

This confirms you are in the `bandit6` home directory.

Step 2: Search the entire server for the required file.

find / -user bandit7 -group bandit6 -size 33c 2>/dev/null

Output

/var/lib/dpkg/info/bandit7.password

<img width="1451" height="87" alt="image" src="https://github.com/user-attachments/assets/abad4ad4-7708-4f65-95c2-02cb6ce9b7ea" />


This is the file that matches all the required conditions.

Step 3: Read the password file.

cat /var/lib/dpkg/info/bandit7.password

Output

<Bandit Level 7 Password>

<img width="1082" height="75" alt="image" src="https://github.com/user-attachments/assets/6644f5c6-1cb0-41a1-9228-be525a3de949" />


Copy this password. You will use it to log in to bandit7.

Step 4: Exit the current SSH session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 5: Log in to bandit7.

ssh [bandit7@bandit.labs.overthewire.org](mailto:bandit7@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 3.

## Commands Used

pwd

Shows the current working directory.

find / -user bandit7 -group bandit6 -size 33c 2>/dev/null

Searches the entire server for a file owned by bandit7, grouped under bandit6, and exactly 33 bytes in size.

cat /var/lib/dpkg/info/bandit7.password

Displays the contents of the password file.

exit

Closes the current SSH session.

ssh [bandit7@bandit.labs.overthewire.org](mailto:bandit7@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 7.

## Concept Learnt

The `find` command can search the entire Linux filesystem using multiple filters such as owner, group, and file size. The `2>/dev/null` part hides Permission denied errors, making the output clean.

## Takeaways

* Use `/` to search the entire server.

* `-user` filters files by owner.

* `-group` filters files by group.

* `-size 33c` finds files that are exactly 33 bytes.

* `2>/dev/null` hides permission error messages.

* Read the returned file with `cat` to get the password for the next level.
