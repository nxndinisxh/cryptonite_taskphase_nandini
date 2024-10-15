# Processes and Jobs

In moder computing, softwares are split into two categories: operating system kernels and processes. 

When Linux starts up, it launches an init (short for initializer) process that, in turn, launches a bunch of other processes which launch more processes until, eventually, you are looking at your command line shell, which is also a process! The shell, of course, launches processes in response to the commands you enter.

## Listing Processes

In this level, you the use of the `ps` command which is used to list running processes.
Use of different arguments like `-ef` and `aux` to make the command useful is also explained.

```
hacker@processes~listing-processes:/$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 14:02 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 14:02 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 14:02 ?        00:00:00 /challenge/14855-run-22043
root          72      68  0 14:02 ?        00:00:00 sleep 6h
hacker        81       1  0 14:02 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libe
hacker       104      81  2 14:02 ?        00:00:08 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libe
hacker       128     104  0 14:02 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libe
hacker       156     104  3 14:02 ?        00:00:10 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node --dns-result-order=ipv4first /nix/store/3v4hdb2gmpj7jv2z848i
hacker       246     104  0 14:03 ?        00:00:01 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libe
hacker       269     246  0 14:03 pts/0    00:00:00 /run/workspace/bin/bash --init-file /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/out/v
hacker      1431     269  0 14:08 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:/$ /challenge/14855-run-22043
Yahaha, you found me! Here is your flag:
pwn.college{IoSil_cU_ciHYvb0jgnsq3XKgJT.dhzM4QDL0IzN0czW}
Now I will sleep for a while (so that you could find me with 'ps').
hacker@processes~listing-processes:/$ 
```

Flag: `pwn.college{IoSil_cU_ciHYvb0jgnsq3XKgJT.dhzM4QDL0IzN0czW}`

## Killing Processes

This level deals with the `kill` command which can be used to terminate any running processs using the `PID` in the `ps -ef` list pf that process.

```
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 14:16 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 14:16 ?        00:00:00 /run/dojo/bin/sleep 6h
root          71       1  0 14:16 ?        00:00:00 su -c /challenge/.launcher hacker
hacker        73      71  0 14:16 ?        00:00:00 /challenge/dont_run
hacker        74      73  0 14:16 ?        00:00:00 sleep 6h
hacker        83       1  2 14:16 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-
hacker       104      83 14 14:16 ?        00:00:05 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-
hacker       145     104  7 14:16 ?        00:00:02 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node --dns-result-order=ipv4first /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rj
hacker       163     104  0 14:16 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-
hacker       206     104  1 14:16 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-
hacker       223     206  0 14:16 pts/0    00:00:00 /run/workspace/bin/bash --init-file /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/out/vs/workben
hacker       338     223  0 14:16 pts/0    00:00:00 ps -ef
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 14:16 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 14:16 ?        00:00:00 /run/dojo/bin/sleep 6h
hacker        74       1  0 14:16 ?        00:00:00 sleep 6h
hacker        83       1  1 14:16 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-
hacker       104      83 10 14:16 ?        00:00:06 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-
hacker       145     104  5 14:16 ?        00:00:03 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node --dns-result-order=ipv4first /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rj
hacker       163     104  0 14:16 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-
hacker       206     104  1 14:16 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-
hacker       223     206  0 14:16 pts/0    00:00:00 /run/workspace/bin/bash --init-file /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/out/vs/workben
hacker       451     223  0 14:17 pts/0    00:00:00 ps -ef
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{Yt2uldg5nQ-IudgDoU4Bf-uiL3M.dJDN4QDL0IzN0czW}
hacker@processes~killing-processes:~$ 
```

Flag: `pwn.college{Yt2uldg5nQ-IudgDoU4Bf-uiL3M.dJDN4QDL0IzN0czW}`

## Interrupting Processes

How will you interrupt a process that's running?
Using `Ctrl+C` you can interrupt any process that is running.

Flag: `pwn.college{wrbwmag130GGTUN95HZ-4VD4roQ.dNDN4QDL0IzN0czW}`

## Suspending Processes

You can suspend a process to the background by using `Ctrl+Z`


```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root        1572     254  0 16:55 pts/0    00:00:00 bash /challenge/run
root        1574    1572  0 16:55 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[3]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root        1572     254  0 16:55 pts/0    00:00:00 bash /challenge/run
root        1653     254  0 16:55 pts/0    00:00:00 bash /challenge/run
root        1655    1653  0 16:55 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{Qc7MEtzPaSBuH1aK-cOnVReugyy.dVDN4QDL0IzN0czW}
```

Flag: `pwn.college{Qc7MEtzPaSBuH1aK-cOnVReugyy.dVDN4QDL0IzN0czW}`

## Resuming Processes

`fg` with the argument as the process name brings the suspended proces back to the foreground of the terminal and resumes them.

```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{I8rn6L0uGSmBpsPH-rVpI4CEN3T.dZDN4QDL0IzN0czW}
Don't forget to press Enter to quit me!

Goodbye!
```

Flag: `pwn.college{I8rn6L0uGSmBpsPH-rVpI4CEN3T.dZDN4QDL0IzN0czW}`

## Backgrounding Processes

Your process can still be running in background using the `bg` command.

```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         741 S+   bash /challenge/run
root         743 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         741 S    bash /challenge/run
root         861 S    sleep 6h
root        1092 S+   bash /challenge/run
root        1094 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{UdI-S6Krd7yIxcvAy9TIP86HXzf.ddDN4QDL0IzN0czW}
```

Flag: `pwn.college{UdI-S6Krd7yIxcvAy9TIP86HXzf.ddDN4QDL0IzN0czW}`

## Foregrounding Processes

This challenge was just a walkthrough in terminal.

```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg /challenge/run
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.
hacker@processes~foregrounding-processes:~$ fg /challenge/run 
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{QDdryAwqG2k3JnW7Cpl56vr2gKF.dhDN4QDL0IzN0czW}
```

Flag: `pwn.college{QDdryAwqG2k3JnW7Cpl56vr2gKF.dhDN4QDL0IzN0czW}`

## Starting Backgrounded Processes

You can run a process in background without suspending using `&` after the process name.

```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run 
You've started me in the foreground! You must start me in the background (by 
appending '&' to the command) to get the flag!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 470



hacker@processes~starting-backgrounded-processes:~$ Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{cj9VM54_xljbS9wjfQFp-Gxcg26.dlDN4QDL0IzN0czW}

[1]+  Done                    /challenge/run
hacker@processes~starting-backgrounded-processes:~$ 
```

Flag: `pwn.college{cj9VM54_xljbS9wjfQFp-Gxcg26.dlDN4QDL0IzN0czW}`

## Process Exit Codes

