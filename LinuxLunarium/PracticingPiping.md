# Practicing Piping

This module will teach about input and output redirection.

## Redirecting output

We can run echo PWN > COLLEGE to write the message PWN to the file COLLEGE. Running this gives us the flag.
Flag: pwn.college{4ZNcB5lDNFTWnVDfeOXRIaT4Cdi.dRjN1QDL0IzN0czW}

## Redirecting more Ouptut

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