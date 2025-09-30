#Shell_Variables

##Printing Variables
To print using "echo"

###Solve:
**Flag:** pwn.college{0Z7pWnzrHP4D6HA-9D0Ypp9doUc.QX3UTN0wSMzkjNzEzW}

Just like the example I came to understand that echo prints the flag and $ is added before flag to make it act as variable.

``` bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{0Z7pWnzrHP4D6HA-9D0Ypp9doUc.QX3UTN0wSMzkjNzEzW}
```
###Learnings:
I learnt the use of echo and "$" one prints the value and other when prepending it to variable name
###References:
None

##Setting Variables
To set a value to variable using "="

###Solve:
**Flag:** pwn.college{w3eSual-nrYdWpQsI2amSEINm0M.QX5UTN0wSMzkjNzEzW}

Just like the example I came to learn how to assign value and by using "=" assigned "COLLEGE" to "PWN"

``` bash
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{w3eSual-nrYdWpQsI2amSEINm0M.QX5UTN0wSMzkjNzEzW}
```
###Learnings:
I learnt the use of "=" as an assigning operator to variables. Also, the fact that space(" ") plays a vital role and there shouls be no spaces while assigning.

##Multi-word Variables
To print using spaces(" ") as a single token. 

###Solve:
**Flag:** pwn.college{4iPQS7Jnb7MXd3mI_uXQSs4QEoG.QXwYTN0wSMzkjNzEzW}

I knew how spaces play a role an to contain them quotes("") could be used.
 
``` bash
Connected!
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{4iPQS7Jnb7MXd3mI_uXQSs4QEoG.QXwYTN0wSMzkjNzEzW}
```
###Learnings:
I learnt the use of "" and how it can solve the problem of spaces while assignment.
###References:
None

##Exporting Variables
To export variable to another shell

###Solve:
**Flag:** pwn.college{0Z7pWnzrHP4D6HA-9D0Ypp9doUc.QX3UTN0wSMzkjNzEzW}

As asked in the question I assigned value "COLLEGE" to "PWN" and exported it, after that assigned "PWN" to "COLLEGE" but didn't export it. and then ran the specified command to get the flag
``` bash
Connected!
hacker@variables~exporting-variables:~$ PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{4SJwHTe_sJlpVgzc1omA0ANUf6c.QXyYTN0wSMzkjNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```
###Learnings:
I learnt that how by default, variables that you set in a shell session are local to that shell process and we need to export them to different shells if we are employing their use.

###References
None

##Printing Exported Variables
To print using "env"

###Solve:
**Flag:** pwn.college{wrNHf6g04-OJmIDzbvAom3K75bK.QX4UTN0wSMzkjNzEzW}

Just like the example I came to understand that env prints the exported variable and in the drop down list I found the flag.
``` bash
Connected!
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=f7489921d1da30f80f18a5d7614b07ed71cbaad70dd29cf5a74b3c3a3c193374
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{wrNHf6g04-OJmIDzbvAom3K75bK.QX4UTN0wSMzkjNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env```
###Learnings:
I learnt the use of env and how it prints every exported variable set in our shell.
###References:None

##Sorting Command Output
To store output of command directly into variable

###Solve:
**Flag:** pwn.college{kBgPXHvrZFSHTV8_zz9zDuHlNIU.QX1cDN1wSMzkjNzEzW}

I used the command substitution for assigning the specified command output directly to the variable "PWN" and got the flag
``` bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{kBgPXHvrZFSHTV8_zz9zDuHlNIU.QX1cDN1wSMzkjNzEzW}```
###Learnings:
I learnt the use of command substitution. Additionally in older versions even `command` could be used for command substitution.

###References
None


##Reading input
To use "read" and assign value to variable

###Solve:
**Flag:** pwn.college{0Z7pWnzrHP4D6HA-9D0Ypp9doUc.QX3UTN0wSMzkjNzEzW}

I used the read built-in command variable PWN and manually entered its value "COLLEGE"
``` bash
Connected!
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{UMCgWfdunOrJ8lkxEUx396ouRHQ.QX4cTN0wSMzkjNzEzW}
```
###Learnings:
I learnt the use of read

###References:
None


##Reading Files
To read a file into variable

###Solve:
**Flag:** pwn.college{w3Ye5Gm11n4Ejrg7skb1-7AEO2H.QXwIDO0wSMzkjNzEzW}

I used read for PWN variable and directed it's input through "/challenge/read_me" 
``` bash
Connected!
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{w3Ye5Gm11n4Ejrg7skb1-7AEO2H.QXwIDO0wSMzkjNzEzW}```
###Learnings:
I learnt how I can direct input to a variable saving us time we would have  otherwise doe in 3 steps using cat command.

###References:
None

##Printing Variables
To print using "echo"

###Solve:
**Flag:** pwn.college{0Z7pWnzrHP4D6HA-9D0Ypp9doUc.QX3UTN0wSMzkjNzEzW}

Just like the example I came to understand that echo prints the flag and $ i>
``` bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{0Z7pWnzrHP4D6HA-9D0Ypp9doUc.QX3UTN0wSMzkjNzEzW}
```
###Learnings:
I learnt the use of echo and "$" one prints the value and other when prepend>###References:
None
