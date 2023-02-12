# Lab Report 3
I have chosen the `find` command to learn more about.

## Find with `-type` flag
We can use the -type flag to specify whether we want to look for file or directories. For searching for files only, use `-type f`, and for searching for directories, use `-type d`.

Example 1:
```
[cs15lwi23asd@ieng6-201]:skill-demo1-data:284$ find written_2/ -type f
written_2/non-fiction/OUP/Abernathy/ch1.txt 
written_2/non-fiction/OUP/Abernathy/ch14.txt
written_2/non-fiction/OUP/Abernathy/ch15.txt
written_2/non-fiction/OUP/Abernathy/ch2.txt 
written_2/non-fiction/OUP/Abernathy/ch3.txt 
written_2/non-fiction/OUP/Abernathy/ch6.txt 
written_2/non-fiction/OUP/Abernathy/ch7.txt 
written_2/non-fiction/OUP/Abernathy/ch8.txt 
written_2/non-fiction/OUP/Abernathy/ch9.txt
...
```
What is happening above is, we are running the find command on the written_2 directory, and specifying via `-type f` that we only want to see files, and not directories. This is useful if we want to look at or do something to all files in a directory.

Example 2:
```
[cs15lwi23asd@ieng6-201]:skill-demo1-data:285$ find written_2/ -type d
written_2/
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Abernathy
written_2/non-fiction/OUP/Berk
written_2/non-fiction/OUP/Castro
written_2/non-fiction/OUP/Fletcher
written_2/non-fiction/OUP/Kauffman
written_2/non-fiction/OUP/Rybczynski
written_2/travel_guides
written_2/travel_guides/berlitz1
written_2/travel_guides/berlitz2
```
In the above example, we are running the find command on the written_2 directory, and specifying via `-type d` that we only want to see directories, and not files. This is useful if we want to look at or do something to all directories in a directory.
