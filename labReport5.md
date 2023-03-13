# Lab Report 5

For lab report 3 (about find/grep etc) do the same exploration of several
options for a different command or commands

instead of the grep command, I will be researching the find command

All options were found on https://www.computerhope.com/unix/ufind.htm

## -type

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

By adding the type d option, I am searching for only directories, instead of
both directories and files. There is also a type f option, which would list
all files.

## -amin -[time]

```
ryanlin@Ryans-MacBook-Pro-1173 written_2 % find . -amin -5
ryanlin@Ryans-MacBook-Pro-1173 written_2 % vim travel_guides/berlitz1/HandRHongKong.txt
ryanlin@Ryans-MacBook-Pro-1173 written_2 % find . -amin -5                             
./travel_guides/berlitz1/HandRHongKong.txt
```

This option specifies the last modified at a specified time, in this case,
5 minutes ago. In the example, at first no files show up, but when I modify
a text file, it shows up.

## -size

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

This option can be used to find files above a certain size. In this case,
I searched for all files above 100 kb, and got 10 results

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