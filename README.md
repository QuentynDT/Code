
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

We first use cd inhere to enter the inhere directory. Then, we use ls to view all the files. To check a file that is 1033 bytes in size, not executable, and human readable, we can use the listed command. Now that we know the password is in file2 in the directory maybehere07, we can use cd and cat to read the password. 

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


