# Pondering_Paths

## The Root
To invoke a program in the launched dojo terminal

### Solve
**Flag:** pwn.college{MukNTU6aTxBWTVLuP52-vd7CUgV.QX4cTO0wSMzkjNzEzW}

In this program I was required to invoke the / directory in which pwn program existed. I just neended to invoke pwn by giving right path.


```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{MukNTU6aTxBWTVLuP52-vd7CUgV.QX4cTO0wSMzkjNzEzW}
```
### Learnings
I  got to know an absolute path is the style of path that starts with root directory. I also learnt how to invoke programs by mentioning the right paths

### Reference
None

## Program and absolute Paths
To invoke a program in launched dojo terminal

### Solve

** Flag: ** pwn.college{49cmVNxcuhEDel3xyqvnXreYgGC.QX1QTN0wSMzkjNzEzW}
In this program unlike previous the invoked program wasn't directly in root directory but in a challenge diractory. I needed to invoke the root then challenge first then the program name itself.

``` bash
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{49cmVNxcuhEDel3xyqvnXreYgGC.QX1QTN0wSMzkjNzEzW} ```

### Learnings
I got to learn that there can be a complex net of directories I need to invoke to reach my desired target and how to properly specify them for correct output.

###Reference
None

## Position thyself
To run challenge program by changing directory into specific path as mentioned by program.
### Solve:
Intially confused how program will tell me where to run, I tool help from some resources after that I learnt how invoking in root directory will tell me where to go, cd there and run the program 

** Flag: ** pwn.college{Q47ubcqPbS-gXzxUQ7HCrtpakQ7.QX2QTN0wSMzkjNzEzW} 

``` bash
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /sys directory.
Please use the cd utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /sys
hacker@paths~position-thy-self:/sys$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!

Here is your flag:
pwn.college{Q47ubcqPbS-gXzxUQ7HCrtpakQ7.QX2QTN0wSMzkjNzEzW}```

### Learnings
Got to know about the cd function and it's use, how to change directory and run program

### References
Gemini Ai (Just for understanding how the program will tell me which directory to go in.)

## Position Elsewhere
To change directory and run program.
### Solve:

** Flag: **: pwn.college{QmBKGnVLk62BYDIB455odFAZO89.QX3QTN0wSMzkjNzEzW}

Following the same steps to solve last intially did run the program for diectory and then "cd" into it and finally run the program 

hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /etc/apt/sources.list.d directory.
Please use the cd utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /etc/apt/sources.list.d
hacker@paths~position-elsewhere:/etc/apt/sources.list.d$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QmBKGnVLk62BYDIB455odFAZO89.QX3QTN0wSMzkjNzEzW}

### Learnings
Each process has a directory in which it's hanging out we need to cd to right directory to invoke the process. Additionally "~" shows the current path that our shell is located at. 
### References
None
## Position yet elsewhere
To change directory and run program.
### Solve
Just like the last two challenges need to find the right directory and cd to that and invoke the program.
** Flag: ** :pwn.college{ogqKd86SMNAH3kQB8PFh9dXaDf4.QX4QTN0wSMzkjNzEzW}

hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var directory.
Please use the cd utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /var
hacker@paths~position-yet-elsewhere:/var$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{ogqKd86SMNAH3kQB8PFh9dXaDf4.QX4QTN0wSMzkjNzEzW}

### Learnings:
We need to cd to right directory that can be anywhere in the system for effectively running our program.

### References
None

## Implicit relative paths from
To run a program by using relative path from root directory
### Solve:

** Flag: **pwn.college{s8wvOAa7rYbta2ZFgqYS6IBaEKL.QX5QTN0wSMzkjNzEzW}

We needed to cd to root directory and run program since we had to use relative path instead of absolute
Connected!
hacker@paths~implicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the cd utility to change directory appropriately.
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{s8wvOAa7rYbta2ZFgqYS6IBaEKL.QX5QTN0wSMzkjNzEzW}
hacker@paths~implicit-relative-paths-from-:/$

## Learnings
I learn the use of relative path and how it's different from absolute path since it depends on the directory we are in and with respect to that our path is determined
### References
None

## Explicit relative paths from /
To use . in relative paths

### Solve:

** Flag: ** pwn.college{YCKMHdfcWkjeWdSU2jUC2-3O7H3.QXwUTN0wSMzkjNzEzW}
Here just like previous question we needed to go to root directory but the use of relative path was not same. We need to make it more explicit by use of ".".

``` bash
Connected!
hacker@paths~explicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the cd utility to change directory appropriately.
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{YCKMHdfcWkjeWdSU2jUC2-3O7H3.QXwUTN0wSMzkjNzEzW} 
```
### Learnings
I learn the use of more explicit relative paths and how they differ from the naked relative paths we used earlier
### References
none

##Implicit relative Path
To explicitly use relative paths to launch run

### Solve: 
** flag: ** :pwn.college{oDTUY-HdExtBGMZsXZhNkP4Q_AF.QXxUTN0wSMzkjNzEzW} 
I needed to invoke the run path explicitly and cd to /challenge to run it the right way of using relative path 

``` bash
Connected!
hacker@paths~implicit-relative-path:~$ /challenge/run
Incorrect...
You are not currently in the /challenge directory.
Please use the cd utility to change directory appropriately.
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{oDTUY-HdExtBGMZsXZhNkP4Q_AF.QXxUTN0wSMzkjNzEzW}
```

### Learnings
I learnt how linux automatically avoids looking in current directory if we give a naked path and how "." now comes into use to execute the program
### References
None
## Home Sweet Home
To find the flag file with three contraints:
Your argument must be an absolute path.
The path must be inside your home directory.
Before expansion, your argument must be three characters or less.
### Solve: 
**Flag: ** :pwn.college{MRowPWZoPnlaroSlw7k6qEyJlxx.QXzMDO0wSMzkjNzEzW}

I needed to use absolute path hence no need to cd just could be invoked directly using "/", home directory and three constrains make use use ~ which specifies home directory and R is just a argument I gave. 

``` bash

Connected!
hacker@paths~home-sweet-home:~$ /challenge/run ~/R
Writing the file to /home/hacker/R!
... and reading it back to you:
pwn.college{MRowPWZoPnlaroSlw7k6qEyJlxx.QXzMDO0wSMzkjNzEzW}
```
### Learnings:
The use of ~ and how it can be used to specify paths in short
### References:
None
