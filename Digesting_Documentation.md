# Digesting_Documentation

## Learning from documentation
This challenge was about finding the right command-line argument to make a program give up the flag by reading its documentation.

### Solve
**Flag:** pwn.college{4fYIgFzoN-XYrJtFScKOP0wqYC5.QX0ITO0wSMzkjNzEzW}

I needed to give the argument --giveflag to /challenge/challenge documentation as the question required me to do so.

```bash

hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{4fYIgFzoN-XYrJtFScKOP0wqYC5.QX0ITO0wSMzkjNzEzW}
```
### Learnings

I learnt what documentation is and how to specify it with arguments.

### References
none

# Digesting_Documentation

## Learning complex usage
This challenge was about reading documentation to understand how to use a command from the arguments.

### Solve
**Flag:** pwn.college{Q48HkrjH1JJZth9VTCoDHyfif9u.QX1ITO0wSMzkjNzEzW}

I saw an example of a "--printfile" argument so I used it to print the program's own description file. The documentation I got back told me that whatever path I gave to "--printfile" the program would try to read it. I first guessed the flag might be at "/challenge/FLAG.md" but that didn't work. I then remembered from other challenges that the flag is often just at "/flag". I tried that path with the "--printfile" argument and it worked.

```bash
Connected!
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /challenge/DESCRIPTION.md
Correct argument! Here is the /challenge/DESCRIPTION.md file:
While using most commands is straightforward, the usage of some commands can get quite complex.
For example, the arguments to commands like sed and awk, which we're definitely not getting into right now, are entire programs in an esoteric programming language!
Somewhere on the spectrum between cd and awk are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the find level in [Basic Commands](/linux-luminarium/commands).
find has a -name argument, and the -name argument itself takes an argument specifying the name to search for.
Many other commands are analogous.

Here is this level's documentation for /challenge/challenge:

> Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!

Given that documentation, go get the flag!
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /challenge/FLAG.md
Correct argument! Here is the /challenge/FLAG.md file:
cat: /challenge/FLAG.md: No such file or directory
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{Q48HkrjH1JJZth9VTCoDHyfif9u.QX1ITO0wSMzkjNzEzW}
hacker@man~learning-complex-usage:~$```

### Learnings
I learnt how differents commands have their own arguments and also the usecase of /flag here.

### References
None


## Reading manuals
To use the `man` command to read the manual page for a program.

### Solve
**Flag:** pwn.college{sGe2INSA4fc26LAZUS6y5puBK_T.QX0EDOO0wSMzkjNzEzW}

My first step was to read the manual for the challenge program itself as stated. The manual page opened up and described the program and its arguments. I found the flag I needed was "--sefcyp" and the value was "242". With that information I quit the man page and ran the program with the correct arguments which gave me the flag.

```bash
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --sefcyp 242
Correct usage! Your flag: pwn.college{sGe2INSA4fc26LAZUS6y5puBK_T.QX0EDO0wSMzkjNzEzW}
```

### Learnings
Understood the use of man commands

### References
None

## Searching manuals
This challenge required to search inside a long manual page to quickly find the information specified.

### Solve
**Flag:** pwn.college{8tdWqt98FOLhjVLXmKw9yAt9AKV.QX1EDO0wSMzkjNzEzW}

I opened the manual page but this time I needed to search instead of reading the whole thing. Once the manual was open I pressed the "/" key to search "flag". This jumped me right to the part of the manual that described the argument I needed which was "--fkbxz". I quit the manual page and tried to run the command but my first attempt failed because I forgot the space between the program name and the argument. I fixed the typo and ran it correctly which gave me the flag.

```bash
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge--fkbxz
bash: /challenge/challenge--fkbxz: No such file or directory
hacker@man~searching-manuals:~$ /challenge/challenge --fkbxz
Initializing...
Correct usage! Your flag: pwn.college{8tdWqt98FOLhjVLXmKw9yAt9AKV.QX1EDO0wSMzkjNzEzW}
```

###Learnings:
I learnt how to use the search in manual also how to move across results and direction of search (backwards/frontwards)

###References:
None

## Searching for manuals
This challenge was about finding the right manual page when the user isn't aware about the name of the command.

### Solve
**Flag:** pwn.college{MBKfSJDO26vAv0_Z1y3mZS2WiCS.QX2EDO0wSMzkjNzEzW}

My first move was to read the manual for "man". In there I learned about the "-k" flag and used to run "man -k challenge". This found a manual page with a weird name. Now that I had the real name I could read its manual. That manual gave me the final arguments I needed. I put it all together and ran the challenge program to get the flag.

```bash
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k challenge
fvvymiwzkj (1)         - print the flag!
hacker@man~searching-for-manuals:~$ man fvvymiwzkj
hacker@man~searching-for-manuals:~$ /challenge/challenge --fvvymi 260
Correct usage! Your flag: pwn.college{MBKfSJDO26vAv0_Z1y3mZS2WiCS.QX2EDO0wSMzkjNzEzW}
```
### Learnings
I learnt the use of man function even if we aren't aware of the real name of the command.It is a supe helpful tool to go across the all manuals of system and find and learn new functions.

### References
None

## Helpful programs
This challenge was about carefully reading a program's help message to find one option that would give the secret code for another option.

### Solve
**Flag:** pwn.college{UU9r4Mv7zdfJkyNmp37k8oRXFAt.QX3IDO0wSMzkjNzEzW}

My first step was to run "/challenge/challenge --help" to understand the program. I saw two options one to give flag with right secret value and another to get the secret value. I first printed the secret value and then used it to get the flag.

```bash
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v]
                                           [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option
                        to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 947
hacker@man~helpful-programs:~$ /challenge/challenge -g 947
Correct usage! Your flag: pwn.college{UU9r4Mv7zdfJkyNmp37k8oRXFAt.QX3IDO0wSMzkjNzEzW}
```
###Learnings:
Learnt the use of --help.

### References:
None

## Help for builtins
To get documentation for builtins.

### Solve
**Flag:** pwn.college{oiAYzDijcV9b22_gWgL-WxSq_F4.QX0ETO0wSMzkjNzEzW}

I started by running "help" as specified to see the list of available builtins and I saw "challenge" on that list. So I then ran "help challenge" to get specific info. The output was super clear it told me to use the secret flag and even gave me the secret value. My first few attempts to run the command failed because I was trying to use a path like /challenge/challenge. I then realized that since it's a builtin I just have to type its name and the final command worked.

```bash
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "oiAYzDij".
hacker@man~help-for-builtins:~$ /challenge/challenge --secret oiAYzDij
bash: /challenge/challenge: No such file or directory
hacker@man~help-for-builtins:~$ challenge --secret oiAYzDij
Correct! Here is your flag!
pwn.college{oiAYzDijcV9b22_gWgL-WxSq_F4.QX0ETO0wSMzkjNzEzW}
```
### Learnings:
I learnt the use of builtin functions and how to access it. Additionaly I learnt they need no paths and can directly be invoked

### References
None
