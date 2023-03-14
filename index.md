# Artur Rodrigues Lab Report 5 - Exploration of Additional Terminal Commands
I really enjoyed writing Lab Report 3 because I got to explore some more about terminal commands, and so for Lab Report 5, I have chosen to explore more about the `diff` command. The diff command is used to, as the name suggests, detect/locate differences between files. This may very well come in handy when I am using my personal linux machine via command line or if I end up doing some work on a remote environment.

## The `diff` command with no flags
The `diff` command by default will display the contents of both files omitting any lines that are equal in both files. Lines prefixed with `<` are lines in the first specified file, and lines prefixed with `>` are lines in the second specified file.

Source: Manual page of `diff` command

```
[cs15lwi23asd@ieng6-203]:~:541$ diff test1.txt test2.txt
1,3c1,3
< Hello there!
< This is a test to see how diff works!
< I hope this will work properly!
---
> Hello There!
> This is a test to se how dif works!
> This may or may not work properly.
```

In the example above, we run the `diff` command with no flags to show us which lines in `test1.txt` and `test2.txt` differ.

## The `diff` command with `-q` flag
The `-q` flag works very simply by informing us of whether or not the two specified files differ. If they do, it will simply output `Files <files1> and <file2> differ`, if they do not differ, then it will not output anything. This may seem like a pretty silly or useless flag, however, it is very useful to first determine if two files differ at all, and if we find out that they do, then we can use the `diff` command with other flags to better locate the differences.

Source: Manual page of `diff` command

```
[cs15lwi23asd@ieng6-203]:~:515$ diff -q test1.txt test2.txt
Files test1.txt and test2.txt differ
```

In the example above, we run the `diff` command with the `-q` flag to check whether or not `test1.txt` and `test2.txt` differ.

## The `diff` command with `-y` flag
The `-y` flag will output both files side by side to the terminal so that we can see each file's contents at the same time. This flag will not spot differences for us, however, it will allow us to see any present differences between the two files.

Source: Manual page of `diff` command

```
[cs15lwi23asd@ieng6-203]:~:517$ diff -y test1.txt test2.txt
Hello there!                                           | Hello There!
This is a test to see how diff works!                  | This is a test to se how dif works!
I hope this will work properly!                        | This may or may not work properly.
```

In the example above, we run the `diff` command with the `-y` flag to see the contents of `test1.txt` and `test2.txt` side by side.

## The `diff` command with `-i` flag
The `-i` flag will ignore case, and display the contents of both files omitting any lines that are equal in both files. Lines prefixed with `<` are lines in the first specified file, and lines prefixed with `>` are lines in the second specified file. 

Source: Manual page of `diff` command

```
[cs15lwi23asd@ieng6-203]:~:542$ diff -i test1.txt test2.txt
2,3c2,3
< This is a test to see how diff works!
< I hope this will work properly!
---
> This is a test to se how dif works!
> This may or may not work properly.
```

In the example above, we are running the `diff` command with the `-i` flag to display the lines which differ between the files while ignoring case.

## The `diff` command with `-c` flag
The `-c` flag will display the lines in each of the files, however, it will prefix lines that are different with a `!`, lines that exist in the second file, but not in the first with a `+`, and lines that exist in the first file, but not in the second file with a `-`.

Source: https://www.computerhope.com/unix/udiff.htm

```
[cs15lwi23asd@ieng6-203]:~:570$ diff -c test1.txt test2.txt
*** test1.txt   Mon Mar 13 18:36:18 2023
--- test2.txt   Mon Mar 13 18:38:24 2023
***************
*** 1,9 ****
! Hello there!
  This text is fine.
  This text is also fine.
  car
- train
  bike
  boat
! This is a test to see how diff works!
! I hope this will work properly!
--- 1,9 ----
! Hello There!
  This text is fine.
  This text is also fine.
  car
  bike
+ train
  boat
! This is a test to se how dif works!
! This may or may not work properly.
```

In the example above, we ran the `diff` command on `test1.txt` and `test2.txt` and these files' contents were displayed to us following the previously mentioned prefix additions to give us more information on the differences between the files.