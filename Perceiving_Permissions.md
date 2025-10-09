## Changing File Ownership
To change ownership to root and read the specified file.

### Solve
**Flag:** `pwn.college{gdvsM0_evgeL14O8OCbxR2WdsgT.QXxEjN0wSMzkjNzEzW}`

My process was to first confirm I couldn't read the flag,which gave me a "Permission denied" error. I then used the command `chown hacker /flag` to change the owner of the `/flag` file from `root` to my user `hacker`. Then I ran `cat /flag` again to get the flag.

```bash
hacker@users~file-ownership:~$ cat /flag
cat: /flag: Permission denied
hacker@users~file-ownership:~$ chown hacker /flag
hacker@users~file-ownership:~$ cat /flag
pwn.college{gdvsM0_evgeL14O8OCbxR2WdsgT.QXxEjN0wSMzkjNzEzW}
```

###Learnings
I learned about the direct relationship between file ownership and access permissions in Linux. Specifically, I learned how to use the" chown" command to change a file's owner

###References
None

## Groups and Files
To change the file's group to one that I belonged to thereby gaining the necessary permissions to read it.

### Solve
**Flag:** `pwn.college{sHaH8KsbAu77neIDLFQsfHSv2mx.QXxcjM1wSMzkjNzEzW}`

To solve this, I used the `chgrp`command to change the group ownership of the `/flag` file. By running `chgrp hacker /flag`, I set the file's group to `hacker`.I was then able to successfully use `cat /flag` to display the flag.

```bash
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{sHaH8KsbAu77neIDLFQsfHSv2mx.QXxcjM1wSMzkjNzEzW}
```

###Learnings
I learned how group ownership is used to manage file access for multiple users. Specifically, I learned how to use the "chgrp" command to change the group associated with a file

###References
None

## Fun with Groups Names
To use 'id' command to now the group nameand then  with `chgrp` to gain read access to the `/flag` file.

### Solve
**Flag:** `pwn.college{ETd5xICW_NILtqY5vWalLGctlxs.QXycjM1wSMzkjNzEzW}`

My first step was to run the `id` command to figure out what groups I belonged to. Once I had the correct group name, I ran `chgrp grp5758 /flag` to change the file's group ownership. I was then able to use `cat /flag` to view the flag.

```bash
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp5758) groups=1000(grp5758)
hacker@permissions~fun-with-groups-names:~$ chgrp grp5758 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{ETd5xICW_NILtqY5vWalLGctlxs.QXycjM1wSMzkjNzEzW}
```

###Learnings
I learned how to use the id command to identify a user's UID (user ID), primary GID (group ID), and all group memberships.

###References
None

## Changing Permissions
The `/flag` file was owned by `root` with permissions that only allowed root to read it. My task was to use the special privileges granted for this challenge to modify the file's permissions and make it readable for my user.

### Solve
**Flag:** `pwn.college{8-LK1rO8M2EwHm42c_PwzNgiJ0-.QXzcjM1wSMzkjNzEzW}`

To gain access to the flag, I needed to add read permissions to it. I used the command **`chmod a+r /flag`**. This command uses symbolic notation where it makes it readable(r)for all users(a).After running this command, the file became world-readable, and I was able to view its contents with `cat /flag`.

```bash
hacker@permissions~changing-permissions:~$ chmod a+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{8-LK1rO8M2EwHm42c_PwzNgiJ0-.QXzcjM1wSMzkjNzEzW}
```

###Learnings:
I learned about the basic structure of Linux file permissions—the three sets of read (r), write (w), and execute (x) permissions for the user, group, and other(a fo all). I also learned how to modify these permissions using the chmod command with symbolic notation (e.g., a+r, u-w, g+x).
###References
None


## Executable Files
 The `/challenge/run` program was initially un-runnable because it lacked the necessary execute permissions. The goal was to use `chmod` to make the file executable and then run it to get the flag.

### Solve
**Flag:** `pwn.college{QjJ6dGeG2SwiKkkL8nhyKJLJBh2.QXyEjN0wSMzkjNzEzW}`

I first checked the file's permissions with `ls -l /challenge/run` and confirmed that the execute bit was not set for anyone. To fix this, I ran the command **`chmod a+x /challenge/run`**, which **adds (`+`)** **execute (`x`)** permission for **all (`a`)** users. After the permissions were updated, I was able to run `/challenge/run` and it printed the flag.

```bash
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r--r-- 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ chmod a+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{QjJ6dGeG2SwiKkkL8nhyKJLJBh2.QXyEjN0wSMzkjNzEzW}
```
###Learnings
I learned that for a file to be executed as a program, it must have the execute (x) permission bit set. Without this permission, the shell will refuse to run the file, even if it contains valid executable code. Using chmod +x is the standard way to make scripts and programs runnable.
### References
none

## Permission Tweaking Practice
The challenge required correctly modifying the permissions of a file eight times in a row using symbolic notation.

### Solve
**Flag:** `pwn.college{kNK9ISBWL__kMipZGi7MI4PPMPc.QXwEjN0wSMzkjNzEzW}`

This was an eight-round challenge where I had to adjust file permissions step-by-step. In each round, I carefully compared the "Current permissions" with the "Needed permissions" and formulated the correct `chmod` command to make the change. This involved adding and removing read, write, and execute permissions for the user, group, and other.

After successfully completing all eight rounds, the `/flag` file became modifiable. It started with no permissions (`---------`), so I ran **`chmod a+r /flag`** to make it readable and then used `cat` to get the final flag.

```bash
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-r--rw-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+w /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": rw-r--rw-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw----rw-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g-r /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": rw----rw-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-----rw-
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$  chmod u-w /challenge
/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": r-----rw-
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-----r--
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$  chmod o-w /challenge
/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": r-----r--
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r----xr-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$  chmod go+x /challeng
e/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": r----xr-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -----xr-x
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$  chmod u-r /challenge
/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": -----xr-x
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ------r--
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$  chmod go-x /challeng
e/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": ------r--
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-x---r-x
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$  chmod u+rx,o+x /chal
lenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod a+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{kNK9ISBWL__kMipZGi7MI4PPMPc.QXwEjN0wSMzkjNzEzW}
hacker@permissions~permission-tweaking-practice:~$
```
###Learnings
This challenge solidified my understanding of chmod's symbolic notation. I practiced adding (+) and removing (-) permissions for the user (u), group (g), and other (o). I also learned that you can apply multiple changes in a single command by separating them with a comma (e.g., chmod u+rx,o+x).
###References 
Used AI (just for knowing how to give imply two changes simultaneously in chmmod command which I learnt was using a comma)

## Permissions Setting Practice
This challenge was an advanced version of the previous `chmod` exercise. Instead of adding or subtracting permissions, this one required **setting them absolutely** using the `=` operator. I had to pass eight rounds of correctly setting the permissions for the user, group, and other, often in a single command, to unlock the final flag.

### Solve
**Flag:** `pwn.college{s6rkUGWxxqeCFyvNXsRyhBeib1s.QXzETO0wSMzkjNzEzW}`

This was an eight-round challenge where I had to set permissions to an exact state. For each round, I analyzed the required `rwx` string (e.g., `rw-r-x-wx`) and constructed a full `chmod` command using the `=` operator and comma-separated clauses to match it. For example, to get `rw-r-x-wx`, the command was **`chmod u=rw,g=rx,o=wx`**.

After successfully passing all eight rounds, I was able to modify the `/flag` file. I used **`chmod a+r /flag`** to make it readable and then used `cat` to view the flag.

```bash
Connected!
hacker@permissions~permissions-setting-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-r-x-wx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rw,g=rx,o=wx /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": rw-r-x-wx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -w----r--
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$  chmod u=w,g=-,o=r /c
hallenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": -w----r--
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ------rwx
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$  chmod u=-,g=-,o=rwx
/challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": ------rwx
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r-x-w-r--
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$  chmod u=rx,g=w,o=r /
challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": r-x-w-r--
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ------r-x
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$  chmod u=-,g=-,o=rx /
challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": ------r-x
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r-x-w-r--
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$  chmod u=rx,g=w,o=r /
challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": r-x-w-r--
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": --xr--r-x
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$  chmod u=x,g=r,o=rx /
challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": --xr--r-x
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -wx-w-r--
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$  chmod u=wx,g=w,o=r /
challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod a+r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{s6rkUGWxxqeCFyvNXsRyhBeib1s.QXzETO0wSMzkjNzEzW}
hacker@permissions~permissions-setting-practice:~$

```
###Learnings
I learned the advanced usage of chmod with the = operator to set permissions absolutely, overwriting any previous permissions. The key takeaway was the powerful and readable syntax of chaining rules with a comma (e.g., chmod u=rx,g=r,o=-) to define a file's entire permission state in a single command.
###References
none

## The SUID Bit
The task was to apply SUID(s) to an executable file owned by `root`.

### Solve
**Flag:** `pwn.college{krIQetWBYfkHP0y8iVkKm9HW-xk.QXzEjN0wSMzkjNzEzW}`

My goal was to make the `/challenge/getroot` program run as its owner, `root`. To do this, I first had to set the SUID bit on the file using the command `chmod u+s /challenge/getroot`. After setting this permission, I executed the program. Because of the SUID bit, the program launched with root privileges and gave me a root shell (indicated by the `#` prompt). From this new privileged shell, I was able to read the protected `/flag` file.

```bash
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{krIQetWBYfkHP0y8iVkKm9HW-xk.QXzEjN0wSMzkjNzEzW}
```
###Learnings
I learned about the SUID (Set User ID) permission and how to set it using chmod u+s. This special permission bit, when applied to an executable file, allows the program to run with the privileges of the file's owner, not the user who is executing it.

###References
none
