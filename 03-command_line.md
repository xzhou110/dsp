# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* pwd: show current working directory path
* mkdir: creating a directory
* rm -rf: deleting a directory
* touch: creating a file using `touch` command
* rm: deleting a file
* mv: renaming a file
* ls -a: listing hidden files
* cp: copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

> > 

---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls`: list files in current directory  
`ls -a`  : list all files
`ls -l`  : displays the listing in long format
`ls -lh`  : disply in long format, and file sizes using human frienly units
`ls -lah`  : all files, long format, file sizes
`ls -t`  : list in the order of time
`ls -Glp`  : displays long format listing but excludes owner name, long format, directory names

> > 

---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

> > 
ls -a
ls -d
ls -c
ls -l
ls -r


---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

> > Building an execution pipeline from standard input

echo "abc" | xargs mkdir
 

