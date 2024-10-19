# Bandit Game

We have to login into level 0 using `ssh bandit0@bandit.labs.overthewire.org -p 2220` and password `bandit0`

### Level0 - Level1
Used `cat readme` to get the clear the level and get the password to next level `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`

### Level1 - Level2
Used `cat ./-` for the password to the next level `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`, the password was in the `-` of the home directory.

### Level2 - Level3
Used double quotes to specify the file name because the name had spaces in it `cat "spaces in this filename"`  
Password for the next level: `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`

### Level3 - Level4 
Used the following commands to get the flag:
```
bandit3@bandit:~$ ls ./inhere -a
.  ..  ...Hiding-From-You
bandit3@bandit:~$ cat ./inhere/...Hiding-From-You 
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```
Password for the next level: `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

### Level4 - Level5
`cd`ed to `inhere`  
`ls -h`ed to list the files in the directory.  
Used `cat ./-file00` to `cat ./-file09` to find the password in `-file07`  
Password: `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

### Level5 - Level6
`cd`ed into `inhere` and used `find -readable -size 1033c` to get the correct file.  
Used `cat` to find the password
Password: `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

### Level6 - Level7
Used `find / -user bandit7 -group bandit6 -size 33c`  
Got a list of many files I was denied access to, but found `/var/lib/dpkg/info/bandit7.password` which I had access to.  
`cat`ed it to get the password.  
Password: `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

### Level7 - Level8
Used `cat data.txt | grep millionth` to get the password  
Password: `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

### Level8 - Level9
`uniq` is used to report or omit repeated lines. An argument `-u` can used to print the unique line in the file. 
I piped the output of `uniq -u` into the sorted version of `data.txt` because `uniq` does not detect repeated lines unless they are adjacent.  
Password: `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

### Level9 - Level10
`strings` is used to print the sequences of printable characters in files.  
I used `strings data.txt | grep =` to get to my password.  
Password: `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`