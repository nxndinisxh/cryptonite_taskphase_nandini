# Practicing Piping

This module will teach about input and output redirection.

## Redirecting output

We can run echo PWN > COLLEGE to write the message PWN to the file COLLEGE. Running this gives us the flag.
Flag: pwn.college{4ZNcB5lDNFTWnVDfeOXRIaT4Cdi.dRjN1QDL0IzN0czW}

## Redirecting more Ouptut

In this challenge, we are required to redirect the output of the command `/challenge/run` into a file called `myflag`.

```
hacker@piping~redirecting-more-output:~$ /challenge/run
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[FAIL] You did not satisfy all the execution requirements.
[FAIL] Specifically, you must fix the following issue:
[FAIL]   You have not redirected anything for this process' stdout.
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ ls
COLLEGE  Desktop  c  college  myflag  not-the-flag
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{o-v_KOXeFjIMV6MUEclSFtjh9s2.dVjN1QDL0IzN0czW}

```

Flag: pwn.college{o-v_KOXeFjIMV6MUEclSFtjh9s2.dVjN1QDL0IzN0czW}

## Appending output

To solve this challenge, we are required to redirect the output of the command `/challenge/run` in append mode (>>) to `/home/hacker/the-flag` to get the complete flag.

```
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ ls
COLLEGE  Desktop  c  college  myflag  not-the-flag  the-flag
hacker@piping~appending-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{o-v_KOXeFjIMV6MUEclSFtjh9s2.dVjN1QDL0IzN0czW}

hacker@piping~appending-output:~$ cat the-flag
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

```

Flag: pwn.college{Al6PMN0NjN9gg6UOq9tw6I1-g5G.ddDM5QDL0IzN0czW}

## Redirecting errors

In this challenge, I ran `/challenge/run > myflag 2> instructions` to redirect output and errors respectively. 

```

hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ ls
COLLEGE  Desktop  c  college  instructions  myflag  not-the-flag  the-flag
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{4YNY3MFAPb-FrnYvTX9lnFS5V_F.ddjN1QDL0IzN0czW}

```
Flag: pwn.college{4YNY3MFAPb-FrnYvTX9lnFS5V_F.ddjN1QDL0IzN0czW}

## Redirecting Input

In this challenge, we were required to redirect a file called `PWN` that contains `COLLEGE` to the command `/challenge/run` to get our flag.

I ran `echo COLLEGE > PWN` to create the file that we need to redirect.

Then I ran `/challenge/run < PWN` to get my flag

```

hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{AVsW-7KAc2dnb-ZKWVEkbDZQ5vv.dBzN1QDL0IzN0czW}
hacker@piping~redirecting-input:~$ 

```

Flag: pwn.college{AVsW-7KAc2dnb-ZKWVEkbDZQ5vv.dBzN1QDL0IzN0czW}

## Grepping stored results

This challenge required us redirect the output of `/challenge/run` to `/tmp.data.txt` and then search for our flag in the data file using the `grep` command.

```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{sj5YS3wixxOfr0nTW5JWz7waAri.dhTM4QDL0IzN0czW}
hacker@piping~grepping-stored-results:~$ 

```

Flag: pwn.college{sj5YS3wixxOfr0nTW5JWz7waAri.dhTM4QDL0IzN0czW}

## Grepping live output

Like in the last challenge, we were required to look for our flag in the output using the piping (|) operator.

I run the command `/challenge/run | grep pwn.college` where | is the piping operator to get to the flag.

```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{U1UhHkZjIZf7he_TMS485RiKaLX.dlTM4QDL0IzN0czW}
hacker@piping~grepping-live-output:~$ 

```
Flag: pwn.college{U1UhHkZjIZf7he_TMS485RiKaLX.dlTM4QDL0IzN0czW}

## Grepping errors

In this challenge, we were asked to look for our flag in the error stream of the `/challenge/run` command using `grep`.

Running the `/challenge/run 2>&1 | grep pwn.college` directly gave the flag.

```
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{QTiHKcY1Xwh1m222ts0avBh5jU_.dVDM5QDL0IzN0czW}
hacker@piping~grepping-errors:~$ 

```
Flag: pwn.college{QTiHKcY1Xwh1m222ts0avBh5jU_.dVDM5QDL0IzN0czW}

## Duplicating piped data with tee

In this challenge, we were supposed to pipe the output of `/challenge/pwn` into `/challenge/college` but we also need to read the output of `/challenge/pwn` to find out the argument that will give the flag.

```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee /challenge/college
Processing...
You are trying to use 'tee' *instead* of /challenge/college. Use it *between* 
/challenge/pwn and /challenge/college!
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee' 
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee output | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat output
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "I8zwnXSY"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret I8zwnXSY
Processing...
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee' 
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret I8zwnXSY | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{I8zwnXSY0YscsnzNTE7JA7OKSum.dFjM5QDL0IzN0czW}
hacker@piping~duplicating-piped-data-with-tee:~$ 

```
Flag: pwn.college{I8zwnXSY0YscsnzNTE7JA7OKSum.dFjM5QDL0IzN0czW}

## Writing to multiple programs

In this challenge, we need to pipe the output of `/challenge/hack` into both `/challenge/the` and `/challenge/planet`.

```

hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{8q28F06afd_xeZG5v7G7bs7SYca.dBDO0UDL0IzN0czW}

```

Flag: pwn.college{8q28F06afd_xeZG5v7G7bs7SYca.dBDO0UDL0IzN0czW}

## Split-piping stderr and stdout

Here, we were supposed to pipe out the standard error of `/challenge/hack` into `/challenge/the` and the standard output into `/challenge/planet`

```

hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) | /challenge/planet
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{QesHRHoaaNe_Y2WkVhT0IDayHEa.dFDNwYDL0IzN0czW}
hacker@piping~split-piping-stderr-and-stdout:~$ 

```
Flag: pwn.college{QesHRHoaaNe_Y2WkVhT0IDayHEa.dFDNwYDL0IzN0czW}