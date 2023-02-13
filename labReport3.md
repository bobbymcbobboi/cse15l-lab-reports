# Lab Report 3

I will research the grep command.

## -r option

I found this option in the manpage for grep

```
grep -r china
./non-fiction/OUP/Abernathy/ch2.txt:Until the emergence of mass retail, the wholesaler-jobber dominated the distribution of consumer dry goods to general stores: clothing, upholstered furnishings, hardware, drugs, tobacco, furniture, china, and glassware. Unlike traveling peddlers of the past, who carried everything with them, these salesmen could ride the rails into town with no more than a trunk of samples and catalogs. The new infrastructure created by the railroads and telegraph contributed to the growth of wholesale houses. Retailers no longer needed to carry such large inventories, the risk of losing shipments was reduced, and delivery was more certain on a specified schedule. Increased volume cut unit costs and enhanced cash flow, reducing credit needs. Moreover, these salesmen provided a flow of information to their headquarters on changing demand in -various localities as well as the credit ratings of local storekeepers and merchants.
./travel_guides/berlitz1/HistoryJapan.txt:        French Indochina after the defeat of France. The US responded to the
...(cont)
```

The -r option for grep makes it search recursively through all its subdirectories for
the desired search term. It is useful to search through an entire directory in one
command, instead of individually searching through the files.

```
grep -r macroeconomic non-fiction/OUP/Abernathy
non-fiction/OUP/Abernathy/ch1.txt:A Stitch in Time concludes with a look at the many factors shaping today’s retail-apparel-textile channel—from the complex management challenges facing suppliers to labor standards and macroeconomic policy. Chapter 13 (“The Global Marketplace”) reviews trends in U.S. imports and exports of apparel and textiles, including information on trade by countries and specific products. It then connects these trends to changing trade policies, emphasizing the growing regionalization of trade flows in different parts of the world. Chapter 14 (“Suppliers in a Lean World”) examines our survey results from another angle, evaluating firm performance in an integrated channel. Here we highlight the importance of combining information technologies, manufacturing innovations, and new methods of management to respond to lean retailing demands.
non-fiction/OUP/Abernathy/ch1.txt:Finally, Chapter 15 (“Information-Integrated Channels”) touches on a number of public policy issues raised by our findings. These include what can be done about the continuing problem of sweatshops, the new international economics of trade, and the effect of information integration on the business cycle and consumer prices at the macroeconomic level. Last but not least, we take a realistic look at the competitive future of the U.S. retail, apparel, and textile industries.
non-fiction/OUP/Abernathy/ch15.txt:In this final chapter, we step back to survey the ways in which information-integrated channels will affect the public and private sectors. The pervasive changes arising from lean retailing challenge the conventional wisdom about the future of international trade, labor standards, employment, and even macroeconomic fluctuations. At the same time, these changes alter the nature of competitive strategy for businesses that supply lean retailers in apparel, textile, and other industries.
non-fiction/OUP/Abernathy/ch15.txt:The impact of these new policies on retailing and manufacturing sectors may have begun to show up in economy-wide measures of inventory. The overall ratio of inventories to final sales of domestic business fell considerably in the past decade, from 2.78 in 1987 to 2.34 in 1997.12 It has long been known that inventories at the macroeconomic level affect the depth and length of business cycles.13 The connection between recent changes in inventory policy and the business cycle have only begun to be studied in a systematic fashion.14 As noted in the 1988 Economic Report of the President,
non-fiction/OUP/Abernathy/ch15.txt:Our work on apparel supplier adjustments to lean retailing suggests that an economy characterized by an increasing level of modern manufacturing and retailing practices should experience lower levels of inventories relative to sales. Because a reduction in the I/S ratio means that changes in sales will be matched by a smaller change in inventories, a lower ratio also implies lower inventory volatility. This is important because aggregate inventory volatility has historically made up a significant portion of the volatility of Gross Domestic Product (GDP). If the effects documented for retail-apparel-textile channels are more pervasive across other sectors similarly affected by channel integration, these changes could imply lower GDP volatility. This macroeconomic link may prove to be the most profound implication of the adoption of firm-level information technology and manufacturing practices.
non-fiction/OUP/Abernathy/ch15.txt:Fundamental changes in inventory policies in retail and manufacturing may significantly affect price levels as well. The increased volatility of producer and consumer prices in a number of sectors since 1995 has been attributed in part to the adoption of new inventory polices related to lean retailing.16 Some have suggested a connection between these policies and price fluctuations.17 According to one view, an information-integrated channel may lead to increased volatility in aggregate prices because the impact of shifts in supply and demand is more rapidly reflected in consumer prices without the buffering impact of inventory. Competitive information-integrated channels may also reduce aggregate price levels, as expressed by price markup policies that in the past have reflected the incomplete information of channel participants.18 Whatever the effect, the more widespread adoption of information-integrated channels documented in this book raise a central question for future models of industry- and macroeconomic-price movements.19
non-fiction/OUP/Abernathy/ch14.txt:The implications of these changes do not end here. An economy consisting of lean retailing and corresponding “lean” suppliers operates in a fundamentally different manner from one based on traditional retailing and supply practices. The industrial transformation currently in progress encompasses international trade issues, competitiveness, labor regulation, and macroeconomic policies. Accordingly, the last chapter of this book is devoted to our reflections on the impact of channel integration on certain public policy issues.
```

In this example, I am searching for the term "macroeconomic" in the Abernathy directory.
Without the -r option, I might have to search through all the files in the directory.

## -c option

I found this option in the manpage for grep.

```
grep -rc macroeconomic non-fiction/OUP/Abernathy
non-fiction/OUP/Abernathy/ch2.txt:0
non-fiction/OUP/Abernathy/ch3.txt:0
non-fiction/OUP/Abernathy/ch1.txt:2
non-fiction/OUP/Abernathy/ch7.txt:0
non-fiction/OUP/Abernathy/ch6.txt:0
non-fiction/OUP/Abernathy/ch8.txt:0
non-fiction/OUP/Abernathy/ch9.txt:0
non-fiction/OUP/Abernathy/ch15.txt:4
non-fiction/OUP/Abernathy/ch14.txt:1
```

With the -c option, it will display a count for the number of times a term exists in a file
instead of the excerpts from the file. This makes it a lot more readable, which is useful. I combined
it with the -r option to search the whole directory.

```
grep -rc the travel_guides/berlitz2/Algarve*
travel_guides/berlitz2/Algarve-History.txt:32
travel_guides/berlitz2/Algarve-Intro.txt:21
travel_guides/berlitz2/Algarve-WhatToDo.txt:43
travel_guides/berlitz2/Algarve-WhereToGo.txt:147
```

With the -c option, I was able to find which file has the most occurences of the word
"the". Without it, it would've been very hard to read.


## -i option

I found this option in the manpage for grep

```
ryanlin@Ryans-MacBook-Pro-1173 written_2 % grep -ic the ./travel_guides/berlitz2/China-History.txt
67
ryanlin@Ryans-MacBook-Pro-1173 written_2 % grep -c the ./travel_guides/berlitz2/China-History.txt
63
```

The -i option makes the grep command case insensitive. This is useful if you want to find
the number of times a word occurs regardless of case. In this case, the word "the" occurred
67 times, with 4 of them being uppercase.

```
ryanlin@Ryans-MacBook-Pro-1173 written_2 % grep -c west ./travel_guides/berlitz2/China-History.txt
2
ryanlin@Ryans-MacBook-Pro-1173 written_2 % grep -ic west ./travel_guides/berlitz2/China-History.txt
6
```

In this example, the word "west" only occurred twice in the China-History.txt file,
but it occured 6 times if you ignore case.

## -n option

I found this option on the grep man page.

```
grep -rn hello
./travel_guides/berlitz1/WhereToItaly.txt:2041:        (or Ca’ Grande), while gondoliers claim Othello’s Desdemona lived in
./travel_guides/berlitz1/WhereToHongKong.txt:484:        the local people smile “hello” and, if you’re lucky, point you to a
```

The -n option prints the line number before the place the search term was found.
This is useful to locate where in the file the search term was found.

```
grep -rn bye
./non-fiction/OUP/Castro/chN.txt:32:Good-bye my Lady
```

In this example, I am easily able to find out where in the chN.txt file the word
"bye" was found, so I know where I am looking in the file.

