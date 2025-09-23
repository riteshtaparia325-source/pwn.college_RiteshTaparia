# Hello_Hackers

## Intro to Commands

In this challenge we are asked to open the terminal in dojo.pwn.college and invoke the hello command.
### Solve:
**Flag:** pwn.college{wVvjn9xj2AlAB__EcuKsvBQ_zO6.QX3YjM1wSMzkjNzEzW}

Here I got introduced to commands for first time and after seeing the example my thought process was to just write the command as stated in the question.

```bash
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{wVvjn9xj2AlAB__EcuKsvBQ_zO6.QX3YjM1wSMzkjNzEzW}
```

### Learnings:
I got to know how to invoke commands. Also that commands are case sensitive in linux and we need to carefully enter what we want.

### References:
None

##Intro to Arguments:

In this challenge we are asked to open the terminal in dojo.pwn.college and run the hello command with a single argument hackers.

### Solve:
**Flag:** pwn.college{QX22lKzb967bdq-cJDgZLp3TNeG.QX4YjM1wSMzkjNzEzW}

Here I knew my objective was to add a argument "Hackers" to command "Hello" which serves as additional data to the command. The first word while writing should have been the argument and the second the argument 

``` bash
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{QX22lKzb967bdq-cJDgZLp3TNeG.QX4YjM1wSMzkjNzEzW}
```

###Learnings:
I got to know arguments serve as additional data for command itself and a command can take any number of arguments.

###References:
None

##Command History

In this challenge we are asked to access history of every command we invoked till now

### Solve:
**Flag:** pwn.college{Aca2hz_nQfBuftdDVPDtiBh3zIW.0lNzEzNxwSMzkjNzEzW}

Here again I knew the use of arrow key would have allowed me to access the history of previous two commands I had practiced.We just needed to bring up the terminal and hit the up arrow key to see the commands used.

```bash

hacker@hello~command-history:~$ the flag is pwn.college{Aca2hz_nQfBuftdDVPDtiBh3zIW.0lNzEzNxwSMzkjNzEzW}
```
(Press up arrow key after bringing up terminal to get flag)
###Learnings: 
I learnt how to access previous given commands and check history which will specifically be useful when we give a long set of commands to the terminal and want to check it back.

### References:
None
