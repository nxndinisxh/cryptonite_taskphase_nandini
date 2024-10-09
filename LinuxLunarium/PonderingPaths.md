# Pondering Paths

This module is about learning the basics of Linux file paths. 

## The Root

1st challenge is about learning how to access a program named `pwn` using the `/pwn` command. `/` is the symbol for the root directory, the words following it are the names of the programs/paths that follow.
`/pwn` is the path to the pwn program under the root directory.
Flag was obtained by entering `/pwn` command on the terminal 
Flag: pwn.college{geL3ISy0aupqQVj-MuwqI7vtjWO.dhzN5QDL0IzN0czW}

## Program and absolute paths

This challenge was teaching a bit more complex way of accessing the `run`  directory which was inside a `challenge` directory in te `/` directory.
Flag was obtained by running the absolute path command `/challenge/run`
Flag: pwn.college{EMqlcj7mnQax2BGlU3c4go0W1LU.dVDN1QDL0IzN0czW}

## Position thy self

This challenge wanted me to invoke the absolute path from the right directory.

I tried invoking `/challenge/run` command to which it showed

Incorrect..
And told me I was not in the correct directory

I ran the `cd /usr/share/zoneinfo/posix/Asia` command to get to the right directory and then ran the `/challenge/run` command to get my flag.
Flag: pwn.college{ILrXGKs9iIHxy_1flcso0xl9xJI.dZDN1QDL0IzN0czW}

## Position elsewhere

This was a similar challenge to what we did in the last challenge
 I tried invoking `/challenge/run` to which it chowed
 Incorrect.. 
 And told me I was not in the correct directory

 I ran the `cd /proc/192/fd` command to enter the correct directory and then the `/challenge/run` to get the flag.

Flag: pwn.college{8X1q0f-EkinMZ7VkBxL1BG_qpYp.ddDN1QDL0IzN0czW}

## Position yet elsewhere

 This was the same challenge to what we did in the last ones
 I tried invoking `/challenge/run` to which it chowed
 Incorrect.. 
 And told me I was not in the correct directory

 I ran the `cd /usr/share/zoneinfo/posix/Asia` command to enter the correct directory and then the `/challenge/run` to get the flag.

Flag: pwn.college{ka5l_Cx1zFLrfUEYIa4qdeXVTeJ.dhDN1QDL0IzN0czW}

## implicit relative paths, from /

This challenge required me to go in the `/` directory using the `cd /` cmd and then invoke the relative path `challenge/run` to get the flag.

Flag: pwn.college{c4MopsqKJZ4KF9nt6rSch9wKZ81.dlDN1QDL0IzN0czW}

## explicit relative paths, from /

This challenge required me to invoke the directory from the `/` directory using the relative paths.

Flag was obtained on going into the `/` directory using `cd /` cmd and then invoking the directory using `./challenge/run` cmd

Flag: pwn.college{oNShTY5BwRQllSc4oyg3sk7BH3K.dBTN1QDL0IzN0czW}

## implicit realtive path

This challenge required me to invoke the `run` directory from `challenge` directory using the relative paths.

Flag was obtained by running the following commands
1. `cd /challenge`
2. `./run`

Flag: pwn.college{shcygkeLdCtHxGa4t_PYebHDDum.dFTN1QDL0IzN0czW}

## home sweet home

This challenge what `~` signifies. It is shorthand for the home directory of the user. Here, in the challenge the user is the hacker so `~` iss expanded to `/home/hacker`

The flag was obtained by running the `/challenge/run ~/c` cmd.
The constraints I followed were
1. The argument was an absolute path
2. The path was inside the home directory
3. The argument was 3 character or less before expansion.
Flag: pwn.college{cwzEJG7eooT79Q_gmW5QH39L34R.dNzM4QDL0IzN0czW}