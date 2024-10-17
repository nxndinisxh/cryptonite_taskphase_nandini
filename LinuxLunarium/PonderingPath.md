# Pondering PATH

Where is the `ls` program located? Let's know.

## The PATH Variable 

There is a special shell variable, called `PATH`, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands. Without a `PATH`, bash cannot find the ls command.  

I run the `PATH=""` to get the flag.
```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{QsQSnhQnNW3zMS2f2DsFSrnMFLd.dZzNwUDL0IzN0czW}
hacker@path~the-path-variable:~$ 
```

Flag: `pwn.college{QsQSnhQnNW3zMS2f2DsFSrnMFLd.dZzNwUDL0IzN0czW}`

## Setting PATH

For this challenge,  the program `/challenge/run` will run the win command via its bare name, but this command exists in the `/challenge/more_commands/` directory, which is not initially in the `PATH` variable. Therefore we need to add the path to the `PATH` variable to get our flag.

```
hacker@path~setting-path:~$ PATH=/challenge/more_commands/win
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
/challenge/run: line 4: win: command not found
It looks like that did not work... Did you set PATH correctly?
hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{kncRsJSH74EC2LB3AhUb7rN0I-L.dVzNyUDL0IzN0czW}
hacker@path~setting-path:~$ 
```

Flag: `pwn.college{kncRsJSH74EC2LB3AhUb7rN0I-L.dVzNyUDL0IzN0czW}`

## Adding Commands

