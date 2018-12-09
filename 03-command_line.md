# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

## Questions

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  

* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

### My Cheat Sheet

1. * `pwd`  
2. * `mkdir <dirname>`  
3. * `rmdir <dirname>` or `rm -rf <dirname>`  
4. * `touch <filename>`  
5. * `rm <filename>`  
6. * `mv <old_name> <new_name>`  
7. * `ls -d .*`  
8. * `cp [<source_dir>/]<source_file> <target_dir>`  
9. * `find . -type f -exec grep -il <string>`  
10. * ``cp -p <filename> <filename>.`date +%Y%m%d` ``[**¹**](#footnotes)

---

### Q2.  List Files in Unix

What do the following commands do:  
`ls`  
`ls -a`  
`ls -l`  
`ls -lh`  
`ls -lah`  
`ls -t`  
`ls -Glp`  

> > If no additional options are included, all of these commands will operate on the current directory
> >
> > 1. List directory content, excluding those entries that start with a dot (.)
> > 2. List everything, including entries that start with a dot (.)
> > 3. List directory content, excluding dot entries, in a long format
> > 4. List directory content, excluding dot entries, in a long format and display size information in “human readable” format (e.g. KB, MB, GB, etc)
> > 5. The same as #4, but include entries that start with a dot
> > 6. The same as #1 but the results are sorted by time (newest to oldest); I personally prefer `ls -alrt`
> > 7. List directory content, excluding dot entries, in a long format; color code the results; add a trailing slash (/) if the entry is a directory

---

### Q3.  More List Files in Unix

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

> > * `ls -alrt`
> > * `ls -1`
> > * `ls -ld`
> > * `ls -alb`
> > * `ls -alq`

---

### Q4.  Xargs

What does `xargs` do? Give an example of how to use it.

> > The `xargs` command reads white space delimited strings from standard input and uses what it finds as parameters to a command. It can be used to concatenate multi-line input to run against a single command, for example:
> >
> > `ls -1 | xargs touch` - Update the timestamp of everything in the current directory
> >
> > It can also be used to run the same command across multiple inputs, for example:
> >
> > `` ls | xargs -n1 -I{} cp -p {} {}.`date +%Y%d%m` ``[**¹**](#footnotes) - Makes a date stamped backup of everything in the current directory

#### Footnotes

¹ You may need to enclose the format string in single quotes, `‘+%Y%m%d’`, if % is a shell escape (e.g. in csh/tcsh)
