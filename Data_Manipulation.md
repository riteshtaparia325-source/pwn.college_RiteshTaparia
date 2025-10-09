# Data_Manipulation

## Translating Characters
The challenge required me to fix a flag where the letter casing was swapped using the `tr` command.

### Solve
**Flag:** `pwn.college{smA5uGCf3gDKu4ywh3dgmswkpBS.01MxEzNxwSMzkjNzEzW}`

To solve this, I first ran the program `/challenge/run` to see the output. Then,I used '--help 'command to see how I can convert whole uppercase and lower case after that I piped that output directly into the `tr` command.I then piped the output of "/challenge./run" to tr 'A-Za-z' 'a-zA-Z' to  translate all lowercase letters to uppercase and vice versa.

```bash
hacker@data~translating-characters:~$ /challenge/run
Your case-swapped flag:
PWN.COLLEGE{SMa5UgcF3GdkU4YWH3DGMSWKPbs.01mXeZnXWsmZKJnZeZw}

hacker@data~translating-characters:~$ tr --help
Usage: tr [OPTION]... STRING1 [STRING2]
Translate, squeeze, and/or delete characters from standard input,
writing to standard output.  STRING1 and STRING2 specify arrays of
characters ARRAY1 and ARRAY2 that control the action.

  -c, -C, --complement    use the complement of ARRAY1
  -d, --delete            delete characters in ARRAY1, do not translate
  -s, --squeeze-repeats   replace each sequence of a repeated character
                            that is listed in the last specified ARRAY,
                            with a single occurrence of that character
  -t, --truncate-set1     first truncate ARRAY1 to length of ARRAY2
      --help        display this help and exit
      --version     output version information and exit

ARRAYs are specified as strings of characters.  Most represent themselves.
Interpreted sequences are:

  \NNN            character with octal value NNN (1 to 3 octal digits)
  \\              backslash
  \a              audible BEL
  \b              backspace
  \f              form feed
  \n              new line
  \r              return
  \t              horizontal tab
  \v              vertical tab
  CHAR1-CHAR2     all characters from CHAR1 to CHAR2 in ascending order
  [CHAR*]         in ARRAY2, copies of CHAR until length of ARRAY1
  [CHAR*REPEAT]   REPEAT copies of CHAR, REPEAT octal if starting with 0
  [:alnum:]       all letters and digits
  [:alpha:]       all letters
  [:blank:]       all horizontal whitespace
  [:cntrl:]       all control characters
  [:digit:]       all digits
  [:graph:]       all printable characters, not including space
  [:lower:]       all lower case letters
  [:print:]       all printable characters, including space
  [:punct:]       all punctuation characters
  [:space:]       all horizontal or vertical whitespace
  [:upper:]       all upper case letters
  [:xdigit:]      all hexadecimal digits
  [=CHAR=]        all characters which are equivalent to CHAR

Translation occurs if -d is not given and both STRING1 and STRING2 appear.
-t is only significant when translating.  ARRAY2 is extended to length of
ARRAY1 by repeating its last character as necessary.  Excess characters
of ARRAY2 are ignored.  Character classes expand in unspecified order;
while translating, [:lower:] and [:upper:] may be used in pairs to
specify case conversion.  Squeezing occurs after translation or deletion.

GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
Report any translation bugs to <https://translationproject.org/team/>
Full documentation <https://www.gnu.org/software/coreutils/tr>
or available locally via: info '(coreutils) tr invocation'
hacker@data~translating-characters:~$ /challenge/run | tr 'A-Za-z' 'a-zA-Z'
yOUR CASE-SWAPPED FLAG:
pwn.college{smA5uGCf3gDKu4ywh3dgmswkpBS.01MxEzNxwSMzkjNzEzW}

'''
###Learnings
I learned how to use tr to perform a complete case swap of character streams by mapping two character ranges simultaneously.

###References
None

## Deleting Characters
In this challenge, I had to remove specific decoy characters from the output of a program.

### Solve
**Flag:** `pwn.college{swBiTYmfyuu-aKtqDivf0WTA09f.0FNxEzNxwSMzkjNzEzW}`

My first attempt was to pass the characters to `tr -d` as separate arguments (`tr -d '^' '%'`) which failed with an "extra operand" error. The error message made me realize that the `-d` option expects all characters to be deleted to be in a single string. The correct approach then after running the  "--help " command I realised  was to combine them into one argument, like `'^%'`. This successfully removed both characters and revealed the flag.

```bash
Connected!
hacker@data~deleting-characters:~$ /challenge/run
Your character-stuffed flag:
p^w%n^%.^%c^%o^%ll^e^%g^%e^%{^%s^%wB^%i^%T%Y^%m%f%yu%u^-a%K^t^%q^%D^i^%vf^%0^W^T^A^0^%9%f^%.^%0^%F^%N^x^E^zN%x^w^%S^%M^%z^k^j^%N^z^E^%z^W}^%^%
hacker@data~deleting-characters:~$ /challenge/run | tr -d '^' '%'
tr: extra operand ‘%’
Only one string may be given when deleting without squeezing repeats.
Try 'tr --help' for more information.
hacker@data~deleting-characters:~$ tr --help
Usage: tr [OPTION]... STRING1 [STRING2]
Translate, squeeze, and/or delete characters from standard input,
writing to standard output.  STRING1 and STRING2 specify arrays of
characters ARRAY1 and ARRAY2 that control the action.

  -c, -C, --complement    use the complement of ARRAY1
  -d, --delete            delete characters in ARRAY1, do not translate
  -s, --squeeze-repeats   replace each sequence of a repeated character
                            that is listed in the last specified ARRAY,
                            with a single occurrence of that character
  -t, --truncate-set1     first truncate ARRAY1 to length of ARRAY2
      --help        display this help and exit
      --version     output version information and exit

ARRAYs are specified as strings of characters.  Most represent themselves.
Interpreted sequences are:

  \NNN            character with octal value NNN (1 to 3 octal digits)
  \\              backslash
  \a              audible BEL
  \b              backspace
  \f              form feed
  \n              new line
  \r              return
  \t              horizontal tab
  \v              vertical tab
  CHAR1-CHAR2     all characters from CHAR1 to CHAR2 in ascending order
  [CHAR*]         in ARRAY2, copies of CHAR until length of ARRAY1
  [CHAR*REPEAT]   REPEAT copies of CHAR, REPEAT octal if starting with 0
  [:alnum:]       all letters and digits
  [:alpha:]       all letters
  [:blank:]       all horizontal whitespace
  [:cntrl:]       all control characters
  [:digit:]       all digits
  [:graph:]       all printable characters, not including space
  [:lower:]       all lower case letters
  [:print:]       all printable characters, including space
  [:punct:]       all punctuation characters
  [:space:]       all horizontal or vertical whitespace
  [:upper:]       all upper case letters
  [:xdigit:]      all hexadecimal digits
  [=CHAR=]        all characters which are equivalent to CHAR

Translation occurs if -d is not given and both STRING1 and STRING2 appear.
-t is only significant when translating.  ARRAY2 is extended to length of
ARRAY1 by repeating its last character as necessary.  Excess characters
of ARRAY2 are ignored.  Character classes expand in unspecified order;
while translating, [:lower:] and [:upper:] may be used in pairs to
specify case conversion.  Squeezing occurs after translation or deletion.

GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
Report any translation bugs to <https://translationproject.org/team/>
Full documentation <https://www.gnu.org/software/coreutils/tr>
or available locally via: info '(coreutils) tr invocation'
hacker@data~deleting-characters:~$  /challenge/run | tr -d ^ %
tr: extra operand ‘%’
Only one string may be given when deleting without squeezing repeats.
Try 'tr --help' for more information.
hacker@data~deleting-characters:~$  /challenge/run | tr -d ^ |tr -d &
[1] 148
hacker@data~deleting-characters:~$ tr: missing operand
Try 'tr --help' for more information.

[1]+  Exit 1                  /challenge/run | tr -d ^ | tr -d
hacker@data~deleting-characters:~$ /challenge/run | tr -d '^%'
Your character-stuffed flag:
pwn.college{swBiTYmfyuu-aKtqDivf0WTA09f.0FNxEzNxwSMzkjNzEzW}
hacker@data~deleting-characters:~$
```
###Learnings
I learned that when using tr -d to delete multiple characters, they must all be passed within a single string argument (e.g., tr -d 'abc'), not as separate arguments.
###References
None

## Deleting Newlines
This challenge involved a flag that was split into many lines. I had to use `tr` to delete the newline characters and put the flag back together.

### Solve
**Flag:** `pwn.college{oi9SequesSGt19Yj8-88BRqy99n.0VNxEzNxwSMzkjNzEzW}`

After running the program, I saw the output was completely vertical. The goal was to remove the invisible newline characters. To do this, I piped the output to `tr -d`. I specified the newline character, `\n`, and made sure to enclose it in single quotes so the shell would pass it correctly to the command. This joined all the parts into a single line, revealing the flag.

```bash
Connected!
hacker@data~deleting-newlines:~$ /challenge/run
Your line-split flag:
pw
n
.
co
l
l
e
g
e
{
o
i9Se
qu
e
s
S
Gt
19Y
j8-8
8
B
R
q
y9
9n
.0VNx
Ez
Nx
w
S
M
z
kj
N
z
EzW}

hacker@data~deleting-newlines:~$ /challenge/run | tr -d '\n'
Your line-split flag: pwn.college{oi9SequesSGt19Yj8-88BRqy99n.0VNxEzNxwSMzkjNzEzW}hacker@data~deleting-newlines:~$

```

###Learnings
I learned how to delete special, non-printable characters like newlines with tr by using their escaped representation (\n) inside quotes

### References
None

## Extracting the first lines with head
For this challenge,I needed to get the first 7 lines from one program's output and feed them into a second program to get the flag.

### Solve
**Flag:** `pwn.college{g5HQvxBOJ-fTo9HzmXwFvsmJy46.0lNxEzNxwSMzkjNzEzW}`

The solution required chaining three commands together.I initially ran "/challenge/pwn | head -n 7 "to aee the first 7 lines which were codes and I understood I needed to pipe them to the third command. The first command, `/challenge/pwn`, produced the initial stream of data. I piped its output to `head -n 7` to filter for only the top seven lines. Finally, I used a second pipe to send that filtered output directly to the `/challenge/college` program, which validated the input and gave me the flag.

```bash
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7

SECRET-CODE-29727

SECRET-CODE-19060

SECRET-CODE-14589

SECRET-CODE-3491

SECRET-CODE-30463

SECRET-CODE-27591

SECRET-CODE-27438

hacker@data~extracting-the-first-lines-with-head:~$  /challenge/pwn | head -n 7| /challenge/college

Congratulations, you piped the right codes!

pwn.college{g5HQvxBOJ-fTo9HzmXwFvsmJy46.0lNxEzNxwSMzkjNzEzW}
```
###Learnings
I learnt the use of "head" command that can help us see certain number of lines of the bigger code
### References
None

## Extracting specific sections of text
This challenge required me to use `cut` to isolate the second column containing the flag's characters and then use `tr` to join them into a single line.

### Solve
**Flag:** `pwn.college{k0UwPb1gk4XvizkuCwnE0ziSrkC.01NxEzNxwSMzkjNzEzW}`

After inspecting the output of `/challenge/run`, I saw the data was in two space-separated columns, with the flag characters in the second one. I built a pipeline to solve this. First, I piped the output to `cut`, using `-d ' '` and `-f 2` to select the second field. This gave me all the flag characters, each on a new line. To finish, I added another pipe to `tr -d '\n'` to remove the newlines and assemble the complete flag.

```bash
extracting-specific-sections-of-text:~$ /challenge/run

9721 p

10645 w

2938 n

12500 .

12344 c

19642 o

23081 l

22280 l

26251 e

27577 g

30427 e

15688 {

29833 k

31623 0

6674 U

9093 w

32398 P

10569 b

2451 1

13255 g

1405 k

30300 4

8403 X

10233 v

27816 i

18655 z

21740 k

30117 u

11306 C

9890 w

2660 n

14405 E

27888 0

8354 z

5017 i

17385 S

10467 r

24942 k

4244 C

8370 .

15713 0

13092 1

697 N

16668 x

13058 E

31560 z

26978 N

15139 x

11592 w

28456 S

26451 M

12014 z

12332 k

13738 j

23138 N

4483 z

19550 E

13031 z

27408 W

8984 }



/challenge/run | cut -d ' ' -f 2 | tr -d '\n'

pwn.college{k0UwPb1gk4XvizkuCwnE0ziSrkC.01NxEzNxwSMzkjNzEzW}

```
###Learnings
I learnt the use of "cut" command that can helpo extract specific columns (fields) from text by defining a delimiter with -d and selecting the desired field number with -f 

### References
None

## Sorting data
This challenge required me to find a specific flag within a file containing 100 fake flags. The solution involved using the `sort` command to order the flags alphabetically and identify the last one in the list.

### Solve
**Flag:** `pwn.college{0pZG35JldzZoh4hTBNUmLQt0RWI.0FM0MDOxwSMzkjNzEzW}`

To find the flag, I first navigated to the `/challenge` directory. Then, I ran the `sort flags.txt` command. This printed all 100 flags to the terminal in alphabetical order. As the challenge description mentioned, the correct flag was the last one in the sorted list, which I found at the very bottom of the long output.

```bash
hacker@data~sorting-data:~$ cd /challenge
hacker@data~sorting-data:/challenge$ sort flags.txt
ovm.bnllefe{0oYG34IkdyZoh4hTBMTmLPs0RVI.0FM0LDOxvSMzkjNzEzV}
ovm.bolldgd{0pZG35IldyZnh4hSANTmLPt0RVI.0FL0MCOwwSMzjjMzDyW}
ovn.cnlkdge{0pZG34JldyYog3gSBNUmKQs0QWI.0FM0LDOwwRMykjNyEyW}
ovn.cnllegd{0pYG35JkdyZoh3hSANTlLPt0RWI.0FM0LDNwwRLzjjNzEzW}
owm.bolldgd{0pZG35JldzZnh4hTBNTlLPs0QVH.0FM0LDOwwSMzkjNzEzW}
owm.bollefd{0pZG35JkdyYng4gTBNUmLQt0QWI.0FM0MDOxwSMzjiNyEyW}
owm.collefe{0oYG35JldzYoh3hSAMUlLPs0RWH.0EM0MDOxwSLzjjNyEzW}
own.bnklege{0oZG35JlczZoh4hTBNTlLQs0RWH.0FM0MCOxwRLzkjNzDzW}
own.bnlkefe{0pZF34JldyZnh4hTANUmLQt0RWI.0FM0MDOwwRMzkjMyEzW}
own.bokldfe{0pZG24JlczYng4gSANTmLQt0QVH.0EM0LDOxwSMzkjNzEzW}
own.cnkldge{0oZG25JldyYnh4hTBMTlKQt0RVI.0FM0MCOwvSMzkjNyDyV}
own.cnlkdge{0oYG34JkdzYoh3gTANUmLQt0RWI.0EM0MDOxwRMzkjMyEzW}
own.cnlkege{0pZG25JldzZoh3hTBMUmLQt0RVI.0FM0MDOxvSMykjNzEzW}
own.cnllegd{0pZG25JldzZog3hTBNUlLQt0QWI.0EM0MCOxwSMzkjNzDzV}
own.cokkege{0pZG34IlcyZoh4hTBNTmKPs0QVI.0FL0MDNwwRMykjNyEzW}
own.coklege{0pZF35JldyZnh4hSBNTmLQt0QVI.0EM0MDNwwSMyjjNzDzW}
own.colkdfe{0pYG34IkdzYnh3gTBNUmLQt0QWI.0FL0MDOxwSLzkjMyDyV}
own.collegd{0oZG35JkdzZoh4hTBMUmLQt0RWI.0FM0MCOxwRMzkiNzEyW}
own.college{0oZG35JlczZoh4gTANTlLQt0RWI.0EM0MCNxwRMzkjMzDyW}
own.college{0pZG35JldzZog4hTAMUmLQs0QVH.0FL0MDNxwSMykjMzEzV}
pvm.bokkege{0pZG35JkczZoh4hTAMUmLQt0QWI.0FM0LCNxwSMykjNzEyW}
pvm.cnlkege{0pZG35JldzZoh4hTANUmLPt0RWH.0EM0MDOxwSMzjjNzDzW}
pvm.cnllefe{0pZG34IkdyYng4hTBNUlLQt0RWH.0FM0MDNxvRMzjjNyEzW}
pvn.bolldfe{0pZF34IkczZng4hTBMTmLQt0QVI.0FM0LDNwvSMzkjNzDzW}
pvn.bollefe{0pZG34IldzZng3hTAMTmLQt0QWH.0FM0LCNwwSLykjNyEzW}
pvn.bollege{0pZG35IldzZoh3hSBNUmKQt0RWI.0FM0MDOxwRMzkjNzEzW}
pvn.cnklefe{0pZG35IkcyYoh4hTBNUmLPt0RWI.0FM0LDOxwRLzkiNyEzV}
pvn.cnklefe{0pZG35IldzYoh3hTBNUmKQt0QWI.0FM0MDOxwSMykjNzEzW}
pvn.cnlkdge{0pZG34JldyYnh4hSBNUmKQs0QWI.0EM0LDOxvRMzkjNyEyW}
pvn.cnlldgd{0oYG35JldyZnh4gSANUmKQt0RWI.0FM0MDOxvRMzkjNzEyV}
pvn.cnlldge{0oZF35IldyZng4hTBNUlKQt0RVI.0FM0MDOxvSLyjjNzEzW}
pvn.cnllege{0pZG35JldzZoh4hTBNUmKPt0RWI.0FL0MCOxwSMykjNzEzW}
pvn.cokkdge{0pZG35JldyZog4hSBNUmLPs0RWI.0FM0LDNxwSMzkjNzEzV}
pvn.colkege{0pZG35JkdzZog4gTBNUmLQt0RWI.0EL0MDOxwSMzjiNzEzW}
pvn.collefd{0pZF25JkdzZog4gTBNUmLQt0QWI.0EM0LCNxwSLzkjNzDyW}
pvn.college{0pZG35JldzYog4hTBNUmLQt0RWI.0FM0MCOxvSMzkjNzEzW}
pwm.bolldge{0pYG34IldzZoh4hTBNUmLQt0RWI.0FM0MDOxwSMzkjNzEzV}
pwm.bolldge{0pZG34JldzZng3hTANUmKPt0RWI.0FM0MDNxvSMykiNzEzW}
pwm.cnkldge{0oZF35JlczZng4hTBNUlLQt0RWI.0FL0LDNxvSMzjjMyEzV}
pwm.cnkldge{0oZG34IldzZog3gTBNTmLQt0RVI.0EL0MDOxwSMzkjNyDyW}
pwm.cnllegd{0oYF35JlcyYoh4hSBNUmLQt0RWI.0EM0LCNxvRMyjiNzEzV}
pwm.cokldfe{0oYG25JkcyYog3hTANUmLQt0QWI.0FM0MDNxwRMzkjNyDyW}
pwm.coklegd{0oYF34JldzZng3hSBNTlLPt0QWH.0FM0LDNxvRMzjjNyEyW}
pwm.coklege{0pZF35IldzZnh4hTBNUmLQt0QVI.0EM0MDOxwSMzkjNzEzW}
pwm.coklege{0pZF35JldzZog3hSBNUmLQt0RWI.0FM0MDOwwSLzkjNzDzW}
pwm.colkdge{0pYG25JldyZoh4hTANUlLQs0RWI.0FM0MCNwwSMykjNzEzW}
pwm.colkdge{0pZG34JkdyZoh4hTANUlLPt0RWI.0FM0LCNxwSMzjjMzDyW}
pwm.colldfe{0pZF35JldyZog3hTAMUmLQt0RWI.0FM0MDOxwSMzjiNzEzW}
pwm.collefe{0pYG25IkcyYnh4gTBNUlKQs0QWI.0FM0LCOwwSMykjNzEzW}
pwm.collefe{0pYG34JlczYoh4gTANUlLQs0RVI.0EL0MDNxwRLzkjMzEzV}
pwm.collegd{0pZG34JldyYnh4hTBNUlLQt0RWH.0FM0MDNwwSLzkjMyEzV}
pwm.college{0oYF34IkczZoh3gSBNTlLQs0RVI.0EM0MDNwwRMzkjMzEyV}
pwm.college{0pZG35JlczZoh4hTBNUmLQt0RWI.0FM0LDOxwSMyjjNzEzW}
pwn.bnklege{0pYG34IldzZoh3hTBMUlLPt0RWI.0FL0MCOwwRLzkjNzEzW}
pwn.bokkdge{0oYF35JldyYoh3hTANTlLQt0QWI.0EM0LDOwwSMzkjMzEzV}
pwn.bokldge{0pZG35JkczZoh4hSBNUmLQt0RWI.0FL0MDOxwSLzkjNzEzV}
pwn.boklegd{0pZG35JldyZnh4hTBNUmLQs0QWH.0FM0MCOxwSMykjNzEzV}
pwn.bolkdge{0pZG34IlczYog4hSANUmKPt0RVI.0EM0MDOwwSLykiNzDyW}
pwn.bolkege{0pZG35JlcyYoh4hTBNUlLQt0RWI.0FM0MDOwwRLzkjNzEzV}
pwn.bolkege{0pZG35JldyYnh4hTBMUmLQt0QVH.0EM0LDNwwSMzkjNzDyW}
pwn.cnlkdgd{0pYG24JldyZoh4gTAMUmKQt0RWI.0FL0LDOwwSLzkjNzDzW}
pwn.cnllefd{0pZF34JkdzYoh4hTBNUlLQt0RWI.0FL0MDOxwSMzjjNzEzV}
pwn.cnllefe{0pYF35IkdzZoh4hTBNUmLQt0RVI.0FL0MDOxwSMzkiNzEyW}
pwn.cnllefe{0pZG25JkdzZoh4hTBNUmLQt0RWI.0FM0MDOxwSMzjjMzEzW}
pwn.cnllege{0pZG25IldyZnh4hTBNTmLQs0RWI.0FM0MDOxwSLykjNzEzW}
pwn.cokldge{0pZG35JkdzYoh4hTBMUmLQt0RVH.0FL0MCNxvSMzkjMzEzW}
pwn.coklefe{0pZG35JldyZog4hTBNUmLQt0RWI.0FM0MDOxwSLzjjMzEzW}
pwn.coklegd{0oYG35IldzZnh3hTANUlLQt0RWI.0FL0MCNxwSLzkjMzEyV}
pwn.coklege{0pYG35JldzZoh4hTBNTlLQt0RVI.0EM0LDOxwSMykjNzEzW}
pwn.coklege{0pZG35IldzZoh4gTBNUlLQs0RVI.0EM0MDOxwSMykjNzEzW}
pwn.colkefe{0pZG35JlczZoh3hTANUmLQt0RWI.0FM0MDOxwSMzkjNzEzW}
pwn.colkege{0pYG35IldzZoh3hTBNUmKQt0RWH.0FM0LDOxwSLzkjNzEzW}
pwn.colldge{0pZG25JkczZog4gTBMUmLPt0QWI.0EM0MDOwwSMzkiNzEyV}
pwn.colldge{0pZG25JkdzZoh3hTANUmKQt0RWI.0FM0MDOxwRMykjNzDzV}
pwn.colldge{0pZG34IldzZng4gTANUlLPs0RWH.0FM0MDNxvRMzkjNzEzW}
pwn.colldge{0pZG35JldzZoh4gTBNUmLQt0QWI.0FM0MDOxwSMzkjNzEzW}
pwn.collefe{0oZF35IldzYoh4hTAMUmLPs0RWH.0FL0MDOwvSLzkjMzEyW}
pwn.collefe{0pYG35JldzZoh4hTBNUmLQt0RWH.0FL0MDOxvRMzkjMzEzW}
pwn.collefe{0pZG35JldyZoh4hTBNUmLQt0RWI.0FM0MDOxwSMzkjMzEzV}
pwn.collegd{0pZG24IlczZnh4hTAMTmLPt0RWI.0FM0MDOxwSMzjiMyEzW}
pwn.collegd{0pZG35JldzZoh3gTBMUmLPt0RWH.0EM0LDOwwSMzjjNzDzV}
pwn.college{0oZF35JkdzZng3hTBNUlLPt0QWI.0FM0MCNxwSLzkjNzEzW}
pwn.college{0oZG25JkdzZnh3hTANTmKQt0QWI.0EL0MDNwwRMzjjNyEzW}
pwn.college{0oZG35JldyZoh4hTBNUmLQt0RWI.0FM0MDOxvRMykjNzDzW}
pwn.college{0pYG35IldyZoh4hTBNUmLQt0RWI.0EL0MDNxwSMzkjNzEzW}
pwn.college{0pZF35IldzZnh4hTBNUmKQt0RVH.0FM0MDOxvSMzkjNzEyV}
pwn.college{0pZG34JkdyYoh4gSAMUlLQs0RWI.0FM0MDOxwSLzjiNzEzW}
pwn.college{0pZG35JkdzZog4hTBNTmLQt0RWI.0EM0MDOxwSMzkjNzEzW}
pwn.college{0pZG35JldyZng4hTANUmLQt0RWI.0FL0MDNxwSMykjNzEzW}
pwn.college{0pZG35JldyZng4hTBNUmLQt0RWI.0FM0MDOxwSMzkjNzEzW}
pwn.college{0pZG35JldyZoh4hTBNUmLQt0RWI.0FM0LDOxwSMzkjNzEzW}
pwn.college{0pZG35JldzZnh4hSBNUlLQt0RWI.0FM0MDOxwSMzkjNzEzW}
pwn.college{0pZG35JldzZoh4hTBMUmLQt0RWH.0FL0MDOxwRMzkjMzEzW}
pwn.college{0pZG35JldzZoh4hTBNUlLQt0RVI.0FM0MDOxwRMzkjNzEzW}
pwn.college{0pZG35JldzZoh4hTBNUmLPt0RWI.0FM0MDOxwSMzkjNzEzW}
pwn.college{0pZG35JldzZoh4hTBNUmLQt0QWI.0FM0MDOxwSMzkjNzDzW}
pwn.college{0pZG35JldzZoh4hTBNUmLQt0RWI.0FM0MDNxwSMzkjNzEzW}
pwn.college{0pZG35JldzZoh4hTBNUmLQt0RWI.0FM0MDOxvSMzkjNzEzW}
pwn.college{0pZG35JldzZoh4hTBNUmLQt0RWI.0FM0MDOxwSMzjjNzEzW}
pwn.college{0pZG35JldzZoh4hTBNUmLQt0RWI.0FM0MDOxwSMzkjNzEzW}
pwn.college{0pZG35JldzZoh4hTBNUmLQt0RWI.0FM0MDOxwSMzkjNzEzW}
hacker@data~sorting-data:/challenge$
```
###Leanrnings
I learned how to use the basic sort command to alphabetically order lines from a file.With the right arguments it can also be used to sort like:
-r: reverse order (Z to A)
-n: numeric sort (for numbers)
-u: unique lines only (remove duplicates)
-R: random order!

### References
None
