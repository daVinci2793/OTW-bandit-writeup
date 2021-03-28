# Bandit OverTheWire Wargame

## bandit0

### Simple ssh and cat command

    ssh bandit0@bandit.labs.overthewire.org -p 2220
    cat readme

#### Password

```
boJ9jbbUNNfktd78OOpsqOltutMc3MY1 
```

## bandit1

### cat command with special characters

    cat ./-

The ```./``` prefix is necessary in this context because the tac character is reserved for switches and options while using a command shell. If you were to try and simply write ``` cat - ``` the command line would say cat tac what? Then, anything you feed to it will just be outputted to stdout. The way to break out of this is the keyboard interrupt ```^C``` This interrupt will become indispensible in your future hacking ventures as it will allow you to break out of infinite loops, shells, commands you did not mean to run, hung programs, et cetera.

#### Password

```
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9 
```

## bandit2

### cat with spaces in the filename

    cat spaces\ in\ this\ filename
    or
    cat "spaces in this filename"

This is similar to the previous challenge in that you cannot simply run cat on the file in the directory. This is because the shell understands spaces a delimiters. That is to say, if you were simply try and ```cat space in this filename``` you would most likely get a bunch of errors saying ```cat: spaces: No such file or directory``` and so on. You can take two approaches either escape the special character with the backslash or *tell* the shell that it is a single string with quotation marks.

#### Password

    UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK 

## bandit3

### Changing directory with cd and listing hidden files

    cd inhere
    ls -a
    cat .hidden

First this challenge introduces you to recognizing and navigating directories, then it introduces you to the concept of a hidden file. Depending on your shell, you may notice that inhere is different color and even if you don't when you try to ```cat inhere``` you get an error informing you that inhere is a directory. You navigate in to the directory using the change directory command. Once you are in there and you run ```ls``` your screen will remain blank, this is your cue to try and display all files and folders in the directory. When you do, you will see a file called ```.hidden``` the dot prefix in linux indicates a hidden file or directory.

#### Password

    pIwrPrtPN36QITSp3EQaw936yaFoFgAB 

## bandit4

> "The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command."

### Introducing the ```file``` command

    file ./*
    cat ./-file07

The challenge text for this room suggest that you may want to learn more about the files in the inhere directory. On a windows machine, both you and the OS would look at the file extension to learn more about a file. On a linux machine, files types are just a way to make things more human-friendly. In linux, the os understands the file type by reading the file signature or magic-bytes. These are binary values that preface the file content informing the OS what it is about to read and maybe even how to understand it. The way that you would gain access to this information would be using the ```file``` command.

In this room, when you run the command with the wildcard it will output the file types for all the files in the directory. You will notice that one of them is different, and if you are familiar with computers you may recognize the acronym ASCII. ASCII is an encoding standard for readable characters. From the hint, we have found our file!

#### Password

    koReBOKuIDDepwhWk7jZC0RTdopnAYKh

## bandit5

> The password for the next level is stored somewhere on the server and has all of the following properties:
>
> * owned by user bandit7
> * owned by group bandit6
> * 33 bytes in size

### Introducing the
