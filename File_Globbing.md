# File_Globbing

## Matching with *
To use `*` wildcard to match directory names.

### Solve
**Flag:** pwn.college{kTXDDrsGIi6OPxVTe3L9KKEbgXp.QXxIDO0wSMzkjNzEzW}

The goal was to change into the /challenge directory using a wildcard. I knew that the " * " character in bash is a wildcard that can match any string of characters.I typed "cd /c*" hoping the shell would find the /challenge directory for me. After that I just had to run the `/challenge/run` program to get the flag.

```bash
hacker@globbing~matching-with-:~$ cd /c*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{kTXDDrsGIi6OPxVTe3L9KKEbgXp.QXxIDO0wSMzkjNzEzW}
```
### Learnings
I learnt the use of wildcard "*" and it's use to match sequence of characters

### Reference
None

## Matching with ?
To use `?` wildcard to match exactly one character in ile globbing.

### Solve
**Flag:** pwn.college{wF1v_eNJGruzI2uA-V2NT07aX.QXyIDO0wSMzkjNzEzW}

This time I had to get into the `/challenge` directory using the `?` wildcard. I know that `?` matches any single character so I constructed a pattern that would uniquely match the target directory. The pattern I used was `/?ha??enge`. This worked because the first `?` matched the `c` the `??` matched the two `l`s and the last `?` matched the final `e`. The shell expanded this pattern and moved me into the `/challenge` directory. After that running `/challenge/run` gave me the flag.

```bash
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{wF1v_eNJGruzI2uA-V2NT07aX.QXyIDO0wSMzkjNzEzW}
```
###Learnings
I learnt about "?" wildcard and how its different from "*" as it just replaces one character unlike the latter one.
### References
None


## Matching with []
To use square brackets `[]` for globbing.

### Solve
**Flag:** pwn.college{gIlvkRmima4JAsDbrBh6uTDvq4a.QXzIDO0wSMzkjNzEzW}

For this challenge I had to use character sets. I first changed into the "/challenge/files" directory as directed. I needed to provide a filename to the "/challenge/run" program. The square brackets "[absh]" tell the shell to match any one character from that set. The shell found the correct file that matched this pattern passed it to the program and I got the flag.

```bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{gIlvkRmima4JAsDbrBh6uTDvq4a.QXzIDO0wSMzkjNzEzW}
	```
###Learnings
I learnt how a set of unique character which replaces just one character at a time can be used using [] wildcard.

### References:
None

## Matching paths with []
To globb a pattern as part of a full file path instead of just on a filename in the current directory.

### Solve
**Flag:** pwn.college{032r2e8Mr1Dd93w59K1m7ERMhvL.QX0IDO0wSMzkjNzEzW}

This time instead of first changing directories I realized I could probably use the file path. I combined the path to the files "/challenge/files/" with the character set pattern "file_[absh]" from the last challenge. I gave this full path pattern to the "/challenge/run" program. The shell correctly expanded the wildcard in the path to find the right file and the program gave me the flag.

```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[absh]
You got it! Here is your flag!
pwn.college{032r2e8Mr1Dd93w59K1m7ERMhvL.QX0IDO0wSMzkjNzEzW}
```

### Learnings:
I learnt how we could just globb with right path and use the wild card
### References:
None
 
## Multiple Globs
To find any file containing a specific character.

### Solve
**Flag:** pwn.college{MxhyB4fvb_EUbXb-j8H_gkd5Mf5.0lM3kjNxwSMzkjNzEzW}

I needed to find the right file to pass as an argument. I used the  "*p*". This pattern tells the shell to look for any filename that has the letter 'p' anywhere in it. The shell expanded this wildcard to the correct filename, passed it to the `/challenge/run` program, and I got the flag.

```bash
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{MxhyB4fvb_EUbXb-j8H_gkd5Mf5.0lM3kjNxwSMzkjNzEzW}
```
### Learnings
I learnt I can use globbing to find any file containing that character by using that pattern creatively

### References
None

## Mixing globs
To combine different wildcards to create a more powerful and specific pattern to find the right file.

### Solve
**Flag:** pwn.college{USYGfWjjr9X-qsfKF8NfYNL41FD.QX1IDO0wSMzkjNzEzW}

I was in the "/challenge/files" directory and needed to find the correct file to pass to the program. I used the pattern "[cep]* ".The shell found the file that matched this pattern passed it to the `/challenge/run` program and I got the flag.

```bash
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{USYGfWjjr9X-qsfKF8NfYNL41FD.QX1IDO0wSMzkjNzEzW}
```
###Learnings
I learnt that I can combine different wildcards and create a pattern for very precise search

### References
None

## Exclusionary globbing
To use exclusionary globbing to match files that don't start with a specific set of characters.

### Solve
**Flag:** pwn.college{oMqd4G_XNH-bB1kaT4mQZqRxkiI.QX2IDO0wSMzkjNzEzW}

I figured I needed to exclude files from my search pattern.I used the pattern "[!pwn]* ".,The shell found the file that fit this rule, passed it to the `/challenge/run` program, and I got the flag.

```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{oMqd4G_XNH-bB1kaT4mQZqRxkiI.QX2IDO0wSMzkjNzEzW}
```
#Learnings
I learnt how we could also exclude certain set of characters we don't want to search using "!" and "^" in newer versions

## Tab completion
This challenge was about using the Tab key to auto-complete a filename.

### Solve
**Flag:** pwn.college{IZ216r1jSgnVyzO-98lqifFnPvy.0FN0EzNxwSMzkjNzEzW}

I knew I needed to use the Tab key. I first ran ls /challenge to see the files available. To read it I started typing cat command which gave me an error and then I wrote again and hit Tab which auto-completed the rest of the filename.

```bash
hacker@globbing~tab-completion:~$ ls /challenge
DESCRIPTION.md  pwncollege
hacker@globbing~tab-completion:~$ cat/challenge/pwncollege
bash: cat/challenge/pwncollege: No such file or directory
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege 
pwn.college{IZ216r1jSgnVyzO-98lqifFnPvy.0FN0EzNxwSMzkjNzEzW}
```

###Learnings:
I learnt the use of tab key to aut-complete without typos.
### References:
None 

## Multiple options for tab completion
Use Tab to complete and find the correct file.

### Solve
**Flag:** pwn.college{8OY7fhTVJauhv4Gsn5guOuvdlPa.0lN0EzNxwSMzkjNzEzW}

My goal was to find and read the flag file using the Tab key to help me. I started typing the path and when I got to "/challenge/files/pwncollege-fla" and hit Tab, the shell showed me two possible completions I knew the correct file was "pwncollege-flag". My first thought was to `cd` into it, but that failed because it's a file not a directory. I then realized I just needed to read it, so I used `cat` with the full path, which printed the flag.

```bash
hacker@globbing~multiple-options-for-tab-completion:~$ cd /challenge/files/pwncollege-fla
pwncollege-flag     pwncollege-flamingo
hacker@globbing~multiple-options-for-tab-completion:~$ cd /challenge/files/pwncollege-flag
bash: cd: /challenge/files/pwncollege-flag: Not a directory
hacker@globbing~multiple-options-for-tab-completion:~$ cat  /challenge/files/pwncollege-flag
pwn.college{8OY7fhTVJauhv4Gsn5guOuvdlPa.0lN0EzNxwSMzkjNzEzW}

```
###Learnings
I learnt how to use tab key if multiple functions start with same character

###References
None

## Tab completion on commands
This challenge was about using **Tab completion** to find and execute a command with a long name, not just a file path.

### Solve
**Flag:** pwn.college{AFpm8X_Kdx26rXJJOIZJta3-b4k.0VN0EzNxwSMzkjNzEzW}

I figured there was a program with a long name that I needed to run. I started by typing pwncollege and pressed tab. The shell then auto-completed the full command name. Once the full command was typed out I just hit Enter and it gave me the flag.

```bash
hacker@globbing~tab-completion-on-commands:~$ pwncollege-25845
Correct! Here is your flag:
pwn.college{AFpm8X_Kdx26rXJJOIZJta3-b4k.0VN0EzNxwSMzkjNzEzW}
```
### Learnings
Not just files tab could be used for commands as well

### References
None
