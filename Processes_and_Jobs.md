#Processes_and_Jobs

## Listing Processes
In this challenge, I had to find a running program whose name was randomized and directory was unlistable.

### Solve
**Flag:** `pwn.college{EFxTgaByMq8FDEDJdHnPQ999kdK.QX4MDO0wSMzkjNzEzW}`

Since I couldn't use `ls` to find the program, I checked the list of currently running processes. I used the command `ps -efww` to get a full, non-truncated list. By scanning the output, I found a process running from the `/challenge/` directory, which revealed its full name: `/challenge/21077-run-24241`. I then executed that file directly to get the flag.

```bash
hacker@processes~listing-processes:~$ ps -efww
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 12:49 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 12:49 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 12:49 ?        00:00:00 /challenge/21077-run-24241
...
hacker@processes~listing-processes:~$ /challenge/21077-run-24241
Yahaha, you found me! Here is your flag:
pwn.college{EFxTgaByMq8FDEDJdHnPQ999kdK.QX4MDO0wSMzkjNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```

###Learnings
I learnt the use of ps command. Adding arguments like -ef will help list every process(e) and in a full format(f). I can also use aux, to list processes for all users(a),to list processes that aren't running in a terminal(x), and for a "user-readable" output(u).To prevent it from truncating we can append it with w twice to disable the truncation. 

###References
https://www.computernetworkingnotes.com/linux-tutorials/ps-aux-command-and-ps-command-explained.html

## Killing Processes
This challenge required me to terminate a specific background process that was preventing the main challenge program from running.

### Solve
**Flag:** `pwn.college{EdI_zYPhUhU3_0JbZlCo2xO1qkt.QXyQDO0wSMzkjNzEzW}`

To solve this, I first needed to find the (PID) of the "/challenge/dont_ run "  program. I used the command "ps -ef | grep dont_ run"  to filter the process list for the one I needed. The output showed me its PID was `136`. After identifying the correct process, I used `kill 136` to terminate it. Once the `dont_run` then I  executed `/challenge/run` successfully to get the flag.

```bash
hacker@processes~killing-processes:~$ ps -ef | grep dont_run
hacker       136     135  0 12:54 ?        00:00:00 /challenge/dont_run
hacker       178     158  0 12:54 pts/0    00:00:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{EdI_zYPhUhU3_0JbZlCo2xO1qkt.QXyQDO0wSMzkjNzEzW}
```
###Learnings
I learnt the use of kill command to terminate a specific process using its PID.

###References
None

## Interrupting Processes
This challenge required  to stop a program that is actively running in the foreground of the terminal.

### Solve
**Flag:** `pwn.college{IJYS78OStkf_CuqS77z3Aj_UAaK.QXzQDO0wSMzkjNzEzW}`

I started the `/challenge/run` program, which then paused and waited without returning to the shell.I pressed "Ctrl+C " then`. This action sent an interrupt signal to the process, causing it to print the flag and terminate cleanly.

```bash
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{IJYS78OStkf_CuqS77z3Aj_UAaK.QXzQDO0wSMzkjNzEzW}
hacker@processes~interrupting-processes:~$
```
###Learnings
I learnt how to terminate a process that clogs the terminal using "ctrl+C"
###References
None

## Killing Misbehaving Processes
This challenge involved a decoy process that was continuously writing fake flags to a named pipe. I had to find and kill the decoy process.

### Solve
**Flag:** `pwn.college{ALWWyyfAUgESthO9ZvVsNPXGR4F.0FNzMDOxwSMzkjNzEzW}`

My process involved two terminals. In the first, I ran `cat /tmp/flag_fifo` to monitor the output. In the second, I used `ps -ef | grep decoy` to find the PID of the interfering process which was `142` and used  `kill 142`. After the decoy was stopped, I ran `/challenge/run` in the second terminal. This allowed it to write the correct flag to the pipe, which then appeared in my first terminal.

```bash
# --- In Terminal 1 ---
hacker@...$ cat /tmp/flag_fifo
... (a stream of decoy flags appears) ...

# --- In Terminal 2 ---
hacker@processes~killing-misbehaving-processes:~$ ps -ef | grep decoy
root         139       1  0 13:01 ?        00:00:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
hacker       142     139  0 13:01 ?        00:00:01 /usr/bin/python /challenge/decoy
hacker       176     166  0 13:04 pts/1    00:00:00 grep --color=auto decoy
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!

# --- Real flag appears in Terminal 1 ---
pwn.college{ALWWyyfAUgESthO9ZvVsNPXGR4F.0FNzMDOxwSMzkjNzEzW}
```
###Learnings
I learnt how to terminate a process using two terminals as used earlier and kill the decoy process to obtain real flag
###References
None

# Processes

## Suspending Processes
This challenge required two instances of the same program to be running in the same terminal simultaneously.

### Solve
**Flag:** `pwn.college{oEWUWbaSjXOp3ySliCos4orW2Dq.QX1QDO0wSMzkjNzEzW}`

I launched `/challenge/run` for the first time. When it paused, I pressed `Ctrl-Z` to suspend it and send it to the background. The shell  gave me back my prompt. With the first process suspended but still technically running, I launched `/challenge/run` a second time. This new instance was able to print the flag.

```bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID           PID    PPID  C STIME TTY          TIME CMD
root          155     135  0 13:08 pts/0    00:00:00 bash /challenge/run
root          157     155  0 13:08 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID           PID    PPID  C STIME TTY          TIME CMD
root          155     135  0 13:08 pts/0    00:00:00 bash /challenge/run
root          162     135  0 13:09 pts/0    00:00:00 bash /challenge/run
root          164     162  0 13:09 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{oEWUWbaSjXOp3ySliCos4orW2Dq.QX1QDO0wSMzkjNzEzW}
```
###Learnings
I learnt how to suspend a process using "Ctrl+Z" and send it to background
###References
None

## Resuming Processes
This task required me to bring suspended process back to the foreground using the `fg` command.

### Solve
**Flag:** `pwn.college{cISpz44naINXk9w4H3PKXIBpAt2.QX2QDO0wSMzkjNzEzW}`

I first executed `/challenge/run`. When the program prompted me, I suspended it by pressing `Ctrl-Z`.I then typed the `fg` command and hit Enter. This brought the suspended program back to the foreground, allowing it to resume execution and print the flag.

```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{cISpz44naINXk9w4H3PKXIBpAt2.QX2QDO0wSMzkjNzEzW}
Don't forget to press Enter to quit me!
```
###Learnings
I learned how to use the fg (foreground) command to resume the most recently suspended job.

###References
None

## Backgrounding Processes
The challenge required a second copy of itself to be actively *running* in the background, not just suspended.

### Solve
**Flag:** `pwn.college{8JkHQYjcPkywgXZdnLmP98uKGke.QX3QDO0wSMzkjNzEzW}`

I started by running `/challenge/run` and then suspended it using `Ctrl-Z`.I used the `bg` command to resume it in the background.With the first instance actively running in the background, I launched `/challenge/run` and got the flag.

```bash
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID           PID STAT CMD
root          153 S+   bash /challenge/run
root          155 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.

hacker@processes~backgrounding-processes:~$
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID           PID STAT CMD
root          153 S    bash /challenge/run
root          163 S    sleep 6h
root          164 S+   bash /challenge/run
root          166 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{8JkHQYjcPkywgXZdnLmP98uKGke.QX3QDO0wSMzkjNzEzW}
```
###Learnings                                                           
I learned how to use the bg (background) command to resume the most recent suspended job and let it run in background. I also learned how to inspect the detailed status of processes using ps -o stat. A process suspended with Ctrl-Z has a T status. After resuming it with bg, its status changes to S (sleeping/waiting), which shows it's active but not suspended. A process actively running in the foreground has a status of R                                                                     


###References                                             
None

## Foregrounding Processes
This challenge required to bring an actively running background process back into the foreground.

### Solve
**Flag:** `pwn.college{I6gRBsT4yBhcC77ztsadaryBeil.QX4QDO0wSMzkjNzEzW}`

First I ran `/challenge/run` and immediately suspended it with `Ctrl-Z`. Second I used the `bg` command to make the suspended process start running again,but in the background. Finally with the process actively running in the background,I used the `fg` command. This brought the process back into the foreground,which completed the challenge and printed the flag.

```bash
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{I6gRBsT4yBhcC77ztsadaryBeil.QX4QDO0wSMzkjNzEzW}
```
###Learnings
I learned that the fg command is versatile. It not only resumes a suspended process but can also be used to take an actively running background process and bring it back to the foreground

###References
None

## Starting Backgrounded Processes
This challenge required running a program in the background. Instead of the suspend/resume cycle directly as a background job from the start.

### Solve
**Flag:** `pwn.college{ofLdDn8cf78YGmBhpnvv-pOWy4k.QX5QDO0wSMzkjNzEzW}`

I needed to append an ampersand (`&`) to the end of the `/challenge/run` command. The shell immediately started the process in the background and returned my prompt and printed the flag.

```bash
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 153
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{ofLdDn8cf78YGmBhpnvv-pOWy4k.QX5QDO0wSMzkjNzEzW}

[1]+  Done                    /challenge/run
```

###Learnings
I learned that appending an ampersand (&) to a command is a simple and direct shortcut to launch it as a background job. This is more efficient than manually using Ctrl-Z and bg for tasks that I know from the start should not occupy the foreground.

###References
None

## Process Exit Codes
This challenge required to run one program that would exit with an error, capture that specific exit code and then pass it as an argument to a second program.

### Solve
**Flag:** `pwn.college{QMOadnqH-HbvlTElTRAobeh0Vyv.QX5YDO1wSMzkjNzEzW}`

First I ran `/challenge/get-code`, which I knew would terminate with a specific non-zero exit code. Immediately after that command finished, I ran `/challenge/submit-code` and provided `$?` as the argument. The shell automatically substituted `$?` with the numerical exit code from the `get-code` command, which solved the challenge.

```bash
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ /challenge/submit-code $?
CORRECT! Here is your flag:
pwn.college{QMOadnqH-HbvlTElTRAobeh0Vyv.QX5YDO1wSMzkjNzEzW}
```
###Learnings
I learned about shell exit codes where 0 typically means success and 1  means failure and how to access the exit code of the most recently executed command using the special $? variable.
###References
None
