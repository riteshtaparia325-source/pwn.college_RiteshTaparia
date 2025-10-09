## Launching screen
The task was simply to launch a new `screen` session to receive the flag.

### Solve
**Flag:** `pwn.college{08veld86RHx2TPALnXgmhm-Eph5.0VN4IDOxwSMzkjNzEzW}`

I just had to type the `screen` command and press Enter. This action launched a new virtual terminal session,clicked enter and the flag was immediately displayed. After noting the flag, I typed `exit` to close the `screen` session and return to my original shell.

```bash
hacker@terminal-multiplexing~launching-screen:~$ screen

# --- Inside the new screen session ---
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{08veld86RHx2TPALnXgmhm-Eph5.0VN4IDOxwSMzkjNzEzW}

# User types 'exit' here to leave the screen session
```
### Learnings
I learned the most basic functions of screen: how to start a new session by simply typing screen, and how to terminate the session and return to the original terminal by typing exit.
###References
None

## Detaching and Attaching
The task was to start a screen session, detach from it, have an external program send the flag to that session, and then reattach to view the flag.

### Solve
**Flag:** `pwn.college{o6wVlI15p8si2c8m7TDhnv_KiWd.0lN4IDOxwSMzkjNzEzW}`

First, I launched a new session with the `screen` command. Once inside, I detached by pressing the key combination `Ctrl-A` followed by `d`, which returned me to my original shell. From there, I ran the `/challenge/run` program, which detected my detached session and sent the flag to it. Finally, I reattached to the session using `screen -r`. Upon reattaching, I was able to see the flag.

```bash
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen

# User presses Ctrl-A then d inside the screen session to detach
[detached from 139.pts-0.terminal-multiplexing~detaching-and-attaching]

hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 139.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...
Flag sent! Now reattach to your screen session with: screen -r

hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r

# Upon reattaching, the flag is visible inside the screen session.
# The user echoes the flag in the main terminal to record it.
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{o6wVlI15p8si2c8m7TDhnv_KiWd.0lN4IDOxwSMzkjNzEzW}
Yes! Flag is: pwn.college{o6wVlI15p8si2c8m7TDhnv_KiWd.0lN4IDOxwSMzkjNzEzW}
```
### Learnings
I learned how to detach and reattach again to screen using commands like "Ctrl+A"+d and screen -r.

###References
None

## Finding Sessions
This challenge involved managing multiple detached `screen` sessions. With several sessions running simultaneously, the task was to list all of them and then systematically reattach to each one to find the session containing the flag.

### Solve
**Flag:** `pwn.college{cL0AxOLRoiRmpQ8JMMlcUqPLtgS.01N4IDOxwSMzkjNzEzW}`

My first step was to run `screen -ls`, which showed me three active, detached sessions. I then began checking them one by one. I used `screen -r 144` to attach to the first session, saw it was a decoy, and detached with `Ctrl-A d`. I did the same for the second session, `147` which revealed the flag.

```bash
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        144.session_ca9dc6e6a0888494    (Detached)
        147.session_9b9ce758856ca93c    (Detached)
        150.session_2b1c2de7fe029c4c    (Detached)
3 Sockets in /home/hacker/.screen.

# Checking the first session (decoy)
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 144
# User sees a decoy message and detaches with Ctrl-A d
[detached from 144.session_ca9dc6e6a0888494]

# Checking the second session (decoy)
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 147
# User sees another decoy and detaches with Ctrl-A d
[finds the flag]
# The user then echoes the flag in the main terminal to record it.
hacker@terminal-multiplexing~finding-sessions:~$ echo pwn.college{cL0AxOLRoiRmpQ8JMMlcUqPLtgS.01N4IDOxwSMzkjNzEzW}
pwn.college{cL0AxOLRoiRmpQ8JMMlcUqPLtgS.01N4IDOxwSMzkjNzEzW}
```

###Learnings
I learned how to manage multiple screen sessions. The key commands are screen -ls to list all existing sessions and screen -r <session_id> to reattach to a specific session by its name or process ID.
###References
None


## Switching Windows
This challenge introduced the concept of "windows" within a `screen` session, which are like having tabs in a single terminal. The task was to reattach to a pre-existing session and navigate between its windows to find the flag.

### Solve
**Flag:** `pwn.college{sC5Q2hgjW44aPFJ-II2XdTckp3W.0FO4IDOxwSMzkjNzEzW}`

First, I used `screen -ls` to find the correct session, which was `135.challenge_session`. I reattached to it using `screen -r 135`. This placed me in Window 1, where a message instructed me to switch to Window 0. I then used the keyboard shortcut `Ctrl-A` followed by `0` to switch to Window 0, where the flag was displayed.

```bash
hacker@terminal-multiplexing~switching-windows:~$ screen -ls
There are screens on:
        ...
144.session_ca9dc6e6a0888494    (Remote or dead)
        147.session_9b9ce758856ca93c    (Remote or dead)
        150.session_2b1c2de7fe029c4c    (Remote or dead)

        135.challenge_session   (Detached)
...

hacker@terminal-multiplexing~switching-windows:~$ screen -r 135

# --- Inside screen, the user lands in Window 1, which displays: ---
# Welcome to the window switching challenge!
# You are currently in window 1.
# The flag is hidden in window 0.
# Use Ctrl-A 0 to switch to window 0!

# User then presses Ctrl-A followed by 0.

# --- Inside screen, the user is now in Window 0, which displays: ---
# Excellent work! You found window 0!
# Here is your flag: pwn.college{sC5Q2hgjW44aPFJ-II2XdTckp3W.0FO4IDOxwSMzkjNzEzW}
```

###Learnings
It looks like you manually recorded the output from the screen session. I've reconstructed the steps for the documentation. Here is your solution in the copyable block format.

Markdown

## Switching Windows
This challenge introduced the concept of "windows" within a `screen` session, which are like having tabs in a single terminal. The task was to reattach to a pre-existing session and navigate between its windows to find the flag.

### Solve
**Flag:** `pwn.college{sC5Q2hgjW44aPFJ-II2XdTckp3W.0FO4IDOxwSMzkjNzEzW}`

First, I used `screen -ls` to find the correct session, which was `135.challenge_session`. I reattached to it using `screen -r 135`. This placed me in Window 1, where a message instructed me to switch to Window 0. I then used the keyboard shortcut **`Ctrl-A`** followed by **`0`** to switch to Window 0, where the flag was displayed.

```bash
hacker@terminal-multiplexing~switching-windows:~$ screen -ls
There are screens on:
        ...
        135.challenge_session   (Detached)
...

hacker@terminal-multiplexing~switching-windows:~$ screen -r 135

# --- Inside screen, the user lands in Window 1, which displays: ---
# Welcome to the window switching challenge!
# You are currently in window 1.
# The flag is hidden in window 0.
# Use Ctrl-A 0 to switch to window 0!

# User then presses Ctrl-A followed by 0.

# --- Inside screen, the user is now in Window 0, which displays: ---
# Excellent work! You found window 0!
# Here is your flag: pwn.college{sC5Q2hgjW44aPFJ-II2XdTckp3W.0FO4IDOxwSMzkjNzEzW}
```
###Learnings
I learned how to manage multiple windows within a screen session. The key is the Ctrl-A prefix for commands,different keyboard shortcuts, all starting with Ctrl-A:

Ctrl-A c - Create a new window
Ctrl-A n - Next window
Ctrl-A p - Previous window
Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
Ctrl-A " - bring up a selection menu of all of the windows 

###References
None


## Detaching and Attaching tmux
The task was to practice the detach-and-reattach workflow, but this time using the `tmux` commands.

### Solve
**Flag:** `pwn.college{ctkndPzpk2gJ-K-eqGek3S35a0T.0VO4IDOxwSMzkjNzEzW}`

First, I launched a new `tmux` session by simply typing `tmux`. Once inside, I detached from the session by pressing the key combination `Ctrl-B` and then `d`. This returned me to my original shell while leaving the `tmux` session running in the background. I then ran the `/challenge/run` program, which detected the detached session and sent the flag to it. Finally, I reattached using the shorthand command `tmux a`, where I was able to see the flag.

```bash
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux

# User presses Ctrl-B then d inside the tmux session to detach
[detached (from session 0)]

hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...
Flag sent! Now reattach to your tmux session with:
  tmux attach

hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a

# Upon reattaching, the flag is visible inside the tmux session.
# The user then echoes the flag in the main terminal to record it.
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ echo Congratulations, here is your flag: pwn.college{ctkndPzpk2gJ-K-eqGek3S35a0T.0VO4IDOxwSMzkjNzEzW}
Congratulations, here is your flag: pwn.college{ctkndPzpk2gJ-K-eqGek3S35a0T.0VO4IDOxwSMzkjNzEzW}
```

###Learnings
I learned the basic workflow for tmux. The key differences from screen are the prefix key, which is Ctrl-B by default, and the external commands. I practiced detaching with Ctrl-B d and reattaching with tmux a

###References
None

## Switching Windows tmux
The task was to reattach to a pre-existing session and use `tmux` keybindings to switch between its windows to find the flag.

### Solve
**Flag:** `pwn.college{EuWXwRxs1wN6QO_UkkGSK61sfBa.0FM5IDOxwSMzkjNzEzW}`

I first listed the active sessions with `tmux ls` to find the `challenge_session`. Then, I reattached to it using `tmux a`. This placed me in Window 1, where a message instructed me to switch to Window 0. I used the `tmux` keyboard shortcut `Ctrl-B` followed by `0` to switch to Window 0, where the flag was displayed.

```bash
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux ls
challenge_session: 2 windows (created Thu Oct  9 21:43:41 2025)

hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux a

# --- Inside tmux, the user lands in Window 1, which displays: ---
# Welcome to the tmux window switching challenge!
# You are currently in window 1.
# The flag is hidden in window 0.
# Use Ctrl-B 0 to switch to window 0!

# User then presses Ctrl-B followed by 0.

# --- Inside tmux, the user is now in Window 0, which displays: ---
# Excellent work! You found window 0!
# Here is your flag: pwn.college{EuWXwRxs1wN6QO_UkkGSK61sfBa.0FM5IDOxwSMzkjNzEzW}
```
###Learnings
I learned how to manage multiple windows within a tmux session. The key is the Ctrl-B prefix for all commands.he key combos are different, but the concept is the same:

Ctrl-B c - Create a new window
Ctrl-B n - Next window
Ctrl-B p - Previous window
Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9
Ctrl-B w - See a nice window picker


###References
None
