# Chaining Commands

How can we run commands in succession to achieve some cumulative effect?  
Let's Learn.

## Chaining with Semicolons

Two commands to be run in succession are separated by a semicolon **;**

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{QeJ_Pxlpnm7VRLNI28WrzTNI1Ji.dVTN4QDL0IzN0czW}
hacker@chaining~chaining-with-semicolons:~$ 
```

Flag: `pwn.college{QeJ_Pxlpnm7VRLNI28WrzTNI1Ji.dVTN4QDL0IzN0czW}`

## Your First Shell Script

In this challenge, we were supposed to add commands to a bash file called `x.sh` and run it to get our flag.  
I used nano text editor to edit `x.sh`  
Running the `bash x.sh` cmd gave the flag.

Flag: `pwn.college{47w0jDJjCl-6_EONXh2gBY8q03C.dFzN4QDL0IzN0czW}`

## Redirecting Script Output

`x.sh` already had the commands from the previous level. Just piping(**|**) the the output of the script into a single invocation of the `/challenge/solve` command was required.
```
hacker@chaining~redirecting-script-output:~$ cat x.sh
/challenge/pwn
/challenge/college

hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve 
Correct! Here is your flag:
pwn.college{AXO_oiBmgLuXl7mrMxp5bMf_Kyk.dhTM5QDL0IzN0czW}
hacker@chaining~redirecting-script-output:~$ 
```

Flag: `pwn.college{AXO_oiBmgLuXl7mrMxp5bMf_Kyk.dhTM5QDL0IzN0czW}`

## Executable Shell Scripts

How can you not use the `bash` command explicitly and find the output to that bash file?  
Making the file executable and incoking it using it's actual path, you can do that.

```
hacker@chaining~executable-shell-scripts:~$ cat x.sh
/challenge/pwn
/challenge/college

hacker@chaining~executable-shell-scripts:~$ nano x.sh
hacker@chaining~executable-shell-scripts:~$ cat x.sh
/challenge/solve
hacker@chaining~executable-shell-scripts:~$ ~/x.sh
bash: /home/hacker/x.sh: Permission denied
hacker@chaining~executable-shell-scripts:~$ chmod u+x x.sh
hacker@chaining~executable-shell-scripts:~$ ~/x.sh
You must make a shellscript in your home directory that will launch 
/challenge/solve, make it executable, and invoke it without explicitly 
specifying 'bash'!
hacker@chaining~executable-shell-scripts:~$ 
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{I3W1Su3DRlyjw7jE2u_150-nPhP.dRzNyUDL0IzN0czW}
```

Flag: `pwn.college{I3W1Su3DRlyjw7jE2u_150-nPhP.dRzNyUDL0IzN0czW}`

# END