#Pondering_Path 

## The PATH Variable
The goal was to prevent a script from finding and using the `rm` command by clearing the `PATH` variable in the parent shell before running the script.

### Solve
**Flag:** `pwn.college{ggGcn1zqY56XQYbXCg0-L4zxgKw.QX2cDM1wSMzkjNzEzW}`

The `/challenge/run` script was designed to delete the flag by calling the `rm` command. To prevent this, I first cleared the `PATH` variable in my current shell by running the command `PATH=""`. After that, I executed `/challenge/run` and it was unable to find the `rm` executable, the deletion failed, and the script gave me the flag.

```bash
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{ggGcn1zqY56XQYbXCg0-L4zxgKw.QX2cDM1wSMzkjNzEzW}
```
###Learnings
I learnt how we cand define path ourselves and certain commands like ls and rm arenn't stored in directory but the path.

###References
None

## Setting PATH
The task was to set the `PATH` so that a script could find and run a command located in a non-standard directory.

### Solve
**Flag:** `pwn.college{k1ZKJxH-hh5m3yU81HKLlkySXWW.QX1cjM1wSMzkjNzEzW}`

The `/challenge/run` program needed to execute a command named `win`, but `win` was in a directory not listed in the default `PATH`. My first attempt to set the `PATH` variable using `PATH = /challenge/more_ commands` failed due to the spaces around the equals sign. I corrected this syntax error by running `PATH=/challenge/more_commands`, with no spaces. With the `PATH` correctly set, I was able to run `/challenge/run`, which could then find and execute `win`, giving me the flag.

```bash
hacker@path~setting-path:~$ PATH = /challenge/more_commands
bash: PATH: command not found
hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{k1ZKJxH-hh5m3yU81HKLlkySXWW.QX1cjM1wSMzkjNzEzW}
```
###Learnings
I learnt how to define paths of command as PATH and invoke them directly instead of changing directory or defining its paths again and again.
###References
None

## Finding Commands
This challenge introduced the `which` command to locate executables within the directories specified by the `$PATH` variable. The task was to find the location of a specific command (`win`) and then read a flag file located in that same directory.

### Solve
**Flag:** `pwn.college{khvKb68efMeDKgMMfL28CNs3h6u.01NzEzNxwSMzkjNzEzW}`

My first step was to use the `which win` command. This searched the `$PATH` and returned the full path to the executable: `/challenge/paths/7501/win`. Knowing the flag was in the same directory, I then used `cd /challenge/paths/7501` to navigate into that directory. Once inside, I was able to read the flag with `cat flag`.

```bash
hacker@path~finding-commands:~$ which win
/challenge/paths/7501/win
hacker@path~finding-commands:~$ cd /challenge/paths/7501
hacker@path~finding-commands:/challenge/paths/7501$ cat flag
pwn.college{khvKb68efMeDKgMMfL28CNs3h6u.01NzEzNxwSMzkjNzEzW}
```
###Learnings
I learnt how to define paths of unknown commands by using `which` that returns the path.
###References
None

## Adding Commands
The goal was to update the `PATH` in a way that my custom script could still find and use standard system commands like `cat`.

### Solve
**Flag:** `pwn.college{MfD-Xp9mBjQLtWq7tumZMD8wMWz.QX2cjM1wSMzkjNzEzW}`

My first step was to create a new directory for my scripts with `mkdir /home/hacker/my_ scripts`. Inside that directory, I created a file named `win` containing the command `cat /flag` and made it executable with `chmod a+x`.To ensure the shell could find my new `win` command while still being able to find `cat`, I prepended my new directory to the existing path using the command **`PATH=/home/hacker/my_scripts:$PATH`**. After setting this, I ran `/challenge/run`. It successfully found and executed my `win` script, which in turn was able to find and run `cat /flag` to print the flag.

```bash
hacker@path~adding-commands:~$ mkdir /home/hacker/my_scripts
hacker@path~adding-commands:~$ echo 'cat /flag' > /home/hacker/my_scripts/win
hacker@path~adding-commands:~$ chmod a+x /home/hacker/my_scripts/win
hacker@path~adding-commands:~$ PATH=/home/hacker/my_scripts:$PATH
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{MfD-Xp9mBjQLtWq7tumZMD8wMWz.QX2cjM1wSMzkjNzEzW}
```
###Learnings
I learned the standard method for adding a new directory to the command search path without losing access to existing commands. The syntax PATH=/new/directory:$PATH prepends a new directory to the PATH variable, causing the shell to search there first, while preserving all the original directories.
###References
None

## Hijacking Commands
The goal was to trick the `/challenge/run` program, which attempts to call the standard `rm` command, into running different rm.

### Solve
**Flag:** `pwn.college{4W3uMrqT_AopAgTaA4GeACxIDDZ.QX3cjM1wSMzkjNzEzW}`

First, I created a directory `/home/hacker/fake_bin` to hold my fake command. Inside this directory, I created a new script also named `rm`. Instead of deleting files, this script's only command was `cat /flag`. I then made my fake `rm` script executable with `chmod a+x`.

The most critical step was to prepend my directory to the `PATH` using the command **`PATH=/home/hacker/fake_bin:$PATH`. When I then ran `/challenge/run`, its attempt to execute `rm` found and ran my rm, which printed the flag.

```bash
hacker@path~hijacking-commands:~$ mkdir /home/hacker/fake_bin
hacker@path~hijacking-commands:~$ echo 'cat /flag' > /home/hacker/fake_bin/rm
hacker@path~hijacking-commands:~$ chmod a+x /home/hacker/fake_bin/rm
hacker@path~hijacking-commands:~$ PATH=/home/hacker/fake_bin:$PATH
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/fake_bin/rm. Executing!
pwn.college{4W3uMrqT_AopAgTaA4GeACxIDDZ.QX3cjM1wSMzkjNzEzW}
```

###Learnings
I learnt how we can hijack path and trick system into making run our copy of commands, hence diverting them from their usual route.

###References
None

