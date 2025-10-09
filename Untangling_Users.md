
# Untangling_Users

## Becoming root with su
This challenge required using the `su` command with the `root` user's password to start a root shell.

### Solve
**Flag:** `pwn.college{40JypnJW53U74RWnidP--HJ-0jK.QX1UDN1wSMzkjNzEzW}`

To gain root access I ran the `su` command and then  entered the password `hack-the-planet`. From this I was able to directly read the `/flag` file using `cat`.

```bash
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{40JypnJW53U74RWnidP--HJ-0jK.QX1UDN1wSMzkjNzEzW}
```
###Learnings
I learnt the use of su command
###Reference
None

## Other Users with su
To use the `su` command and a given password to log in as the user `zardus`.

### Solve
**Flag:** `pwn.college{Y_eLdRAuXX1CSjvioy3Awzqknjo.QX2UDN1wSMzkjNzEzW}`

To solve this, I used the command `su zardus`. The system then prompted me for a password, where I entered `dont-hack-me`. After I was successfully authenticated,I simply executed `/challenge/run` to receive the flag.

```bash
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{Y_eLdRAuXX1CSjvioy3Awzqknjo.QX2UDN1wSMzkjNzEzW}
```

###Learnings:
I learned how to use the su <username> command to switch to another user's account directly from my current terminal session, provided I have the correct password for that user.

###References:
None

## Cracking Passwords
To use the "John the Ripper" password cracking tool to find the plaintext password for the `zardus` user and then use it to gain access to their account.

### Solve
**Flag:** `pwn.college{YRLY196kakR_l3Uy4_xll7hNvCM.QX3UDN1wSMzkjNzEzW}`

My first step was to crack the password. I ran the command `john /challenge/shadow-leak`. After about 20 seconds, the tool successfully cracked the hash and revealed that the password for the `zardus` account was **aardvark**. I then used the `su zardus` command, entered `aardvark` when prompted, and successfully switched to the zardus user. From there, I executed `/challenge/run` to get the flag.

```bash
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04894g/s 285.0p/s 285.0c/s 285.0C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ 
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{YRLY196kakR_l3Uy4_xll7hNvCM.QX3UDN1wSMzkjNzEzW}
```
### Learnings:
I learned how to use a password cracking tool,john to perform an offline attack on a leaked password hash file.

### References:
None

# File Permissions and Ownership

## Using sudo
To read the root-owned `/flag` file by executing the `cat` command as the root user via sudo.

### Solve
**Flag:** `pwn.college{IRwzOBo7R6D3KT0z2QH-naHftlX.QX4UDN1wSMzkjNzEzW}`

Since `/flag` is owned by `root`, a normal `cat /flag` command would fail due to a lack of permissions. To overcome this, I prepended the command with `sudo`. The command `sudo cat /flag` executes `cat` with root privileges, allowing it to bypass the standard file permissions and successfully read the file's contents.

```bash
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{IRwzOBo7R6D3KT0z2QH-naHftlX.QX4UDN1wSMzkjNzEzW}
```
###Learnings
I learnt the use of sudo command.
