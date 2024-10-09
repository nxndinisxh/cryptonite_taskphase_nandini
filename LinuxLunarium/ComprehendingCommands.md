# Comprehending Commands

Here, we learnt some more Linux Commands.

## cat: not the pet, but the command!

cat is a crucial command among the Linux commands.
cat will concatenate (hence the name) multiple files if provided multiple arguments.

Flag for this challenge was obtained by running `cat` command with the argument `flag`

Flag: pwn.college{Ybt933Lykm0zJ8MskQ_QvZ3pjLh.dFzN1QDL0IzN0czW}

## catting absolute paths

In this challenge we learnt that `cat` cmd can also have arguments as absolute paths.
Flag for this challenge was obtained after running the `cat /flag` cmd.
Flag: pwn.college{wxRhS5apb3vK8-L4znl9tKno6h5.dlTM5QDL0IzN0czW}

## more catting practice

In this challenge, we weren't allowed to use the `cd` cmd but the flag was inside the  /lib/llvm-10/include/flag file, so I used the `cat` cmd followed by the file's absolute path as the argument which handed me the flag.
FLag: pwn.college{8KmwbSvAsnG1r8oiOTVJOroWkhL.dBjM5QDL0IzN0czW}

## grepping for a needle in a haystack

This challenge required me to find the flag using the `grep` cmd.
`grep` will search the file for lines of text containing text mentioned with the file path the text is present in  and print them to the console.

Here, the Flag was obtained by running `grep pwn.college /challenge/data.txt`
Flag: pwn.college{c52Np_jTMWeREx0kwSHXvg6pSwE.ddTM4QDL0IzN0czW}

## listing files

This challenge taught how to list the names of the files in a directory
`ls` cmd without arguments lists the names of the files in the current directory and argument in form of path of the directory lists the names of the files in that directory

Flag for this challenge was obtained by listing the files in the `/challenge` file and then invoking `/challenge/31593-renamed-run-11486` 
Flag: pwn.college{sPDPLkkV8s0fHwLRn6ak3E4bfln.dhjM4QDL0IzN0czW}

## touching files

This challenge taught haow to create files in a directory using the `touch` cmd. In this level, two files were created : /tmp/pwn and /tmp/college, and  `/challenge/run` was run to get the flag.
Flag: pwn.college{McSF4NOVYtpK_eX5ON7It8RQVMM.dBzM4QDL0IzN0czW}

## removing files

Here, we learnt how to delete a file using the `rm` cmd.
Flag was obtained by deleting the file using the `rm delete_me` cmd and then checking using the `/challenge/check` cmd.
Flag: pwn.college{I6EUTjUY4Y7xWQQhy5Ydss7-Rgw.dZTOwUDL0IzN0czW}

## hidden files

`ls` doesn't list all the files by default. Linux has a convention where files that start with a `.` don't show up by default in `ls` and in a few other contexts. To view them with `ls`, you need to invoke `ls` with the `-a` flag.

To get the flag, I run the `cd /` cmd to get into the `/` directory as mentioned in the challenge.
I got a file named `.flag-92882954213198` using the `ls -a` cmd. 
To find the flag inside this file I read the file using the `cat .flag-92882954213198` cmd.

Flag: pwn.college{sE5djdWu00Tjayf9bQLFtXTKLWP.dBTN4QDL0IzN0czW}

## An Epic Filesystem Quest

In this Level, I was required to use the `cd`, `ls` and `cat` commands to their full potential

There were three types of files that were to be accessed from different paths without `cd`ing into the directory and with `cd`ing into the files.
The hidden files were to be `cat`ed using the `ls -a` cmd for that directory after `cd`ing into it.
The trapped files were to be `cat`ed using the ls cmd with the path as the argument.

After a series of `cat`ing, `ls`ing and `cd`ing, I finallt found the flag.

Flag: pwn.college{IMnWqv3dh6jiH-SQV8Lclbr5kBI.dljM4QDL0IzN0czW}

## making directories

In this level, I was required to make a `pwn` directory in the `/tmp` directory using the `mkdir` command and then create a `college` file in it using the `touch` command.

Flag: pwn.college{w5No_Z9ANuSyly95vCepOz32s3N.dFzM4QDL0IzN0czW}

## finding files

In this level, I run the `find` cmd for the `/` directory to find the `flag` file in which the flag to this challenge was saved.
Running the `flag / -name flag` gave me a list of files with `flag` files in them
`cat`ing through them gave me the flag in the `/usr/local/lib/python3.8/dist-packages/sympy/logic/utilities` directory

Flag: pwn.college{0i43I8A0jUtjoMJW3a5kBuOV0Vq.dJzM4QDL0IzN0czW}

## linking files

In this challenge, we learn about linking.

Links come in two flavors: hard and soft (also known as symbolic) links.

To solve this challenge, I tried `/challenge/catflag` but it read the `/home/hacker/not-the-flag` file, I tried `ln -s /flag /home/hacker/not-the-flag` and then tried the `/challenge/catflag` which gave me the flag.

Flag: pwn.college{UE-EiLpLa1mawL4cZPulmG2AEXG.dlTM1UDL0IzN0czW}