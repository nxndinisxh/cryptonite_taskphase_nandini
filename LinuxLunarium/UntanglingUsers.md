# Untangling Users

There are many users on a typical Linux system. The full list can using the `/etc/passwd` file.  
We can see **hacker** and **root**, along with a bunch of others. Many are there for historical reasons, some are service accounts to support various installed software, and some are "utility" accounts (e.g., the **nobody** user is used to ensure that, e.g., a program runs without any special privileges).

## Becoming root with su

`su` is a setuid binary.  
Running as root, it can start a root shell! Of course, `su` is discerning: before allowing the user to elevate privileges to root, it checks to make sure that the user knows the root password
To solve this challenge, Password is `hit-the-planet`.
```
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{o0R8kuqVodLpTXKaVz1yXDXrxTm.dVTN0UDL0IzN0czW}
root@users~becoming-root-with-su:/home/hacker# 
```

Flag: `pwn.college{o0R8kuqVodLpTXKaVz1yXDXrxTm.dVTN0UDL0IzN0czW}`

## Other users with su

This needed to switch to `zardus` user and then run `/challenge/run` for the flag. Password was: `dont-hack-me`.
Flag: `pwn.college{8p0t-LNUgnDimqqJuxTH3TAlzMb.dZTN0UDL0IzN0czW}`

## Cracking Passwords

This level is about how to get access to passwords using the `/etc/shadow` 

```
hacker@users~cracking-passwords:~$ john ./challenge/shadow-leak
Created directory: /home/hacker/.john
stat: ./challenge/shadow-leak: No such file or directory
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04894g/s 285.0p/s 285.0c/s 285.0C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{ANp4dij0AEaQvWP5J5FhEZ2iCGk.ddTN0UDL0IzN0czW}
zardus@users~cracking-passwords:/home/hacker$ 
```

Flag: `pwn.college{ANp4dij0AEaQvWP5J5FhEZ2iCGk.ddTN0UDL0IzN0czW}`

## Using sudo

Just use `sudo` to read the flag

```
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{4mYze4I3PUGljvvCFOADOcE0MUQ.dhTN0UDL0IzN0czW}
hacker@users~using-sudo:~$ 
```
Flag: `pwn.college{4mYze4I3PUGljvvCFOADOcE0MUQ.dhTN0UDL0IzN0czW}`

# END