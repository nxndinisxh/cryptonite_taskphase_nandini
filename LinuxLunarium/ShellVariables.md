# Shell Variables

This module gets us familiar with setting, printing, and using the shell variables.

## Printing Variables

`echo` just prints stuff.
Eg: 
```
hacker@variables~printing-variables:~$ echo FLAG
FLAG
```
But it can also be used to print the variables using the `$` before the variable name.

```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{owxjMCcjfXr8noT43MOFdn9v45o.ddTN1QDL0IzN0czW}
```

Flag: `pwn.college{owxjMCcjfXr8noT43MOFdn9v45o.ddTN1QDL0IzN0czW}`

## Setting Variables

Seems like we can also create variables in shell, by simply using "variablename"="variablevalue"
This was the task of the level too: Creating a variable PWN and assigning a value COLLEGE to it.

Flag: `pwn.college{EB_sYO2GUvAuUDrdOw23bWJLpN-.dlTN1QDL0IzN0czW}`

## Multi-word Variables

What if you want to set a value to variable that has spaces!? 
Looks like it's not that hard!
Just using double quotes with the value will do the work.

```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
```

Flag: `pwn.college{YvbdPZ1qxPRxUK4ilIYad0_f8-Z.dBjN1QDL0IzN0czW}`

## Exporting Variables

Shell does not allow other commands to inherit the variables outside the shell process unless it is explicitly done.
To do that, `export` command is used.

To obtain the flag, the following steps were taken:

```
hacker@variables~exporting-variables:~$ PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
Incorrect...
You have not set the COLLEGE variable to the correct value (it should be 
'PWN'). Do that before running this script! Even though it is not exported, in 
this challenge, we have ways to check...
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{4RXObZIJy5_hk9GEWXKIkPhK-SN.dJjN1QDL0IzN0czW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ 
```

Flag: `pwn.college{4RXObZIJy5_hk9GEWXKIkPhK-SN.dJjN1QDL0IzN0czW}`

## Printing Exported Variables

Running the `env` gave me a list of all the exported variables and going through the list gave me the flag.
Flag: `pwn.college{0tj_pZQrHYuoFnYbWOaMvwG3uHA.dhTN1QDL0IzN0czW}`

## Sorting Command Output

We learnt about Command Substitution in this challenge.
I was supposed to store the output of the command `/challenge/run` in the `PWN` variable and then read it to get the flag.

```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{wvoWw2jqSrUVs02j4_A_x1dKqJD.dVzN0UDL0IzN0czW}
```

Flag: `pwn.college{wvoWw2jqSrUVs02j4_A_x1dKqJD.dVzN0UDL0IzN0czW}`

## Reading Input

What if you wanted to take input from the user using the command line!?
You can do it using the `read` command. 

```
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{k_GcBIi5P3n-HiiqLFv6rMOU_XZ.dhzN1QDL0IzN0czW}
```

Flag: `pwn.college{k_GcBIi5P3n-HiiqLFv6rMOU_XZ.dhzN1QDL0IzN0czW}`

## Reading Files

There is also a way to read what is there in a file.
You can use the `read` command to read the contents of a file too.

```
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{0kiN3cmpqLi6S_ElwdXLHl9wG9u.dBjM4QDL0IzN0czW}
```

Flag: `pwn.college{0kiN3cmpqLi6S_ElwdXLHl9wG9u.dBjM4QDL0IzN0czW}`

# END