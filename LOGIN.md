
# SSH Login Format for Bandit (Linux Terminal)

## Level 0 Login

Open the Linux terminal and connect using:

Bash

```
user@ubuntu:~$ ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Password

```
bandit0
```

Successful Login Prompt

Bash

```
bandit0@bandit:~$
```

## Levels 1 to 33 Login

For every subsequent Bandit level, use the same SSH command by replacing `n` with the level number.

Syntax

Bash

```
user@ubuntu:~$ ssh banditn@bandit.labs.overthewire.org -p 2220
```

Where `n` = 1 to 33.

### Examples

Bash

```
user@ubuntu:~$ ssh bandit1@bandit.labs.overthewire.org -p 2220
```

Bash

```
user@ubuntu:~$ ssh bandit5@bandit.labs.overthewire.org -p 2220
```

Bash

```
user@ubuntu:~$ ssh bandit16@bandit.labs.overthewire.org -p 2220
```

Bash

```
user@ubuntu:~$ ssh bandit33@bandit.labs.overthewire.org -p 2220
```

After entering the correct password for that level, you will see:

Bash

```
banditn@bandit:~$
```

where `n` is the level you logged into.

> Use this SSH format for all Bandit levels (1–33) in your Linux-based walkthroughs.
