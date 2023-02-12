# Lab Report 3
I have chosen the `find` command to learn more about.

## Find with `-type` flag
We can use the `-type` flag to specify whether we want to look for file or directories. For searching for files only, use `-type f`, and for searching for directories, use `-type d`.

Source: https://geekflare.com/linux-find-commands/

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
What is happening above is, we are running the `find` command on the written_2 directory, and specifying via `-type f` that we only want to see files, and not directories. This is useful if we want to look at or do something to all files in a directory.

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
In the above example, we are running the `find` command on the written_2 directory, and specifying via `-type d` that we only want to see directories, and not files. This is useful if we want to look at or do something to all directories in a directory.

## Find with `-iname` flag
The `-iname` flag works similarly to the `-name` flag, except, `-iname` is case insensitive. An easy way to remember this command would be to just think of the i in `-iname` as ignore case. This find command flag will find all paths that match the given string, but will ignore case.

Source: https://geekflare.com/linux-find-commands/

Example 1:
```
[cs15lwi23asd@ieng6-201]:skill-demo1-data:290$ find written_2/ -iname "*cH*"
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch14.txt        
written_2/non-fiction/OUP/Abernathy/ch15.txt        
written_2/non-fiction/OUP/Abernathy/ch2.txt
written_2/non-fiction/OUP/Abernathy/ch3.txt
written_2/non-fiction/OUP/Abernathy/ch6.txt
written_2/non-fiction/OUP/Abernathy/ch7.txt
written_2/non-fiction/OUP/Abernathy/ch8.txt
written_2/non-fiction/OUP/Abernathy/ch9.txt
written_2/non-fiction/OUP/Berk/CH4.txt
written_2/non-fiction/OUP/Berk/ch1.txt
written_2/non-fiction/OUP/Berk/ch2.txt
written_2/non-fiction/OUP/Berk/ch7.txt
written_2/non-fiction/OUP/Castro/chA.txt
written_2/non-fiction/OUP/Castro/chB.txt
```
As can be seen in the above example, `find` ignored case when looking for paths that match the given input `"*cH*"` and so it shows us every path that has the substring "ch" in it, regardless of case. This is super useful as sometimes we can't remember if something was capitalized or not, or maybe in that specific situation we don't really care about capitalization.

Example 2:
```
[cs15lwi23asd@ieng6-201]:skill-demo1-data:294$ find written_2/ -iname "*todo*"
written_2/travel_guides/berlitz2/Algarve-WhatToDo.txt      
written_2/travel_guides/berlitz2/Amsterdam-WhatToDo.txt    
written_2/travel_guides/berlitz2/Athens-WhatToDo.txt       
written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt      
written_2/travel_guides/berlitz2/Bali-WhatToDo.txt
written_2/travel_guides/berlitz2/Barcelona-WhatToDo.txt    
written_2/travel_guides/berlitz2/Beijing-WhatToDo.txt      
written_2/travel_guides/berlitz2/Berlin-WhatToDo.txt       
written_2/travel_guides/berlitz2/Bermuda-WhatToDo.txt      
written_2/travel_guides/berlitz2/Budapest-WhatToDo.txt     
written_2/travel_guides/berlitz2/California-WhatToDo.txt   
written_2/travel_guides/berlitz2/CanaryIslands-WhatToDo.txt
written_2/travel_guides/berlitz2/Cancun-WhatToDo.txt       
written_2/travel_guides/berlitz2/China-WhatToDo.txt        
written_2/travel_guides/berlitz2/Costa-WhatToDo.txt        
written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt  
written_2/travel_guides/berlitz2/Crete-WhatToDo.txt        
written_2/travel_guides/berlitz2/Cuba-WhatToDo.txt
written_2/travel_guides/berlitz2/Nepal-WhatToDo.txt        
written_2/travel_guides/berlitz2/Paris-WhatToDo.txt        
written_2/travel_guides/berlitz2/Poland-WhatToDo.txt       
written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt     
written_2/travel_guides/berlitz2/PuertoRico-WhatToDo.txt   
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt
```
In the above example, `find` is looking in written_2 for all paths that contain the string `"todo"` regardless of capitalization. In this case the `-iname` flag is useful because I wanted to find all of the things to do in these different places, and by searching for "todo" while ignoring case, I get back all of the possible things to do, regardless of the files are capitalized.
