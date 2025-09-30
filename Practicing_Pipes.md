#Practicing_Pipes

##Redirecting Output
To use ">" character to redirect output

###Solve:

**Flag** :pwn.college{gkmgaRfWEpMKNxxxOFZelDaF-JL.QX0YTN0wSMzkjNzEzW}

In this challenge I understood the use of ">" operator from example given and just implied its use here by redirecting the output of "echo PWN" to "COLLEGE" file 



```bash
Connected!

hacker@piping~redirecting-output:~$ echo PWN > COLLEGE

Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your

flag:

pwn.college{gkmgaRfWEpMKNxxxOFZelDaF-JL.QX0YTN0wSMzkjNzEzW} 
```

###Learnings: 
I learnt the use of ">" operator which helps helps us redirecting an output storing it in a file.

###References: 
None

## Redirecting more output
To use ">" character to redirect output from a command

###Solve:

**Flag** :pwn.college{kW2DRqTc-26bz8KStSp6UzB2fJE.QX1YTN0wSMzkjNzEzW}

I had already understood the use of ">" operator from previous question and just used it for command "/challenge/run" to redirect to "myflag" as given in challenge


```bash
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{kW2DRqTc-26bz8KStSp6UzB2fJE.QX1YTN0wSMzkjNzEzW}
```

###Learnings:
I learnt the use of ">" operator isn't just limited to echo but can be used for other commands as well
###References:
None

##Appending Output
To use ">>" character to append output

###Solve:

**Flag** :pwn.college{U5zOhf6nsiiquZ1qiQXrYNMHTth.QX3ATO0wSMzkjNzEzW}

In this challenge I understood the use of ">>" operator from example given and used it to append the "/home/hacker/the-flag" which contained the first half of flag to "/challenge/run" which contained the second half of the flag 


```bash
Connected!
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{U5zOhf6nsiiquZ1qiQXrYNMHTth.QX3ATO0wSMzkjNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in truncate mode (>)
rather than append mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
hacker@piping~appending-output:~$
```

###Learnings:
I learnt the use of ">>" operator which helps helps us append a redirected output. In this case,two halfs of flag
###References:
None

##Redirecting Errors
To redirect and save both output and error of given command.

###Solve:

**Flag**:pwn.college{wKzIJToN21yP0K1bJiXW_vVWpl6.QX3YTN0wSMzkjNzEzW}

In this challenge I understood the use of "2>" operator from example given to redirect errors. I already knew how to redirect output and using both knowledge I proceeded to solve.I redirected of specified command to "myflag" and errors(instructions here) to "instructions". Then rat cat function on instructions to ensure and finally ran cat on output for flag


```bash
Connected!
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{wKzIJToN21yP0K1bJiXW_vVWpl6.QX3YTN0wSMzkjNzEzW}

hacker@piping~redirecting-errors:~$```

###Learnings:
I learnt the use of a File Descriptor (FD) which is a number that describes a communication channel in Linux.
FD 0: Standard Input
FD 1: Standard Output
FD 2: Standard Error
How FD 1 is default but can be shifted with error by adding a prefix 2 like in this question
###References:
None

##Redirecting Input
To use "<" character to redirect input

###Solve:

**Flag** :pwn.college{0HCKIiJL24WueDM22hItXHpKcIH.QXwcTN0wSMzkjNzEzW}

In this challenge I understood the use of "<" operator from example given. I knw I had to first redirect "echo COLLEGE"'s output to PWN and then direct it as input for the specified function.


```bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{0HCKIiJL24WueDM22hItXHpKcIH.QXwcTN0wSMzkjNzEzW}
hacker@piping~redirecting-input:~$
```

###Learnings:
I learnt the use of "<" operator which helps helps us redirecting an input
###References:
None

##Grepping stored results
To use ">" character and grep together for rediecting output and finding it
###Solve:

**Flag** : pwn.college{8RKgq8SVHjX0nSdyZbUdkKl9fwf.QX4EDO0wSMzkjNzEzW}

In this challenge I already knew the use of ">" operator and grep. I needed to combine them for this challenge. First I redirected the output of specified command to "/tmp/data.txt" then I needed to explore it for flags for which I employed the grep function and entered the keyword "pwn.college" common to all flags.


```bash
Connected!
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{8RKgq8SVHjX0nSdyZbUdkKl9fwf.QX4EDO0wSMzkjNzEzW}
hacker@piping~grepping-stored-results:~$
```

###Learnings:
I soldified the learning of ">" and grep.
###References:
None

##Grepped live Output
To avoid storing results in a file and use "|" operator.

###Solve:

**Flag** : pwn.college{4xQ5mLmqjnVEQDAM-90j1-IxAaE.QX5EDO0wSMzkjNzEzW}

In this challenge I understood the use of "|" operator and piped the output of the specified command to input for grep command where like previous problem I passed "pwn.college" as argument for right results to be printed.


```bash
Connected!
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{4xQ5mLmqjnVEQDAM-90j1-IxAaE.QX5EDO0wSMzkjNzEzW}
hacker@piping~grepping-live-output:~$```

###Learnings:
I learnt the use of "|" operator how it convet the input of one command to another and avoids any use of middle man helping us solve the problem in a single line itself.
###References:
None

##Grepping Errors:
To use ">&" and grep errors via use of pipping operator

###Solve:

**Flag** : pwn.college{YJ8tGjGBoCiT_1cfFUc92zWzfLm.QX1ATO0wSMzkjNzEzW}

In this challenge I understood the use of ">&" from example given and I used it to convert error to output so it can feed through the pipping function. I converted the specified command's error to output and used pipping operator to pour as input for grep command where again I passed "pwn.college" as argument.


```bash
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{YJ8tGjGBoCiT_1cfFUc92zWzfLm.QX1ATO0wSMzkjNzEzW}
```

###Learnings:
I learnt the use of ">&" function which redirects a file descriptor to another hence I could redirect FD2 to FD1 and then use the pipping operator to feed the output as input for grep command

###References:
None

## Filtering with grep-v
To filter out using "grep -v"

###Solve:

**Flag** : pwn.college{EN12Vt0FhkPa3qxLIOaAmAeEhNs.0FOxEzNxwSMzkjNzEzW}

In this challenge I understood the use of "grep-v" command from example given and used it to filter out the word "DECOY" for finding thr flag


```bash
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{EN12Vt0FhkPa3qxLIOaAmAeEhNs.0FOxEzNxwSMzkjNzEzW}
```

###Learnings:
I learnt the use of "grep -v" command and how grep can't just be used to search required words but also filter out uncessary with option "-v"
###References:
None

##Duplicating piped data with tee
To use "tee" command to see data flow during piping

###Solve:

**Flag** : pwn.college{EHlZ-pJd7JxRbMcHAsxvTfzTLfE.QXxITO0wSMzkjNzEzW}

In this challenge I initially misunderstood the example and stupidly thought of using commands as files. Upon re-reading and analysing my mistake I enetered the required two command with tee piped in between for intercepting data flow and storing it in flag file after reading the cat file I got to know the secret code and intially thought that we needed to pass it as argument to "/challenge/college" which was wrong and upon inspecting realised I need to pipe both specified commands and pass secret code as argument to first function.


```bash
Connected!
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee /challenge/college
Processing...
You are trying to use 'tee' instead of /challenge/college. Use it between
/challenge/pwn and /challenge/college!
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee'
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee flag | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat flag
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "EHlZ-pJd"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/college secr
et EHlZ-pJ
/challenge/secret needs to the on the receiving end of the output of
'/challenge/pwn' (or 'tee' for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret EHlZ-pJd | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{EHlZ-pJd7JxRbMcHAsxvTfzTLfE.QXxITO0wSMzkjNzEzW}

```
###Learnings:
I learnt the use of "tee" function and how it saves a duplicate copy when piping happens so we can understand what actually is happening and can be handy to debug unidentified errors
###References:
None

## Process Substitution for input:
To use diff command and find difference between two commands

###Solve:

**Flag** :  pwn.college{w8osR98I0aHcMgDMSi2EX7X826A.0lNwMDOxwSMzkjNzEzW}

In this challenge I first understood the use of <(command) and then used it for sepcified commands to find the difference so that we can obtain the flag.


```bash
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
14a15
> pwn.college{w8osR98I0aHcMgDMSi2EX7X826A.0lNwMDOxwSMzkjNzEzW}
```

###Learnings:
I learnt the use of "<(command)" which makes command act like temorary files stored in named pipe enabling them to be used as arguments for diff command
###References:
https://linuxhandbook.com/bash-process-substitution/

##Writing to multiple programs
Duplicate the output of one command as input to two other commands

###Solve:

**Flag** :pwn.college{gkmgaRfWEpMKNxxxOFZelDaF-JL.QX0YTN0wSMzkjNzEzW}

In this challenge I knew I had to use piping operator as for giving output as inputs to two different commands. So converted the specified commands as temporary file by using >(/command) and joinined them by piping function so both could get input. "tee" is used to make copies and sent to files.


```bash
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/c
hallenge/planet) >(/challenge/the)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
2320223604285081165
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{wFVW1jGt1fpZPs4Vlb13KKc7u_X.QXwgDN1wSMzkjNzEzW}
hacker@piping~writing-to-multiple-programs:~$
```

###Learnings:
My concepts got solidified of "tee" and process substitution
###References:
None

##Split-piping stderr and stdout
To redirect stdout to one program and stderr to another
###Solve:

**Flag** :pwn.college{8oefb8S-MLqsnAd1gB_MUyc_fpI.QXxQDM2wSMzkjNzEzW}

In this challenge I knew I had to use both output and error (FD1 and FD2) of a command. I stored the error of the specified command in a temporary file ">(/challenge/the)" and on other hand sent it's output to "/challenge/planet" via piping operator. Since the redirection techniques was right I obtained the flag 


```bash
Connected!
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) | /challenge/planet
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{8oefb8S-MLqsnAd1gB_MUyc_fpI.QXxQDM2wSMzkjNzEzW}
```

###Learnings:
The use of standard output and error, along with piping and process substitution helped test my knowledge and understanding till now and I got revised with those concepts.
###References:
None

##Named Pipes
To create your own FIFO and redirect output of a specified function
###Solve:

**Flag** : pwn.college{0fV5KoJKlK1TJsPJMzmlyPahnbd.01MzMDOxwSMzkjNzEzW}

In this I first created my FIFO using "mkfifo" and then according to problem statement redirected the output of specified function to my newly created pipe. Now I had to switch terminal since FIFO's blocking behaviour when it is given input is written but output isn't read. I use cat function on another terminal to obtain the flag 


```bash
Terminal 1: 
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo

hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo!
Bash will now try to open the FIFO for writing, to pass it as the stdout of
/challenge/run. Recall that operations on FIFOs will block until both the
read side and the write side is open, so /challenge/run will not actually be
launched until you start reading from the FIFO!

Terminal 2: 
Connected!
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at
/tmp/flag_fifo! Here is your flag:
pwn.college{0fV5KoJKlK1TJsPJMzmlyPahnbd.01MzMDOxwSMzkjNzEzW}```

###Learnings:
I learnt the use of FIFO, it's usecase above files
No disk storage: FIFOs pass data directly between processes in memory - nothing is saved to disk
Ephemeral data: Once data is read from a FIFO, it's gone (unlike files where data persists)
Automatic synchronization: Writers block until the readers are ready, and vice-versa. This is actually useful! It provides automatic synchronization. Consider the example above: with a FIFO, it doesn't matter if cat myfifo or echo pwn > myfifo is executed first; each would just wait for the other. With files, you need to make sure to execute the writer before the reader.
Complex data flows: FIFOs are useful for facilitating complex data flows, merging and splitting data in flexible ways, and so on. For example, FIFOs support multiple readers and writers.

and how it blocks any operations on them until both the read side of the pipe and the write side of the pipe are ready.
###References:
None


