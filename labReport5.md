# Lab Report 5

For lab report 3 (about find/grep etc) do the same exploration of several
options for a different command or commands

instead of the grep command, I will be researching the find command

All options were found on https://www.computerhope.com/unix/ufind.htm

## -type

By adding the type d option, I am searching for only directories, instead of
both directories and files.

```
ryanlin@Ryans-MacBook-Pro-1173 written_2 % find . -type d
.
./non-fiction
./non-fiction/OUP
./non-fiction/OUP/Berk
./non-fiction/OUP/Abernathy
./non-fiction/OUP/Rybczynski
./non-fiction/OUP/Kauffman
./non-fiction/OUP/Fletcher
./non-fiction/OUP/Castro
./travel_guides
./travel_guides/berlitz1
./travel_guides/berlitz2
```
There is also a type f option, which would list all files.

```
ryanlin@Ryans-MacBook-Pro-1173 written_2 % find . -type f
./non-fiction/OUP/Berk/ch2.txt
./non-fiction/OUP/Berk/ch1.txt
./non-fiction/OUP/Berk/CH4.txt
./non-fiction/OUP/Berk/ch7.txt
./non-fiction/OUP/Abernathy/ch2.txt
./non-fiction/OUP/Abernathy/ch3.txt
./non-fiction/OUP/Abernathy/ch1.txt
...
```



## -amin -[time]

This option specifies the last modified at a specified time, in this case,
5 minutes ago. In the example, at first no files show up, but when I modify
a text file, it shows up.

```
ryanlin@Ryans-MacBook-Pro-1173 written_2 % find . -amin -5
```
At first, there are no files modified

```
ryanlin@Ryans-MacBook-Pro-1173 written_2 % vim travel_guides/berlitz1/HandRHongKong.txt
ryanlin@Ryans-MacBook-Pro-1173 written_2 % find . -amin -5                             
./travel_guides/berlitz1/HandRHongKong.txt
```
After modifying a file, it shows up

## -size

This option can be used to find files above a certain size. In this case,
I searched for all files above 100 kb, and got 10 results
```
ryanlin@Ryans-MacBook-Pro-1173 written_2 % find . -size +100k
./non-fiction/OUP/Berk/ch2.txt
./non-fiction/OUP/Berk/CH4.txt
./travel_guides/berlitz1/WhereToIndia.txt
./travel_guides/berlitz1/WhereToItaly.txt
./travel_guides/berlitz1/WhereToMalaysia.txt
./travel_guides/berlitz1/WhereToJapan.txt
./travel_guides/berlitz1/WhereToFrance.txt
./travel_guides/berlitz2/Portugal-WhereToGo.txt
./travel_guides/berlitz2/Canada-WhereToGo.txt
./travel_guides/berlitz2/China-WhereToGo.txt
```

I can also specify less than a file size. I found 2 files with less than a KB
of contents
```
ryanlin@Ryans-MacBook-Pro-1173 written_2 % find . -size -1k -type f
./travel_guides/berlitz1/HandRIstanbul.txt
./travel_guides/berlitz1/HandRIbiza.txt
```


## -maxdepth

```
ryanlin@Ryans-MacBook-Pro-1173 written_2 % find . -maxdepth 1 -type f | wc
       0       0       0
ryanlin@Ryans-MacBook-Pro-1173 written_2 % find . -maxdepth 2 -type f | wc
       0       0       0
ryanlin@Ryans-MacBook-Pro-1173 written_2 % find . -maxdepth 3 -type f | wc
     179     179    7926
ryanlin@Ryans-MacBook-Pro-1173 written_2 % find . -maxdepth 4 -type f | wc
     224     224    9476
```

This option can be used to find files up to a certain max depth.
In this example, I piped the result into wc to find the number of files in each
depth. As you can see, this number increases as the depth increases.

I also used the -type f option so I don't count directories

```
ryanlin@Ryans-MacBook-Pro-1173 written_2 % cd travel_guides               
ryanlin@Ryans-MacBook-Pro-1173 travel_guides % find . -maxdepth 2 -type f | wc
     179     179    5420
```

When I cd into the travel_guides directory, I can again search with a depth to 
see the files that pertain to this directory