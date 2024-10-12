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

