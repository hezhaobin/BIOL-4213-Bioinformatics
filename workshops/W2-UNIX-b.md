---
title: Workshop for Unix, part I
author: Bin He
date: 2018-08-26
---

# Learning objectives

- Be able to read and write to a file
- Be able to use shell commands to extract and summarize information from a GFF file

## Opening with an example

- Use fastx to open up a linux desktop.
- Explain the problem: how to change multiple files' names with a specific pattern
- Demonstrate

# Intro to course
Jan will give ~20-30 min intro to the course

# Lecture (20 min)

## 1. What is UNIX

- How many people have heard of UNIX? In what context?
    - Anroid phone
    - Airplane entertainment system 
    - Mac OS: how many people uses Mac? How many of you know that Mac is built on a UNIX-like kernel
    - Chrome OS
![reboot](https://i.ytimg.com/vi/6-dFmp6yF7g/hqdefault.jpg)

- What is UNIX?
    - UNIX is a **time-sharing** operating system _kernel_: a program that controls the resources of a computer and allocates them among its users. It lets users run their programs; it controls the peripheral devices (discs, terminals, printers and the like); and it provides a file system that manages the long-term storage of information such as programs, data, and documents.

## 2. Why UNIX

- Remote computing -- your PC is just a "terminal" that you use to access networked resources (storage, computing nodes, printing etc.)
- Open source, encourage code sharing

## 3. UNIX history

- Written by Ken Thompson, with ideas and support from Rudd Canaday, Doug McIlroy, Joe Ossanna, and Dennis Ritchie in 1969. Ken Thompson and Dennis Ritchie rewrote the kernel in C in 1973, which gained popularity and essentially became what is UNIX today.
- BSD, developed outside of AT&T Labs
- Linus Torvalds wrote the Linux kernel, combined with the open source tools developed by the GNU project and the X-windows GUI by MIT, led to the flourishing Linux distributions.

## 4. Philosophy of UNIX

- The power of combining many programs doing just one thing, well
    
    UNIX is built on the belief that the power of an operating system lies more in the relationship between programs than the capability of any single program ==> a large number of _small_ programs with a simple, dedicated function + a convenient way to string a series of programs together to achieve a complex function (piping)

    for example, `cat FILE | grep "this" | wc -l` = count the number of lines that contain the word "this" in FILE

## 5. Files in UNIX

- Everything in UNIX system is a file

    - A file is a sequence of bytes. 
    - Anything in the system -- directories (?!), mail messages, your shopping list, any type of media, a networked printer -- each is just a sequence of bytes that either stores the content of a digital object or points to a physical device, hence a file, as far as the system and the programs in it are concerned.

- File permissions
    - Necessary for multi-user systems
    - Has three levels (there are extended attributes that are specific to certain systems)
    - Find out which group(s) you belong to
    - Store your password in plain text file??
    - There is a super-user

- UNIX directory structure
    ```bash
    /bin # Contains several basic programs
    /dev # Contains the files connecting to devices such as the keyboard, mouse and screen
    /etc # Contains configuration files
    /tmp # Contains temporary files
    /home/YOURNAME
    ```
# Workshop (30 min)

_Disclosure_ This workshop uses a lot of materials from the "Computing Skills for Biologists" book by Stefano Allesina and Madlen Wilmes, published by Princeton University Press

## 0. How to launch a terminal?

- Mac
- Linux
- Windows

## 1. How to talk to a Command Line Interface (CLI)?

Try talking to your UNIX CLI:

```bash
$ xeyes      # what do you see?
$ xclock     # how about this?
$ whoami     # and this?
$ hello      # this is getting interesting, let's try this
$ echo "Hello, my names is YOURNAME. Who are you?" # does the system answer your question?
$ echo $HOME # what does the echo command do?
$ echo $PS1  # this variable controls the format of the "prompt"
```

## 2. How to navigate the Directory System
    
**ls** = List files and subdirectories in the current location.

**cd** = Change Directory.

| Command | Meaning |
|---------|---------|
| `cd ..` | Move one directory up. |
| `cd /`  | Move to the root directory. |
| `cd ~`  | Move to the home directory. |
| `cd -`  | Go back to the directory you visited previously. |

**pwd** = Print Working Directory

**Exercise**

Please answer the questions below

```bash
$ cd ~ # where are you at now?
$ pwd  # what do you see, and does it remind you of any results you saw before?
$ cd / # where are you now? 
$ ls   # what do you see? What command can you use to go back to where you were?
```

**Exercise**

See what is in each subdirectory under the root

## 3. Anatomy of a unix command

Similar to the "settings" or "preference" pane you are used to in a __G__raphic __U__ser __I__nterface (GUI), e.g. Windows and Mac, commands in the CLI also have "options". They are typically specified after the main command. Let's use the `ls` command as an example

| Command | Meaning |
|---------|---------|
| `ls -a` | List all files (including hidden files). |
| `ls -l` | Return a long list with details on access permissions, the number of links to a file

**Exercise**

Try `ls -a` and `ls -l` in your home directory. What do you see?

## 4. Learn to get help

`man ls` gives you the manual for ls command. Try it.

## 5. Some useful resources

Unix cheatsheet [here](http://cheatsheetworld.com/programming/unix-linux-cheat-sheet/)

Useful keyboard bindings when entering in the command line interface

| Command| Meaning |
|--------|---------|
| Ctrl+A | Go to the beginning of the line. |
| Ctrl+E | Go to the end of the line. |
| Ctrl+L | Clear the screen. |
| Ctrl+U | Clear the line before the cursor position.  |
| Ctrl+K | Clear the line a er the cursor. |
| Ctrl+C | Kill the command that is currently running.  |
| Ctrl+D | Exit the current shell. |
| Alt+F  | Move cursor forward one word (in OS X, Esc+F).  |
| Alt+B  | Move cursor backward one word (in OS X, Esc+B). |
