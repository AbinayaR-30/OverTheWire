Bandit Level 11 → Level 12 (Linux Terminal)
Level Goal

The password for Bandit Level 12 is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions (ROT13).

The challenge is to decode the ROT13-encoded text using the tr command.

Concept Learned

This level introduces the tr (translate) command.

ROT13 is a simple substitution cipher that shifts every letter by 13 positions.

Applying ROT13 twice returns the original text.

The tr command replaces or translates characters from one set into another.

Commands Used

Linux Command

	

Purpose




pwd

	

Shows the current working directory.




ls

	

Lists files in the current directory.




cat data.txt

	

Displays the contents of data.txt.




tr 'A-Za-z' 'N-ZA-Mn-za-m'

	

Translates characters using the ROT13 cipher.




cat data.txt \| tr 'A-Za-z' 'N-ZA-Mn-za-m'

	

Uses a pipe (\|) to decode the file contents.




exit

	

Closes the current SSH session.




ssh

	

Logs into the next Bandit level.

Pipe (|) sends the output of one command as the input to another command.

Walkthrough (Linux Terminal)
Step 1 – Verify Your Current Directory

After logging into bandit11, check your current location.

bandit11@bandit:~$ pwd

Output

/home/bandit11

This confirms that you are inside the bandit11 home directory.

Step 2 – List Files

Display the files in the current directory.

bandit11@bandit:~$ ls

Output

data.txt

The file data.txt contains text encoded using the ROT13 cipher.

Step 3 – View the Encoded Text (Optional)

Display the contents of the file before decoding.

bandit11@bandit:~$ cat data.txt

Output (Example)

Gur cnffjbeq vf ...

The text is not readable because it has been encoded using ROT13.

Step 4 – Decode the ROT13 Text

Run the following command:

bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
Explanation of the Command

| Command Part | Meaning | |--------------|---------| | cat data.txt | Reads the contents of the file. | | | | Passes the output to the next command. | | tr 'A-Za-z' 'N-ZA-Mn-za-m' | Rotates uppercase and lowercase letters by 13 positions (ROT13). |

Output

The password is <next level password>

The decoded text contains the password for the next Bandit level.

Step 5 – Password for Bandit Level 12
<next level password>

Copy this password carefully. It will be used to log into bandit12.

Step 6 – Exit the Current Session
bandit11@bandit:~$ exit

Output

logout
Connection to bandit.labs.overthewire.org closed.
Step 7 – Log into Bandit Level 12

From your Linux terminal, connect to the next level.

user@ubuntu:~$ ssh bandit12@bandit.labs.overthewire.org -p 2220

When prompted, enter the decoded password.

Password Prompt

bandit12@bandit.labs.overthewire.org's password:

Type the password and press Enter.

Successful Login Prompt

bandit12@bandit:~$

You are now logged into Bandit Level 12.

Complete Command Sequence
bandit11@bandit:~$ pwd
bandit11@bandit:~$ ls
bandit11@bandit:~$ cat data.txt
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
bandit11@bandit:~$ exit

user@ubuntu:~$ ssh bandit12@bandit.labs.overthewire.org -p 2220
Explanation

Command

	

Explanation




pwd

	

Confirms the current working directory.




ls

	

Lists the files available in the directory.




cat data.txt

	

Displays the ROT13-encoded text.




cat data.txt \| tr 'A-Za-z' 'N-ZA-Mn-za-m'

	

Decodes the ROT13 text into readable text.




exit

	

Closes the current SSH session.




ssh bandit12@bandit.labs.overthewire.org -p 2220

	

Connects to Bandit Level 12 using SSH.

Why Use tr?

Command

	

Result




cat data.txt

	

Displays the ROT13-encoded text.




cat data.txt \| tr 'A-Za-z' 'N-ZA-Mn-za-m'

	

Decodes the ROT13 text into readable text.

The tr command is commonly used in Linux for character translation, substitution, deletion, and transformation.

Terminal Output (Example)
bandit11@bandit:~$ pwd
/home/bandit11

bandit11@bandit:~$ ls
data.txt

bandit11@bandit:~$ cat data.txt
Gur cnffjbeq vf ...

bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is <next level password>

bandit11@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

user@ubuntu:~$ ssh bandit12@bandit.labs.overthewire.org -p 2220
bandit12@bandit.labs.overthewire.org's password:
bandit12@bandit:~$
Key Takeaways

Learned what the ROT13 cipher is.

Used the tr command for character translation.

Combined cat and tr using a pipe (|).

Retrieved the password for Bandit Level 12.

Logged into bandit12 using SSH from the Linux terminal.

Result

Successfully decoded the ROT13 text in data.txt, obtained the Bandit Level 12 password, and logged into the bandit12 account using the Linux terminal.
<img width="940" height="205" alt="image" src="https://github.com/user-attachments/assets/05cd8743-a39b-44b9-8b6f-fea0ecb46f6f" />
