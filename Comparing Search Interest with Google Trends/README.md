## Comparing Search Interest with Google Trends.
    Manipulate and plot time series data from Google Trends to analyze changes in search interest over time.
    
 
## Project Description

Time series data is everywhere; from temperature records, to unemployment rates, to the S&P 500 Index. 
Another rich source of time series data is Google Trends, where you can freely download the search interest of terms and topics from as far back as 2004.
This project dives into manipulating and visualizing Google Trends data to find unique insights.

In this project’s guided variant, you will explore the search data underneath the Kardashian family's fame and make custom plots to find how the most famous Kardashian/Jenner sister has changed over time.
In the unguided variant, you will analyze the worldwide search interest of five major internet browsers to calculate metrics such as rolling average and percentage change.

## Project Tasks

#### 1. The sisters and Google Trends

I'm not a fan nor a hater of the Kardashians and Jenners, the polarizing family intrigues me. Why? Their marketing prowess.
Say what you will about them and what they stand for, they are great at the hype game. Everything they touch turns to content.

The sisters in particular over the past decade have been especially productive in this regard. Let's get some facts straight.
I consider the "sisters" to be the following daughters of Kris Jenner. Three from her first marriage to lawyer Robert Kardashian:

(Kourtney Kardashian)[https://en.wikipedia.org/wiki/Kourtney_Kardashian] (daughter of Robert Kardashian, born in 1979)
(Kim Kardashian)[https://en.wikipedia.org/wiki/Kim_Kardashian] (daughter of Robert Kardashian, born in 1980)
(Khloé Kardashian)[https://en.wikipedia.org/wiki/Khlo%C3%A9_Kardashian] (daughter of Robert Kardashian, born in 1984) And two from her second marriage to Olympic gold medal-winning decathlete, Caitlyn Jenner (formerly Bruce):

(Kendall Jenner)[https://en.wikipedia.org/wiki/Caitlyn_Jenner] (daughter of Caitlyn Jenner, born in 1995)
(Kylie Jenner)[https://en.wikipedia.org/wiki/Kendall_Jenner] (daughter of Caitlyn Jenner, born in 1997)
(Kardashian)[https://en.wikipedia.org/wiki/Kylie_Jenner] Jenner sisters family tree

![kardashian_jenner_family_tree](https://user-images.githubusercontent.com/84151016/156175058-e87e0752-be0a-4f38-a839-c4dcffa53089.png)

This family tree can be confusing, but we aren't here to explain it. We're here to explore the data underneath the hype, and we'll do it using search interest data from Google Trends.
We'll recreate the Google Trends plot to visualize their ups and downs over time, then make a few custom plots of our own. And we'll answer the big question: ***Is Kim even the most famous sister anymore?***

First, let's load and inspect our Google Trends data, which was downloaded in CSV form. (The query parameters)[https://trends.google.com/trends/explore?date=2007-01-01%202019-03-21&q=%2Fm%2F0261x8t,%2Fm%2F043p2f2,%2Fm%2F043ttm7,%2Fm%2F05_5_yx,%2Fm%2F05_5_yh]: each of the sisters, worldwide search data, 2007 to present day. (2007 was the year Kim became "active" according to Wikipedia.)

#### 2. Better "kolumn" names

So we have a column for each month since January 2007 and a column for the worldwide search interest for each of the sisters each month. By the way, Google defines the values of search interest as:

Numbers represent search interest relative to the highest point on the chart for the given region and time. A value of 100 is the peak popularity for the term. A value of 50 means that the term is half as popular. A score of 0 means there was not enough data for this term.

Okay, that's great Google, but you are not making this data easily analyzable for us. I see a few things. Let's do the column names first. A column named "Kim Kardashian: (Worldwide)" is not the most usable for coding purposes. Let's shorten those so we can access their values better.
Might as well standardize all column formats, too. I like lowercase, short column names.

![table1](https://user-images.githubusercontent.com/84151016/156177379-10587af2-0e24-44f7-9627-c4b8eba8dcdd.jpeg)


#### 3. Pesky data types

That's better. We don't need to scroll our eyes across the table to read the values anymore since it is much less wide. And seeing five columns that all start with the letter "k" … the aesthetics … we should call them "kolumns" now! (Bad joke.)

The next thing I see that is going to be an issue is that "<" sign. If "a score of 0 means there was not enough data for this term," "<1" must mean it is between 0 and 1 and Google does not want to give us the fraction from google.trends.com for whatever reason. 
That's fine, but this "<" sign means we won't be able to analyze or visualize our data right away because those column values aren't going to be represented as numbers in our data structure.
Let's confirm that by inspecting our data types.

![info 2](https://user-images.githubusercontent.com/84151016/156177461-0b396467-f778-4e47-a261-e20cf415a875.jpeg)

#### 4. From object to integer

Yes, okay, the khloe, kourtney, and kendall columns aren't integers like the kim and kylie columns are. 
Again, because of the "<" sign that indicates a search interest value between zero and one. Is this an early hint at the hierarchy of sister popularity? We'll see shortly. 
Before that, we'll need to remove that pesky "<" sign. Then we can change the type of those columns to integer.

#### 5. From object to datetime

Okay, great, no more "<" signs. All the sister columns are of integer type.
Now let's convert our month column from type object to datetime to make our date data more accessible.

#### 6. Set month as index

And finally, let's set the month column as our index to wrap our data cleaning. 
Having month as index rather than the zero-based row numbers will allow us to write shorter lines of code to create plots, where month will represent our x-axis.

#### 7. The early Kim hype

Okay! So our data is ready to plot. Because we cleaned our data, we only need one line of code (and just thirteen characters!) 
to remake the Google Trends chart, plus another line to make the plot show up in our notebook.

![7](https://user-images.githubusercontent.com/84151016/156177307-201b4eed-e574-48d1-939f-673ec5f6fa7f.png)

#### 8. Kylie's rise

Oh my! There is so much to make sense of here. (Kim's sharp rise in 2007)[https://en.wikipedia.org/wiki/Kim_Kardashian#2007%E2%80%932009:_Breakthrough_with_reality_television], with the beginning of (Keeping Up with the Kardashians)[https://en.wikipedia.org/wiki/Keeping_Up_with_the_Kardashians], among other things.
There was no significant search interest for the other four sisters until mid-2009 when Kourtney and Khloé launched the reality television series, (Kourtney and Khloé Take Miami)[https://en.wikipedia.org/wiki/Kourtney_and_Kim_Take_Miami].
Then there was Kim's rise from famous to (literally more famous)[https://trends.google.com/trends/explore?date=all&geo=US&q=%2Fm%2F0261x8t,%2Fm%2F0d05l6] than God in 2011. (This Cosmopolitan article)[https://www.cosmopolitan.com/uk/entertainment/a12464842/who-is-kim-kardashian/] covers the timeline that includes the launch of music videos, fragrances, iPhone and Android games, another television series, joining Instagram, and more. Then there was Kim's ridiculous spike in December 2014: posing naked on the cover of Paper Magazine in a bid to break the internet will do that for you.

A curious thing starts to happen after that bid as well. Let's zoom in…

![8](https://user-images.githubusercontent.com/84151016/156177283-41ce3172-d677-4e38-804d-e964762401db.png)


#### 9. Smooth out the fluctuations with rolling means

It looks like my suspicion may be true: Kim is not always the most searched Kardashian or Jenner sister. Since late-2016, at various months, Kylie overtakes Kim. Two big spikes where she smashed Kim's search interest: in September 2017 when it was reported that Kylie was expecting her first child with rapper Travis Scott and in February 2018 when she gave birth to her daughter, Stormi Webster. The continued success of Kylie Cosmetics has kept her in the news, not to mention making her the "The Youngest Self-Made Billionaire Ever" according to Forbes.

These fluctuations are descriptive but do not really help us answer our question: is Kim even the most famous sister anymore? We can use rolling means to smooth out short-term fluctuations in time series data and highlight long-term trends. Let's make the window twelve months a.k.a. one year.

![9](https://user-images.githubusercontent.com/84151016/156177257-421cbc19-3512-4db5-be41-4500987e24e0.png)


#### 10. Who's more famous? The Kardashians or the Jenners?

Whoa, okay! So by this metric, Kim is still the most famous sister despite Kylie being close and nearly taking her crown. Honestly, the biggest takeaway from this whole exercise might be Kendall not showing up that much. It makes sense, though, despite her wildly successful modeling career. Some have called her "the only normal one in her family" as she tends to shy away from the more dramatic and controversial parts of the media limelight that generate oh so many clicks.

Let's end this analysis with one last plot. In it, we will plot (pun!) the Kardashian sisters against the Jenner sisters to see which family line is more popular now. We will use average search interest to make things fair, i.e., total search interest divided by the number of sisters in the family line.

The answer? Since 2015, it has been a toss-up. And in the future? With this family and their penchant for big events, who knows?

![10](https://user-images.githubusercontent.com/84151016/156177237-186200eb-92a0-4f11-ab10-21649c4a7c64.png)


