# Percieving Permissions

## Changing File Ownership

Turns out, my new dream is to become the root!
Interestingly, we can change the ownership of files. This is done via the `chown`.
Again, `chown` can only be invoked by the root(a dream tbh!).
Flag was obtained using the following commands:


```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ ls -l
total 36
-rw-r--r-- 1 hacker hacker    4 Oct  9 17:16 COLLEGE
drwxr-xr-x 2 hacker hacker 4096 Oct  5 16:40 Desktop
-rw-r--r-- 1 hacker hacker    8 Oct  9 18:12 PWN
-rw-r--r-- 1 root   hacker   58 Oct  8 19:15 c
-rw-r--r-- 1 hacker hacker    4 Oct  9 17:16 college
-rw-r--r-- 1 hacker hacker  829 Oct  9 18:06 instructions
-rw-r--r-- 1 hacker hacker   93 Oct  9 18:06 myflag
lrwxrwxrwx 1 hacker hacker    5 Oct  9 10:10 not-the-flag -> /flag
-rw-r--r-- 1 root   hacker   77 Oct  9 18:46 output
-rw-r--r-- 1 hacker hacker  435 Oct  9 17:57 the-flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{Is4kE22HHgGxtMITfi51xuVZlvW.dFTM2QDL0IzN0czW}
hacker@permissions~changing-file-ownership:~$ 
```

Flag: `pwn.college{Is4kE22HHgGxtMITfi51xuVZlvW.dFTM2QDL0IzN0czW}`

## Groups and Files

Unless you have write access to the file and membership in the new group, this typically requires root access.

Here, I first invoked the `ls -l` cmd to list the permissions of the files/directories/...  
I tried reading the `myflag` and  `the-files` for the flag but they did not seem correct as I really did not do what the level was asking me to do, then I tried reading `/flag` where I was denied permission.  
That is where I changed the grp to `hacker` (That was what the level asked) and continued to getting my flag in the `/flag`.

```
hacker@permissions~groups-and-files:~$ ls -l
total 36
-rw-r--r-- 1 hacker hacker    4 Oct  9 17:16 COLLEGE
drwxr-xr-x 2 hacker hacker 4096 Oct  5 16:40 Desktop
-rw-r--r-- 1 hacker hacker    8 Oct  9 18:12 PWN
-rw-r--r-- 1 root   hacker   58 Oct  8 19:15 c
-rw-r--r-- 1 hacker hacker    4 Oct  9 17:16 college
-rw-r--r-- 1 hacker hacker  829 Oct  9 18:06 instructions
-rw-r--r-- 1 hacker hacker   93 Oct  9 18:06 myflag
lrwxrwxrwx 1 hacker hacker    5 Oct  9 10:10 not-the-flag -> /flag
-rw-r--r-- 1 root   hacker   77 Oct  9 18:46 output
-rw-r--r-- 1 hacker hacker  435 Oct  9 17:57 the-flag
hacker@permissions~groups-and-files:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{4YNY3MFAPb-FrnYvTX9lnFS5V_F.ddjN1QDL0IzN0czW}

hacker@permissions~groups-and-files:~$ cat the-flag 
 | 
\|/ This is the first half:
 v 
pwn.college{Al6PMN0NjN9gg6UOq9tw6I1-g5G.ddDM5QDL0IzN0czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
hacker@permissions~groups-and-files:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{ccUSp7P-mP0cplpqT3-iJK520aK.dFzNyUDL0IzN0czW}
hacker@permissions~groups-and-files:~$ 
```

Flag: `pwn.college{ccUSp7P-mP0cplpqT3-iJK520aK.dFzNyUDL0IzN0czW}`

## Fun with Groups Names

In this level, the grp name was `grp15911` and that is what the `/flag` was supposed to be shifted to.
```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp15911) groups=1000(grp15911)
hacker@permissions~fun-with-groups-names:~$ chgrp grp15911 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{wB2Zda3t7qxrAnNfUVVe65LkmD8.dJzNyUDL0IzN0czW}
```

Flag: `pwn.college{wB2Zda3t7qxrAnNfUVVe65LkmD8.dJzNyUDL0IzN0czW}`

## Changing Permissions

The following are the meaning of the characters in the actual access permissions.  
```
r - user/group/other can read the file (or list the directory)
w - user/group/other can modify the files (or create/delete files in the directory)
x - user/group/other can execute the file as a program (or can enter the directory, e.g., using `cd`)
- - nothing 
```
Like ownership, file permissions can also be changed. This is done with the `chmod` (change mode) command.  

In this level, we will cover the former: modifying an existing mode. chmod allows you to tweak permissions with the mode format of WHO+/-WHAT, where WHO is user/group/other and WHAT is read/write/execute. For example, to add read access for the owning user, you would specify a mode of u+r. write and execute access for the group and the other (or all the modes) are specified the same way. More examples:

\*u+r, as above, adds read access to the user's permissions
\*g+wx adds write and execute access to the group's permissions
\*o-w removes write access for other users
\*a-rwx removes all permissions for the user, group, and world

