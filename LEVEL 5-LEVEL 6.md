# Bandit Level 5 → Level 6

## Walkthrough

Step 1: Verify your current directory.

pwd

Output

/home/bandit5

This confirms you are in the `bandit5` home directory.

Step 2: Move into the `inhere` directory.

ls

Output

inhere

Enter the directory.

cd inhere

Verify your location.

pwd

Output

/home/bandit5/inhere

<img width="1269" height="103" alt="image" src="https://github.com/user-attachments/assets/2c55e65a-2c56-4319-9a8c-168c245dfddd" />


Step 3: Find the file that matches the given conditions.

find . -type f -size 1033c ! -executable

Output

./maybehere07/.file2

This is the file that matches all the required conditions.

Step 4: Read the password file.

cat ./maybehere07/.file2

Output

<Bandit Level 6 Password>

<img width="682" height="61" alt="image" src="https://github.com/user-attachments/assets/f7ae72a3-53ac-43ef-912a-055b1f54c6af" />


Copy this password. You will use it to log in to bandit6.

Step 5: Exit the current SSH session.

exit

This returns you to Windows Command Prompt or PowerShell.

Step 6: Log in to bandit6.

ssh [bandit6@bandit.labs.overthewire.org](mailto:bandit6@bandit.labs.overthewire.org) -p 2220

When prompted, paste the password from Step 4.

## Commands Used

pwd

Shows the current working directory.

ls

Lists files and directories.

cd inhere

Moves into the `inhere` directory.

find . -type f -size 1033c ! -executable

Searches for a file that is exactly 1033 bytes and not executable.

cat ./maybehere07/.file2

Displays the contents of the password file.

exit

Closes the current SSH session.

ssh [bandit6@bandit.labs.overthewire.org](mailto:bandit6@bandit.labs.overthewire.org) -p 2220

Logs into Bandit Level 6.

## Concept Learnt

The `find` command searches for files and directories using conditions. You can filter files by type, size, permissions, and many other properties. This avoids checking files one by one.

## Takeaways

* `find` searches through directories recursively.

* `-type f` searches only for files.

* `-size 1033c` finds files that are exactly 1033 bytes.

* `! -executable` excludes executable files.

* Use the file returned by `find` to read the password with `cat`.
