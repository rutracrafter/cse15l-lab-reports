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

## Find with multiple directories
The `find` command can also be used on multiple directories at the same time! We just have to specify the multiple directory paths that we want `find` to look into, but there isn't any special flag needed! This is super useful as if we are looking for a file that we can't remember the location of, we can look in multiple directories to speed up the search process!

Source: https://geekflare.com/linux-find-commands/

Example 1:
```
[cs15lwi23asd@ieng6-201]:skill-demo1-data:295$ find written_2/non-fiction/OUP/Fletcher/ written_2/non-fiction/OUP/Kauffman/ -iname "*ch5*"
written_2/non-fiction/OUP/Fletcher/ch5.txt
written_2/non-fiction/OUP/Kauffman/ch5.txt
```
In the example above, we are using `find` to look for paths containing the substring "ch5" regardless of capitalization in the `written_2/non-fiction/OUP/Fletcher/` and `written_2/non-fiction/OUP/Kauffman/` directories! This is super useful in this case because instead of having to use find 2 times, we only had to use it once, imagine if we were looking for paths containing the substring "ch5" regardless of capitalization in 500 different directories! We would not want to write the find command over and over again 500 times, so instead we can specify many paths at once!

Example 2:
```
[cs15lwi23asd@ieng6-201]:skill-demo1-data:299$ find written_2/travel_guides/berlitz1 written_2/travel_guides/berlitz2 -type f -iname "*history*"
written_2/travel_guides/berlitz1/HistoryDublin.txt        
written_2/travel_guides/berlitz1/HistoryEdinburgh.txt     
written_2/travel_guides/berlitz1/HistoryEgypt.txt
written_2/travel_guides/berlitz1/HistoryFWI.txt
written_2/travel_guides/berlitz1/HistoryFrance.txt        
written_2/travel_guides/berlitz1/HistoryGreek.txt
written_2/travel_guides/berlitz1/HistoryHawaii.txt        
written_2/travel_guides/berlitz1/HistoryHongKong.txt      
written_2/travel_guides/berlitz1/HistoryIbiza.txt
written_2/travel_guides/berlitz1/HistoryIndia.txt
written_2/travel_guides/berlitz1/HistoryIsrael.txt        
written_2/travel_guides/berlitz1/HistoryIstanbul.txt      
written_2/travel_guides/berlitz1/HistoryItaly.txt
written_2/travel_guides/berlitz1/HistoryJamaica.txt       
written_2/travel_guides/berlitz1/HistoryJapan.txt
written_2/travel_guides/berlitz1/HistoryJerusalem.txt     
written_2/travel_guides/berlitz1/HistoryLakeDistrict.txt  
written_2/travel_guides/berlitz1/HistoryLasVegas.txt      
written_2/travel_guides/berlitz1/HistoryMadeira.txt       
written_2/travel_guides/berlitz1/HistoryMadrid.txt        
written_2/travel_guides/berlitz1/HistoryMalaysia.txt      
written_2/travel_guides/berlitz1/HistoryMallorca.txt      
written_2/travel_guides/berlitz2/Algarve-History.txt      
written_2/travel_guides/berlitz2/Amsterdam-History.txt    
written_2/travel_guides/berlitz2/Athens-History.txt       
written_2/travel_guides/berlitz2/Bahamas-History.txt      
written_2/travel_guides/berlitz2/Bali-History.txt
written_2/travel_guides/berlitz2/Barcelona-History.txt    
written_2/travel_guides/berlitz2/Beijing-History.txt      
written_2/travel_guides/berlitz2/Berlin-History.txt       
written_2/travel_guides/berlitz2/Bermuda-history.txt      
written_2/travel_guides/berlitz2/Budapest-History.txt     
written_2/travel_guides/berlitz2/California-History.txt   
written_2/travel_guides/berlitz2/Canada-History.txt       
written_2/travel_guides/berlitz2/CanaryIslands-History.txt
written_2/travel_guides/berlitz2/Cancun-History.txt       
written_2/travel_guides/berlitz2/China-History.txt        
written_2/travel_guides/berlitz2/Costa-History.txt        
written_2/travel_guides/berlitz2/CostaBlanca-History.txt  
written_2/travel_guides/berlitz2/Crete-History.txt        
written_2/travel_guides/berlitz2/Cuba-History.txt
written_2/travel_guides/berlitz2/Nepal-History.txt        
written_2/travel_guides/berlitz2/NewOrleans-History.txt   
written_2/travel_guides/berlitz2/Poland-History.txt       
written_2/travel_guides/berlitz2/Portugal-History.txt     
written_2/travel_guides/berlitz2/PuertoRico-History.txt   
written_2/travel_guides/berlitz2/Vallarta-History.txt
```
In this example, we are looking for all files containing the substring "history" regardless of case in the `written_2/travel_guides/berlitz1` and `written_2/travel_guides/berlitz2` directories. This is very similar to the last example, however, look at how useful of a feature this is on a larger scale. If we wanted to output this result into a file using `>` it would much simpler to use `find` with multiple directory paths, rather than having to run `find` on each individual directory path, and then concatenating each run of `find` to the desired file, imagine this time that we do this for 1000 different directories, we are saving so much time by using multiple paths! 

## Find with `-amin` flag
To find files and directories that have been accessed within a specfied amount of minutes, we can use the `-amin` flag. This can be super handy if we are looking for a file or directory that we accessed a few minutes ago, but can't remember the name of.

Source: https://geekflare.com/linux-find-commands/

Example 1:
```
[cs15lwi23asd@ieng6-201]:skill-demo1-data:302$ find written_2/ -amin -15
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
In the example above, we are looking for files and directories that have been accessed within the last 15 minutes. The negative sign in front of the `-15` indicates that we are looking for things that were either accessed 15 minutes ago, or sooner. If we had used a plus instead of a negative sign, we would have wound up with things that were either accessed 15 minutes ago or later. This is a super useful command as I can kind of see what I have been up to in the last 15 minutes. Imagine that I couldn't remember the directory named "Kauffman" maybe I only remembered that it's name started with a "K", but I also remember that I accessed it less than 15 minutes ago, the above command would have really helped me in finding the Kauffman directory!

Example 2:
```
[cs15lwi23asd@ieng6-201]:skill-demo1-data:316$ vim written_2/non-fiction/OUP/Kauffman/ch8.txt
[cs15lwi23asd@ieng6-201]:skill-demo1-data:317$ find written_2/ -amin -5 -type f
written_2/non-fiction/OUP/Kauffman/ch8.txt
```
In the above example, I used the command-line text editor named Vim to access the file with path `written_2/non-fiction/OUP/Kauffman/ch8.txt`, then I used the `find` command with the `-amin` flag and the `-type` flag to look for a file in written_2 that had been accessed in the last 5 minutes. This is similar to the example above, except this time I actually accessed a file rather than only having accessed directories as in the example above. This is super useful because lets say that I had accessed 5 files in the last 5 minutes, and I couldn't remember their names, using the `find` command with the `-amin` flag as in the example above, I could see which files I had accessed in the last five minutes.
