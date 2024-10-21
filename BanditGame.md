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

### Level10 - Level11
`cat`ing the `data.txt` file, I recieved `VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==` as the contents. Running it through the base64
decoder, the decoded text was `The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`

### Level11 - Level12
Used `cat` on the `data.txt` file, got `Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4` as the contents.
Deciphered using rot13 cipher. The decoded cipher was `The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`

### Level12 - Level13
* `xxd`is used to make a hex dump or do the reverse. The `-r` is used to convert (or patch) hex dump into binary.  
* `file` is used to determine file type.  
* `gzip` is used to compress or expand files. More commands of the same type are `gunzip` and `zcat`.  `-d` decopresses the file.  
* `bzip2` is a block-sorting file compressor. `bzcat` decompresses file to stdout. `-d` flag forces `bzip2` to decompress.
* `tar` is an archiving utility. `-x` is used to extract files from an archive. `-f` says use archive file or device archive.  

For clearing this level, the mentioned were heavily used.

```
bandit12@bandit:~$ ls
data.txt
bandit12@bandit:~$ cat data.txt
00000000: 1f8b 0808 dfcd eb66 0203 6461 7461 322e  .......f..data2.
00000010: 6269 6e00 013e 02c1 fd42 5a68 3931 4159  bin..>...BZh91AY
00000020: 2653 59ca 83b2 c100 0017 7fff dff3 f4a7  &SY.............
00000030: fc9f fefe f2f3 cffe f5ff ffdd bf7e 5bfe  .............~[.
00000040: faff dfbe 97aa 6fff f0de edf7 b001 3b56  ......o.......;V
00000050: 0400 0034 d000 0000 0069 a1a1 a000 0343  ...4.....i.....C
00000060: 4686 4341 a680 068d 1a69 a0d0 0068 d1a0  F.CA.....i...h..
00000070: 1906 1193 0433 5193 d4c6 5103 4646 9a34  .....3Q...Q.FF.4
00000080: 0000 d320 0680 0003 264d 0346 8683 d21a  ... ....&M.F....
00000090: 0686 8064 3400 0189 a683 4fd5 0190 001e  ...d4.....O.....
000000a0: 9034 d188 0343 0e9a 0c40 69a0 0626 4686  .4...C...@i..&F.
000000b0: 8340 0310 d340 3469 a680 6800 0006 8d0d  .@...@4i..h.....
000000c0: 0068 0608 0d1a 64d3 469a 1a68 c9a6 8030  .h....d.F..h...0
000000d0: 9a68 6801 8101 3204 012a ca60 51e8 1cac  .hh...2..*.`Q...
000000e0: 532f 0b84 d4d0 5db8 4e88 e127 2921 4c8e  S/....].N..')!L.
000000f0: b8e6 084c e5db 0835 ff85 4ffc 115a 0d0c  ...L...5..O..Z..
00000100: c33d 6714 0121 5762 5e0c dbf1 aef9 b6a7  .=g..!Wb^.......
00000110: 23a6 1d7b 0e06 4214 01dd d539 af76 f0b4  #..{..B....9.v..
00000120: a22f 744a b61f a393 3c06 4e98 376f dc23  ./tJ....<.N.7o.#
00000130: 45b1 5f23 0d8f 640b 3534 de29 4195 a7c6  E._#..d.54.)A...
00000140: de0c 744f d408 4a51 dad3 e208 189b 0823  ..tO..JQ.......#
00000150: 9fcc 9c81 e58c 9461 9dae ce4a 4284 1706  .......a...JB...
00000160: 61a3 7f7d 1336 8322 cd59 e2b5 9f51 8d99  a..}.6.".Y...Q..
00000170: c300 2a9d dd30 68f4 f9f6 7db6 93ea ed9a  ..*..0h...}.....
00000180: dd7c 891a 1221 0926 97ea 6e05 9522 91f1  .|...!.&..n.."..
00000190: 7bd3 0ba4 4719 6f37 0c36 0f61 02ae dea9  {...G.o7.6.a....
000001a0: b52f fc46 9792 3898 b953 36c4 c247 ceb1  ./.F..8..S6..G..
000001b0: 8a53 379f 4831 52a3 41e9 fa26 9d6c 28f4  .S7.H1R.A..&.l(.
000001c0: 24ea e394 651d cb5c a96c d505 d986 da22  $...e..\.l....."
000001d0: 47f4 d58b 589d 567a 920b 858e a95c 63c1  G...X.Vz.....\c.
000001e0: 2509 612c 5364 8e7d 2402 808e 9b60 02b4  %.a,Sd.}$....`..
000001f0: 13c7 be0a 1ae3 1400 4796 4370 efc0 9b43  ........G.Cp...C
00000200: a4cb 882a 4aae 4b81 abf7 1c14 67f7 8a34  ...*J.K.....g..4
00000210: 0867 e5b6 1df6 b0e8 8023 6d1c 416a 28d0  .g.......#m.Aj(.
00000220: c460 1604 bba3 2e52 297d 8788 4e30 e1f9  .`.....R)}..N0..
00000230: 2646 8f5d 3062 2628 c94e 904b 6754 3891  &F.]0b&(.N.KgT8.
00000240: 421f 4a9f 9feb 2ec9 83e2 c20f fc5d c914  B.J..........]..
00000250: e142 432a 0ecb 0459 1b15 923e 0200 00    .BC*...Y...>...
bandit12@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit13 bandit12 2583 Sep 19 07:08 data.txt
bandit12@bandit:~$ file data.txt
data.txt: ASCII text
bandit12@bandit:~$ mkdir /tmp/lvl12
mkdir: cannot create directory ‘/tmp/lvl12’: File exists
bandit12@bandit:~$ mkdir /tmp/lvll12
bandit12@bandit:~$ cd /tmp/levll12
-bash: cd: /tmp/levll12: No such file or directory
bandit12@bandit:~$ cd /tmp/lvll12
bandit12@bandit:/tmp/lvll12$ cp ~/data.txt .
bandit12@bandit:/tmp/lvll12$ ls
data.txt
bandit12@bandit:/tmp/lvll12$ xxd -r data.txt data0
bandit12@bandit:/tmp/lvll12$ file data0
data0: gzip compressed data, was "data2.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 574
bandit12@bandit:/tmp/lvll12$ mv data0 data0.gz
bandit12@bandit:/tmp/lvll12$ gzip -d data0.gz
bandit12@bandit:/tmp/lvll12$ ls
data0  data.txt
bandit12@bandit:/tmp/lvll12$ file data0
data0: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/lvll12$ mv data0 data0.bz2
bandit12@bandit:/tmp/lvll12$ bzip2 -d data0.bz2
bandit12@bandit:/tmp/lvll12$ file data0
data0: gzip compressed data, was "data4.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 20480
bandit12@bandit:/tmp/lvll12$ mv data0 data0.gz
bandit12@bandit:/tmp/lvll12$ gzip -d data0.gz
bandit12@bandit:/tmp/lvll12$ file data0
data0: POSIX tar archive (GNU)
bandit12@bandit:/tmp/lvll12$ mv data0 data0.tar
bandit12@bandit:/tmp/lvll12$ man tar
bandit12@bandit:/tmp/lvll12$ man xxd
bandit12@bandit:/tmp/lvll12$ man file
bandit12@bandit:/tmp/lvll12$ man gzip
bandit12@bandit:/tmp/lvll12$ man bzip2
bandit12@bandit:/tmp/lvll12$ man tar
bandit12@bandit:/tmp/lvll12$ tar -xf data0.tar
bandit12@bandit:/tmp/lvll12$ ls
data0.tar  data5.bin  data.txt
bandit12@bandit:/tmp/lvll12$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/lvll12$ tar -xf data5.bin
bandit12@bandit:/tmp/lvll12$ ls
data0.tar  data5.bin  data6.bin  data.txt
bandit12@bandit:/tmp/lvll12$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/lvll12$ mv data6.bin data6.bz2
bandit12@bandit:/tmp/lvll12$ bzip2 -d data6.bz2
bandit12@bandit:/tmp/lvll12$ ls
data0.tar  data5.bin  data6  data.txt
bandit12@bandit:/tmp/lvll12$ file data6
data6: POSIX tar archive (GNU)
bandit12@bandit:/tmp/lvll12$ mv data6 data6.tar
bandit12@bandit:/tmp/lvll12$ tar -xf data6.tar
bandit12@bandit:/tmp/lvll12$ ls
data0.tar  data5.bin  data6.tar  data8.bin  data.txt
bandit12@bandit:/tmp/lvll12$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/lvll12$ mv data8.bin data8.gz
bandit12@bandit:/tmp/lvll12$ gzip -d data8.g
gzip: data8.g.gz: No such file or directory
bandit12@bandit:/tmp/lvll12$ gzip -d data8.gz
bandit12@bandit:/tmp/lvll12$ ls
data0.tar  data5.bin  data6.tar  data8  data.txt
bandit12@bandit:/tmp/lvll12$ file data8
data8: ASCII text
bandit12@bandit:/tmp/lvll12$ cat data8
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
bandit12@bandit:/tmp/lvll12$
```

Password: `FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

### Level13 - Level14
