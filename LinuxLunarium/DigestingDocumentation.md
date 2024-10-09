# Digesting Documentation

This module is about self leanring through Linux. Learning for help on how to use programs.

## Learning from Documentation

The program for this challenge was `/challenge/challenge`, and in order for it to give the flag  an argument `--giveflag` was supposed to be attached to the command.

Flag: pwn.college{I07_jDzd0E1gLNL9wSsZfH-ceik.dRjM5QDL0IzN0czW}

## Learning Complex Usage

In this challenge, the flag was recieved after giving the arguments `--printfile` and `/flag` to the `/challenge/challenge` program

Flag: pwn.college{UHTpKORe-BqgyEFF1v7M70hQROc.dVjM5QDL0IzN0czW}

## Reading Manuals

In this challenge I run the `man challenge` command to read throught the documentation of the `/challenge/challenge` command.
And then according to the description, I used `/challenge/challenge --awmvjb 555` to get my flag

Flag: pwn.college{Ia5wHC5mARvIj5bb1786T9FdGGW.dRTM4QDL0IzN0czW}

## Searching Manuals

Runnung the `man challenge` in the terminal gave a big list of commands which said they were not the right one. To get to the right one I typed `/` and searched for `flag` to find the argument which will give me the flag.

Flag: pwn.college{0CzpjYTtQ8boSyenXnx6zKzObYU.dVTM4QDL0IzN0czW}

## Searching for manuals

Reading through the `man man` I came across a -k argument.

-k, --apropos
              Equivalent to apropos.  Search the short manual page descriptions for keywords and display any matches.  See apropos(1) for details.

I ran the `man -k challenge` to search for the command. 
It told me to search thorugh the `sclcjbgmqd` manual page, on searching through which I found the `--sclcjb 540` argument to get to the flag.

Flag: pwn.college{sIclIcQLjbgXZIFKmXqddtzS_5q.dZTM4QDL0IzN0czW}

## Helpful Programs

In this level, to find the argument which would give me the flag, I run the `/challenge/challenge --help` command which gave me a bunch of arguments two of which were used.
`-p` was used to print the secret number which was then used with the `-g` argument to print the flag.

Flag: pwn.college{AZdGKdZabE1iz1KM1dy5e6TQYNS.ddjM4QDL0IzN0czW}

## Help for Builtins

Running the `help challenge` for builtin `challenge` gave me a list arguments to go with `challenge` command.
`challenge --secrect 0-V2RcGd` gave me my flag.

Flag: pwn.college{0-V2RcGdpheW41pvgbGMPZvMpii.dRTM5QDL0IzN0czW}
