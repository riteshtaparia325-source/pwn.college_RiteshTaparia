#Comprehending_Commands

##Cat not the pet but the command
The goal of this challenge was to read the contents of a file named `flag` to reveal the solution.

### Solve
**Flag:** pwn.college{gJafU6ThApAUJFD5957bDs8MJQD.QXxcTN0wSMzkjNzEzW}

 I understood I needed the `cat` command to print the contents of this file directly to my terminal which successfully revealed the flag.

```bash
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{gJafU6ThApAUJFD5957bDs8MJQD.QXxcTN0wSMzkjNzEzW} ```

### Learnings:
I learnt how cat command helps us to read content of the files directly in the terminal.

### References: 
None

##Catting absolute paths
This challenge required using the cat command with an absolute path to find a file.

### Solve
**Flag:** pwn.college{48E2k4zT9YwLv-Ry859N4-t-okR.QX5ETO0wSMzkjNzEzW}

I figured the flag file probably wasn't in my current folder this time and tried absolute path `/flag`.

```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{48E2k4zT9YwLv-Ry859N4-t-okR.QX5ETO0wSMzkjNzEzW} ```

### Learnings
I learned that cat works with any path. It's not just for files in our current directory.We can give it an absolute path like /flag to read a file from anywhere on the system.

### References
None

## More catting practice
The goal of this challenge was to find the flag by its relative path.

### Solve
**Flag:** pwn.college{4rAEAasV70fuwxkDy4di1wZUrqF.QXwITO0wSMzkjNzEzW}

For this one I saw the given address of the file and knew I neede to cat directly through its absolute path since I couldn't cd. 

```bash
hacker@commands~more-catting-practice:~$ cat file /lib/systemd/ntp-units.d/flag
cat: file: No such file or directory 
pwn.college{4rAEAasV70fuwxkDy4di1wZUrqF.QXwITO0wSMzkjNzEzW}qF.
```
###Learnings:
I learnt without changing directory I can read using cat command by giving the absolute path of the function.

###References
None.

## Grepping for a needle in a haystack
This challenge was about finding a specific line of text the flag inside a big file.

### Solve
**Flag:** pwn.college{YFKp9qeU4KVAwSsyU8-YAjuK6mu.QX3EDO0wSMzkjNzEzW}

I had to use the grep command to search for flag. I know flags always start with pwn.college so I used grep to search for the text pwn.college.

```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{YFKp9qeU4KVAwSsyU8-YAjuK6mu.QX3EDO0wSMzkjNzEzW}
```

###Learnings
I learnt the use of grep that can help us find specific words when big lines of codes exists.

### References
None


## Comparing files
This challenge was all about comparing two different files to find difference.

### Solve
**Flag:** pwn.college{YconQrExNrKM8HL183IEudvxQND.01MwMDOxwSMzkjNzEzW}

I used the diff command to find difference betwwen two files given. The name gave away that the difference was the flag added to it. 

```bash
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
95a96
> pwn.college{YconQrExNrKM8HL183IEudvxQND.01MwMDOxwSMzkjNzEzW}
```

### Learnings: 
This challenge made me learn the use of diff command.

### References:
None


## Listing files
This challenge was about looking inside a directory to find the right program to run.

### Solve
**Flag:** pwn.college{oAWdK31d2hoTXZ6vuNsbldhdAdc.QX4IDO0wSMzkjNzEzW}

I knew challenge required me to look into /challenge using ls and saw two files one was a description and the other was a program with a long random-looking name. I figured that had to be the one to run. I executed it using its full path and it printed the flag.

```bash
hacker@commands~listing-files:~$ ls /challenge
28176-renamed-run-28477  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/28176-renamed-run-28477
Yahaha, you found me! Here is your flag:
pwn.college{oAWdK31d2hoTXZ6vuNsbldhdAdc.QX4IDO0wSMzkjNzEzW}
```
### Learnings:
I understood the use of ls command.
### References:
None

## Touching files
This challenge was about creating specific files in a certain directory that program was looking for before it would run successfully.

### Solve
**Flag:** pwn.college{Q6vKotuwR7bin52ofFe2wcmv687.QXwMDO0wSMzkjNzEzW}

I knew I had to use touch to create some files as specified before it would give me the flag. I knew they needed to be in the /tmp so I cd' into it. Then I used the touch command to create two empty files named pwn and college as specified. I ran ls to double check that the files were actually created. Once I saw them there I ran the /challenge/run for flag.

```bash
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ ls
bin  college  hsperfdata_root  pwn  tmp.4mK6TfTSUV
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{Q6vKotuwR7bin52ofFe2wcmv687.QXwMDO0wSMzkjNzEzW}
```

### Learnings:
I understood the use of touch command

### References
None


## Removing files
This challenge was to delete a specific file.

### Solve
**Flag:** pwn.college{MsINhThFe8rInf3EakI_nRostbe.QX2kDM1wSMzkjNzEzW}

I knew I needed to delete the specified file. The command to remove files is rm so I ran that. I used ls right after just to confirm that the file was really gone. After confirmation ran the /challenge/check program for the flag.

```bash
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ ls
R
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{MsINhThFe8rInf3EakI_nRostbe.QX2kDM1wSMzkjNzEzW}
```
### Learnings:
I learnt t use the rm command

### References
None

## Moving files
This challenge was about moving a file from a specific location to a new one.

### Solve
**Flag:** pwn.college{kyC6dVC0fMseKnXaco_IeP2T8_h.0VOxEzNxwSMzkjNzEzW}

The goal was to move the flag file from its original location to a new spot as specified. I used the command mv /argument to do this. After the command succeeded I ran `/challenge/check` which confirmed and gave the flag.

```bash
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{kyC6dVC0fMseKnXaco_IeP2T8_h.0VOxEzNxwSMzkjNzEzW}
```
### Learnings
I learnt using the mv function.
### References
None

## Hidden files
This challenge was about finding and reading a hidden file.

### Solve
**Flag:** pwn.college{0-UaATs_skuu3AoET5KWwygyCiy.QXwUDO0wSMzkjNzEzW}

I learnt hidden files start with a "." and to find them we use "ls -a" in root directory. I ran that function and spotted a hidden file with flag. I thought I needed to read it but realised the file was in the root directory not my current one and I needed an absolute path so with another try I succeded.

```bash
hacker@commands~hidden-files:~$ ls -a /
.                      bin        etc    lib64   nix   run   tmp
..                     boot       home   libx32  opt   sbin  usr
.dockerenv             challenge  lib    media   proc  srv   var
.flag-149641183519359  dev        lib32  mnt     root  sys
hacker@commands~hidden-files:~$ cat .flag-149641183519359
cat: .flag-149641183519359: No such file or directory
hacker@commands~hidden-files:~$ cat /.flag-149641183519359
pwn.college{0-UaATs_skuu3AoET5KWwygyCiy.QXwUDO0wSMzkjNzEzW}
```
### Learnings
I learnt how to find hidden files in linux and how they do look like. Addtionally I got revised abut the use of absolute path since I did a error there.

###References
None

## An epic filesystem quest
A long treasure hunt across the entire filesystem and required series of clues each one leading to the next to be followed and use different commands to overcome traps along the way.

### Solve
**Flag:** pwn.college{IjJfg4dfVKhwRsKnfXiQAVUNNTo.QX5IDO0wSMzkjNzEzW}

This was a multi-step journey that started with reading the "/LEAD" file. Each step gave me a new path and a hint about a "trap". I had to adapt my strategy for each clue.

* For normal clues I would just "cd" to the directory and "cat" the clue file.
* For **hidden** clues I had to use "ls -a" to find the hidden file (starting with a ".") before I could "cat" it.
* For **trapped** clues the hint said I couldn't "cd" into the directory. So I had to list the files from a distance using "ls" and giving its absolute path and then read the file with its full absolute path using cat.
* For the **delayed** clue I just had to "cd" into the directory to make the clue file appear.

I followed this pattern of reading the hint figuring out the trick and finding the next clue until I got to the very end. The final clue was a hidden file named ".TRACE".

```bash
Connected!
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
LEAD  challenge  flag  lib32   media  opt   run   sys  var
bin   dev        home  lib64   mnt    proc  sbin  tmp
boot  etc        lib   libx32  nix    root  srv   usr
hacker@commands~an-epic-filesystem-quest:/$ cat /lead
cat: /lead: No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ cat /LEAD
Tubular find!
The next clue is in: /opt/linux/linux-5.4/drivers/media/platform/meson

Watch out! The next clue is *trapped*. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/$ cat /LEAD/opt/linux/linux-5.
4/drivers/media/platform/meson
cat: /LEAD/opt/linux/linux-5.4/drivers/media/platform/meson: Not a directory
hacker@commands~an-epic-filesystem-quest:/$ ls /opt/linux/linux-5.4/drivers/media/platform/meson
EVIDENCE-TRAPPED  Makefile  ao-cec-g12a.c  ao-cec.c  built-in.a
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/linux/linux-5.4/drivers/media/platform/meson/EVIDENCE-TRAPPED
Tubular find!
The next clue is in: /usr/lib/R/library/base/R
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/lib/R/library/base/R
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/base/R$ ls
DOSSIER  Rprofile  base  base.rdb  base.rdx
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/base/R$ cat /DOSSIER
cat: /DOSSIER: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/base/R$ cat DOSSIER
Lucky listing!
The next clue is in: /usr/lib/python3/dist-packages/mpl_toolkits/tests/baseline_images/test_axisartist_floating_axes

The next clue is *delayed* --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/R/library/base/R$ cd /usr/lib/python3/dist-packages/mpl_toolkits/tests/baseline_images/test_axisartist_floating_axes
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/mpl_toolkits/tests/baseline_images/test_axisartist_floating_axes$ ls
MESSAGE  curvelinear3.png  curvelinear4.png
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/mpl_toolkits/tests/baseline_images/test_axisartist_floating_axes$ cat MESSAGE
Tubular find!
The next clue is in: /opt/linux/linux-5.4/drivers/staging/unisys

The next clue is *hidden* --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/mpl_toolkits/tests/baseline_images/test_axisartist_floating_axes$ cd  /opt/linux/linux-5.4/drivers/staging/unisys
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/unisys$ ls -a
.   .GIST          Kconfig      Makefile  include   visorinput
..  Documentation  MAINTAINERS  TODO      visorhba  visornic
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/unisys$ cat .GIST
Tubular find!
The next clue is in: /usr/lib/python3/dist-packages/scipy/build_utils/pycache_

Watch out! The next clue is *trapped*. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/unisys$ ls /usr/lib/python3/dist-packages/scipy/build_utils/pycache_
README-TRAPPED           _fortran.cpython-38.pyc
_init_.cpython-38.pyc  system_info.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/unisys$ cat /usr/lib/python3/dist-packages/scipy/build_utils/pycache_/README-TRAPPED
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/include/config/arch/supports/numa

The next clue is *hidden* --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/staging/unisys$ cd /opt/linux/linux-5.4/include/config/arch/supports/numa
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/config/arch/supports/numa$ ls -a
.  ..  .DISPATCH  balancing.h
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/config/arch/supports/numa$ cat .DISPATCH
Great sleuthing!
The next clue is in: /usr/share/icons/hicolor/96x96/stock/table

The next clue is *hidden* --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/config/arch/supports/numa$ cd /usr/share/icons/hicolor/96x96/stock/table
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/hicolor/96x96/stock/table$ ls -a
.  ..  .HINT
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/hicolor/96x96/stock/table$ cat .HINT
Congratulations, you found the clue!
The next clue is in: /usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/TeX/WinChrome

The next clue is *hidden* --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/hicolor/96x96/stock/table$ cd  /usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/TeX/WinChrome
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/TeX/WinChrome$ ls -a
.  ..  .TRACE  Regular
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/TeX/WinChrome$ cat .TRACE
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{IjJfg4dfVKhwRsKnfXiQAVUNNTo.QX5IDO0wSMzkjNzEzW}
hacker@commands~an-epic-filesystem-quest:/usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/TeX/WinChrome$
```

### Learnings
I got revised with all the functions learnt till now and got a much better understanding of their usecase

###References
None


## Making directories
This challenge required creating a new directory and then placing a specific file inside it before the challenge program would work.

### Solve
**Flag:** pwn.college{wDvglotnhlfGb53WP1_5GCqwgSC.QXxMDO0wSMzkjNzEzW}

I knew challenge required me to create a certain folder structure to exist. I did so using "mkdir". I started by using changing directory to specific location and create another directory named "pwn" after that again cd to "pwn" and created file "college" using touch. After that I ran "/challenge/run" for flag.

```bash
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ cd pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{wDvglotnhlfGb53WP1_5GCqwgSC.QXxMDO0wSMzkjNzEzW}
```

### Learnings:
I learnt the use of mkdir command

### References:
None

## Finding files
This challenge required searching the entire filesystem to find a file with a specific name.

### Solve
**Flag:** pwn.college{MAjts3Bl-N9ditfPbB_I4r2teDI.QXyMDO0wSMzkjNzEzW}

I needed to search the whole system for a file named flag so I started from the root directory /.After a lot of "Permission denied" it gave me a list of all the places it found a file or directory named "flag". I had to figure out which one was the right one. I tried the first path in the list but it turned out to be a directory. The second one I tried worked and gave me the flag.

```bash
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
... (many permission errors) ...
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/opt/linux/linux-5.4/tools/scripts/flag
... (more results) ...
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /opt/linux/linux-5.4/tools/scripts/flag
pwn.college{MAjts3Bl-N9ditfPbB_I4r2teDI.QXyMDO0wSMzkjNzEzW}
```

### Learnings:
I learnt the use of find command

### References:
None.

## Linking files
This challenge was about tricking a program by creating a symbolic link so that when it tried to read one file it was redirected to the real flag file.

### Solve
**Flag:** pwn.college{EgjpsQmDSwA6RmtKqObsTkVIbBg.QX5ETN1wSMzkjNzEzW}

I started by running the `/challenge/catflag` program to see what it did. It told me it was trying to `cat` a file that didn't exist.I knew the real flag was in `/flag`. My plan was to create a symbolic link that would point the path the program was looking for to the real flag.After creating the link I ran the challenge program again. This time it worked because the link pointed it to the correct file.

```bash
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
cat: /home/hacker/not-the-flag: No such file or directory
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{EgjpsQmDSwA6RmtKqObsTkVIbBg.QX5ETN1wSMzkjNzEzW}
```
### Learnings:
I learn about the use of links, both soft and hard. The usecase and how their working

### References:
https://youtu.be/m55AtwjBXpE?list=PL-ymxv0nOtqqRAz1x90vxNbhmSkeYxHVC 
This video helped me understand about links and its usecase.
