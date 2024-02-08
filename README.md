
# Bandit Levels 0 to 18 

This file contains a write-up of the first 18 levels.

## Level 0 -> Level 1

To read the contents of the file readme, we use the 'cat' command. 

### Commands

    ls
    cat readme

Password for level 1:
    
    NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL


## Level 1 -> Level 2

To read the contents of the file -, we use the 'cat' command. Since it fails to read the special character, we use a ./ to use the command properly. 

### Commands
    ls
    cat ./-

Password for level 2:
    
    rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

## Level 2 -> Level 3

To read the contents of the file spaces in this filename, we use the 'cat' command. Since it does not work due to the spaces, we must use a backslash "\\" between each word to use the command properly.

### Commands

    ls
    cat spaces\ in\ this\ filename

Password for level 3:
    
    aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

## Level 3 -> Level 4

We first use cd inhere to enter the inhere directory. Then, we use ls. .hidden does not show up as it is hidden. We can do ls -a to show all files, which displays .hidden. Then we can use cat ./.hidden to read the file.

### Commands
    
    ls
    cd inhere
    ls -a
    cat ./.hidden

Password for level 4:
    
    2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe


## Level 4 -> Level 5

We first use cd inhere to enter the inhere directory. Then, we use ls to view all 10 files. To find the contents of all ten, we take the files as file0*. file07 is the one with the password, so we can read it using the cat command. 

### Commands
    
    ls
    cd inhere
    find ./-file0*
    cat ./-file07

Password for level 5:
    
    lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

## Level 5 -> Level 6

We first use cd inhere to enter the inhere directory. Then, we use ls to view all the files. To check a file that is 1033 bytes in size, not executable, and human readable, we can use the listed command. Now that we know the password is in file2 in the directory maybehere07, we can use cat to read the password. 

### Commands

    ls
    find -type f -size 1033c
    cat maybehere07/.file2

Password for level 6:
    
    P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

## Level 6 -> Level 7

The password file has the following properties, it is owned by user bandit7, owned by group bandit6, and 33 bytes in size. Using the listed command gives a permission denied error. To fix this, we append a command that hides all error messages. Once we find the file, we can read it using cat.

### Commands

    ls
    find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
    cat /var/lib/dpkg/info/bandit7.password

Password for level 7:
    
    z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

## Level 7 -> Level 8

Data.txt is a large file. To find the word millionth in it, the grep command is used to find a pattern as follows.

### Commands

    ls
    grep millionth data.txt

Password for level 8:
    
    TESKZC0XvTetK0S9xNwm25STk5iWrBvP

## Level 8 -> Level 9

Data.txt is a large file. To find the line that occurs only once, we use the sort command, then filter for unique lines by using uniq -u as follows.

### Commands

    ls
    sort data.txt | uniq -u

Password for level 9:
    
    EN632PlfYiZbn3PhVK3XOGSlNInNE00t

## Level 9 -> Level 10

Data.txt is a large file. To find the line that is human readable and has several = signs before it, we use the strings command, followed by the grep -o command, then we use the "==*.*" to find all human readable strings after an = sign.

### Commands

    ls
    strings data.txt | grep -o '==*.*'

Password for level 10:
    
    G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s

## Level 10 -> Level 11

Data.txt is in base64. To decode it, we use the base64 command, followed by cat to print the decoded password.

### Commands

    ls
    base64 -d data.txt | cat -

Password for level 11:
    
    6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

## Level 11 -> Level 12

Data.txt is in ROT13. To decode it, we use the tr command to replace one set of characters with another set. The most efficient way to do this is to define the ranges. For example, the range of capital letters is 'A-Z', but the range of capital letters in ROT13 is 'N-ZA-M'.

### Commands

    ls
    cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

Password for level 12:
    
    JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

## Level 12 -> Level 13

The file has been heavily compressed. First we must create a temporary directory using /tmp/modnar and copy the file there using the cp command. Then, we revert the hexdump (hex1) to get the actual data (datax). This file can be determined to be a gzip file due to the first bytes being 1f8b. The file is converted to a .gz file and decompressed.  This file can then be determined to be a bzip2 file due to the first bytes being 425a 68. The file is converted to a .bz2 file and decompressed. This file can then be determined to be a gzip file due to the first bytes being 1f8b. The file is converted to a .gz file and decompressed. The file now has a string in it, data5.bin. It can be extracted using the tar command. We use mv to convert it to a tar file and extract the data5.bin file using -xf. data5.bin seems to contain a file named data6.bin. It can be extracted using the tar command. We can extract the data6.bin file using -xf. data6.bin can be determined to be a bzip2 file due to the first bytes being 425a 68. The file is converted to a .bz2 file and decompressed. This file once again has a string called data8.bin inside it which can be extracted using the tar command. Finally, data8.bin is gzip compressed and can be decompressed the same way. data8 is a text file that is read using the cat command.

### Commands

    ls
    mkdir /tmp/modnar
    cp data.txt /tmp/modnar/data
    cd /tmp/modnar
    cat data | head

    mv data.txt hex1
    xxd -r hex1 datax
    
    mv datax datax.gz
    gzip -d datax.gz
    
    mv datax datax.bz2
    bzip2 -d datax.bz2

    mv datax datax.gz
    gzip -d datax.gz

    mv datax datax.tar
    tar -xf datax.tar

    tar -xf data5.bin

    bzip2 -d data6.bin

    tar -xf data6.bin.out

    mv data8.bin data8.gz
    gzip -d data8.gz

    cat data8

Password for level 13:
    
    wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
    
## Level 13 -> Level 14

The file can only be accessed by a specific user. To solve this, we connect to bandit14 using local host.

### Commands

    ls
    ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220

Password for level 14:
    
N/A

## Level 14 -> Level 15

The intermediate password is stored in the config directory a.k.a. /etc, in bandit password (bandit_pass) in the file named bandit14. Once we find the intermediate password, we can use the ncat command to connect to the port 30000, and submit the intermediate password to get the password.

### Commands

    ls
    cat /etc/bandit_pass/bandit14
    nc localhost 30000

Intermediate Passwword:

    fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

Password for level 15:
    
    jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

## Level 15 -> Level 16

To use ssl encryption, we use the openssl command. s_client is used to connect to the port via ssl encryption

### Commands

    openssl s_client -connect localhost:30001

Password for level 16:
    
    JQttfApK4SeyHwDlI9SXGR50qclOAil1

## Level 16 -> Level 17

We have to connect to any one of the ports from 31000 to 32000. To scan the ports we can use the nmap command. When this command is used, it yields 5 ports. Checking them, we are able to obtain an ssh key. 

### Commands

    nmap localhost -p T:31000-32000
    openssl s_client -connect localhost:31691

Password for level 17:
    
[sshkey.private](https://github.com/QuentynDT/sshkey/edit/main/README.md)

## Level 17 -> Level 18

We have to connect to the shell using the sshkey. Once connected, we must find the difference between the old and new passwords using diff function. The new line is the password. 

### Commands

    diff password.old password.new

Password for level 18:
    
    hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg

## Level 18 -> Level 19

Here we cannot establish a continuous connection to the server. Thus we must perform all our actions in the same line as the line to enter the port.

### Commands

    ssh bandit18@bandit.labs.overthewire.org -p 2220 ls
    ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme

Password for level 19:
    
    awhqfNnAbc1naukrpqDYcF95h7HoMTrC










