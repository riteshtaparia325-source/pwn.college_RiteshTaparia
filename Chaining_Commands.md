#Chanining_Commands

## Chaining with Semicolons
To use a semicolon (`;`) and execute two commands in same line.

### Solve
**Flag:** `pwn.college{kQoltpyVFeIzg2UK1Qj0_B0G3v9.QX1UDO0wSMzkjNzEzW}`

 I placed a semicolon between the two specified commands on one line: `/challenge/pwn ; /challenge/college` and got the flag
.

```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{kQoltpyVFeIzg2UK1Qj0_B0G3v9.QX1UDO0wSMzkjNzEzW}
```
### Learnings
I learned that the semicolon (;) can be used to separate multiple commands on a single line.

###References
None

## Building on Success
The task was to run a second program, but only if the first program executed successfully.

### Solve
**Flag:** `pwn.college{QUrogQjUAUjtWWOMDxnU1n9kUP0.0lM0MDOxwSMzkjNzEzW}`

My initial attempts to run the programs separately failed. The correct solution was to link them with the `&&` operator. The command `/challenge/first-success && /challenge/second` satisfied the challenge's condition and printed the flag.

```bash
hacker@chaining~building-on-success:~$ /challenge/first-success
hacker@chaining~building-on-success:~$ /challenge/second
Error: /challenge/first-success must be successfully chained with
/challenge/second using &&
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{QUrogQjUAUjtWWOMDxnU1n9kUP0.0lM0MDOxwSMzkjNzEzW}
```

###Learnings
I learned how to use the && (AND) operator to create conditional command chains. This operator executes the command on its right only if the command on its left succeeds

###References
None


## Handling Failure
The task was to run a second program only if the first program failed.

### Solve
**Flag:** `pwn.college{wBPnhhImgWD8tPcHWbxPOtjaNuV.01M0MDOxwSMzkjNzEzW}`

The challenge required `/challenge/second` to run only after `/challenge/first-failure` returned an error. I used the `/challenge/first-failure || /challenge/second`, which  satisfied the condition and produced the flag.

```bash
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{wBPnhhImgWD8tPcHWbxPOtjaNuV.01M0MDOxwSMzkjNzEzW}
```
###Learnings
I learned how to use the || (OR) operator to create conditional command chains based on failure. It executes the command on its right only if the command on its left fails
###References
None

## Your First Shell Script
The task was to place a sequence of two commands into a file named `x.sh` and then execute that file as a script.

### Solve
**Flag:** `pwn.college{8XFopgRywZ-hrOe54CV1m9scXCA.QXxcDO0wSMzkjNzEzW}`

I created the script file directly from the command line using `echo` and output redirection. First, I ran `echo "/challenge/pwn" > x.sh` to create the file and write the first command into it. Then, I used `echo "/challenge/college" >> x.sh` to append the second command to the file on a new line.Finally, I executed the script with `bash x.sh`, which ran the commands in order and produced the flag.

```bash
hacker@chaining~your-first-shell-script:~$ echo "/challenge/pwn" > x.sh
hacker@chaining~your-first-shell-script:~$ echo "/challenge/college" >> x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{8XFopgRywZ-hrOe54CV1m9scXCA.QXxcDO0wSMzkjNzEzW}
```
###Learnings
I learned the basic principle of a shell script: a text file containing a sequence of commands that the shell can execute. I also practiced a useful technique for creating simple scripts directly on the command line using echo with > (overwrite/create) and >> (append) redirection operators.

###References
None

## Redirecting Script Output
The task was to create a script that runs two commands, and then pipe the combined standard output of the entire script into a third, "solver" command.

### Solve
**Flag:** `pwn.college{AhVDERq2ltXW9mRcAJZZ82xbRgv.QX4ETO0wSMzkjNzEzW}`

My first step was to create a script named `script.sh` that contained the commands `/challenge/pwn` and `/challenge/college` on separate lines. I did this using `echo` and output redirection. Once the script was created, I executed it and piped its entire output stream into the solver program using the command `bash script.sh | /challenge/solve` printed the flag.

```bash
hacker@chaining~redirecting-script-output:~$ echo "/challenge/pwn" > script.sh
hacker@chaining~redirecting-script-output:~$ echo "/challenge/college" >> script.sh
hacker@chaining~redirecting-script-output:~$ bash script.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{AhVDERq2ltXW9mRcAJZZ82xbRgv.QX4ETO0wSMzkjNzEzW}

```
###Learnings
I learned that the standard output of an entire shell script (which is the concatenated output of all commands within it) can be piped (|) or redirected (>) just like a single command.
###References
None

## Executable Shell Scripts
The challenge involved creating the script file and then execute it.

### Solve
**Flag:** `pwn.college{MsqDdEt5P595ndcYBAfmvq2Te5e.QX0cjM1wSMzkjNzEzW}`

First I created the script `solve.sh` using the command `echo "/challenge/solve" > solve.sh`. My initial attempt to run it with `./solve.sh` failed with a "Permission denied" error, as expected. After confirming with `ls -l` that the file lacked execute permissions, I ran `chmod a+x solve.sh` to add them. Once the script was made executable, running `./solve.sh` again worked correctly and printed the flag.

```bash
hacker@chaining~executable-shell-scripts:~$ echo "/challenge/solve" > solve.sh
hacker@chaining~executable-shell-scripts:~$ ./solve.sh
bash: ./solve.sh: Permission denied
hacker@chaining~executable-shell-scripts:~$ ls -l ./solve.sh
-rw-r--r-- 1 hacker hacker 17 Oct  9 20:04 ./solve.sh
hacker@chaining~executable-shell-scripts:~$ chmod a+x solve.sh
hacker@chaining~executable-shell-scripts:~$ ./solve.sh
Congratulations on your shell script execution! Your flag:
pwn.college{MsqDdEt5P595ndcYBAfmvq2Te5e.QX0cjM1wSMzkjNzEzW}
```

###Learnings
I learned how ro exectute file as command and also that for a shell script to be run directly as a command (e.g., ./script.sh), the file itself must have the execute (x) permission. This is different from running it with bash script.sh, where bash is the executable and the script is just a file that bash reads for instructions.
###References
None

## Understanding Shebangs
The task was to create a proper shell script, complete with a shebang line, make it executable, and then run a separate program to verify its correctness.

### Solve
**Flag:** `pwn.college{8QqfZh0emX7gGvM5QktU1cE_gj_.0VOzMDOxwSMzkjNzEzW}`

I built the script `solve.sh` in my home directory using `echo` and redirection. The first, crucial step was to add the shebang line. Next, I appended the required command. After creating the script, I made it executable using `chmod a+x /home/hacker/solve.sh`. Finally, I ran the `/challenge/run` program, which successfully tested my script and provided the flag.

```bash
hacker@chaining~understanding-shebangs:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ echo 'echo "hack the planet"' >> /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ chmod a+x /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{8QqfZh0emX7gGvM5QktU1cE_gj_.0VOzMDOxwSMzkjNzEzW}
```
###Learnings
I learned about the importance and syntax of the shebang (#!/path/to/interpreter). This must be the very first line in a script, and it tells the Linux kernel which program (like /bin/bash or /usr/bin/python3) to use to execute the contents of the file. This makes a script self-contained and runnable by any process, not just an interactive shell.
###References
None

## Scripting with Arguments
The task was to create a shell script that takes two arguments and outputs them in reverse order.

### Solve
**Flag:** `pwn.college{EEAfrRnJtp2ggC_PVtDPvq2ASGL.0VNzMDOxwSMzkjNzEzW}`

I created a script named `solve.sh` in my home directory, starting with the  shebang. To access the command-line arguments, I used the special positional variables `$1` for the first argument and `$2` for the second. The core logic of the script was the command `echo "$2 $1"`, which prints the second argument followed by the first. After making the script executable with `chmod`, I ran the `/challenge/run` program, which verified that my script worked correctly and gave me the flag.

```bash
hacker@chaining~scripting-with-arguments:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ echo 'echo "$2 $1"' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ chmod a+x /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{EEAfrRnJtp2ggC_PVtDPvq2ASGL.0VNzMDOxwSMzkjNzEzW}
	```
###Learnings
I learned how to access command-line arguments passed to a shell script by using the positional parameters: $1 for the first argument, $2 for the second, and so on.
###References
None

## Scripting with Conditionals
This challenge introduced conditional logic in shell scripts using the `if` statement. The task was to create a script that would check its input argument and perform an action only if the argument matched a specific string.

### Solve
**Flag:** `pwn.college{4nFHY6Ws7yWeDYjZzlyHaKuS0b8.0lNzMDOxwSMzkjNzEzW}`

I built the `solve.sh` script line-by-line using `echo` and the append redirector (`>>`). Then the if condition appened. This condition checks if the first command-line argument is exactly equal to the string "pwn". If the condition was true, the script would `echo "college"`. I closed the conditional block with `fi`. After making the script executable, I ran the `/challenge/run` verifier, which confirmed the logic was correct.

```bash
hacker@chaining~scripting-with-conditionals:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'if [ "$1" == "pwn" ]; then' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'echo "college"' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'fi' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ chmod a+x /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{4nFHY6Ws7yWeDYjZzlyHaKuS0b8.0lNzMDOxwSMzkjNzEzW}
```

###Learnings
I learned the basic syntax for an if statement in bash: if [ condition ] ; then ... fi also the use of ";" since "if","then" and "fi" must be in seperate line,also that spacing must be after "if", "[", "]" This allows a script to make decisions and execute code conditionally based on criteria, such as comparing an input argument to a string.

###References
None

## Scripting with Default Cases
The task was to create a script that provides one output for a specific input ("pwn") and a different, default output ("nope") for all other inputs.

### Solve
**Flag:** `pwn.college{QDQD6wtkphJ2obPQAXrZ62xYxUX.01NzMDOxwSMzkjNzEzW}`

I constructed the `solve.sh` script by appending each line with `echo` and `>>`. I created an `if` statement to check if the first argument was equal to "pwn". Immediately following that, I added an `else` block to handle all other possibilities. The script would `echo "college"` if the condition was true, and `echo "nope"` otherwise. After closing the block with `fi` and making the script executable, the `/challenge/run` verifier confirmed that the logic handled both cases correctly.

```bash
hacker@chaining~scripting-with-default-cases:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'if [ "$1" == "pwn" ]; then' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'echo "college"' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'else' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'echo "nope"' >>/home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'fi' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ chmod a+x /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$  /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{QDQD6wtkphJ2obPQAXrZ62xYxUX.01NzMDOxwSMzkjNzEzW}
```
###Learnings
I learned the basic syntax for an if-else statement and how else can be used to print if input is anything other than what satisfies if. 
###References
None

## Scripting with Multiple Conditions
The task was to create a script that could check for three different specific inputs and provide a unique output for each, as well as a default output for any other input.

### Solve
**Flag:** `pwn.college{sTrVOzKWpLe2CmNoCdRqoV7uXd0.0FOzMDOxwSMzkjNzEzW}`

I built the `solve.sh` script line by line. I started with an `if` statement for the first condition ("hack"). I then used two `elif` statements to handle the subsequent conditions ("pwn" and "learn"). Finally, I added an `else` block to provide the default "unknown" output. The entire structure was enclosed by the initial `if` and the final `fi`. After making the script executable, the `/challenge/run` verifier confirmed that all conditions were handled correctly.

```bash
hacker@chaining~scripting-with-multiple-conditions:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$  echo 'if [ "$1" == "hack" ]; then' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'echo "the planet"' >>/home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$  echo 'elif [ "$1" == "pwn" ];then'  >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$  echo 'echo "college"' >>/home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$  echo 'elif [ "$1" == "learn" ];then'  >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$  echo 'echo "linux"' >>/home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'else' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'echo "unknown"' >>/home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'fi' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ chmod a+x /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{sTrVOzKWpLe2CmNoCdRqoV7uXd0.0FOzMDOxwSMzkjNzEzW}
```

###Learnings
I learned the basic syntax for an if-elif-else statement and how different conditions be given using elif.
###References
None

## Reading Shell Scripts
The task was to find a password that was stored inside the script itself, and then use that password to get the flag.

### Solve
**Flag:** `pwn.college{sNF6fRBIXKT8UXb_QwPSrwgQ-fi.0lMwgDOxwSMzkjNzEzW}`

My first step was to find the password. I used the command `cat /challenge/run` to print the script's source code to my terminal. By reading the code, I found an `if` statement that was comparing my input to the string `"hack the PLANET"`. This was the password. I then ran `/challenge/run`, and when it prompted for input, I typed `hack the PLANET` and pressed Enter, which revealed the flag.

```bash
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{sNF6fRBIXKT8UXb_QwPSrwgQ-fi.0lMwgDOxwSMzkjNzEzW}
```

###Learnings
I learnt that Reading the source code is a powerful technique for understanding exactly how a program works and can often reveal its secrets.

###References
None

