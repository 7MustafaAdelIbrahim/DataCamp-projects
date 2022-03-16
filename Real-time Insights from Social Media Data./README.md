
## Real-time Insights from Social Media Data

    Learn to analyze Twitter data and do a deep dive into a hot trend.

### Project Description

Fear of missing out, curiosity, self-esteem, speed: it's like social media has changed our basic human needs; these baits are keeping us hooked and engaged.
And Twitter is a master at this game. Elon Musk's tweets keep Wall Street on its toes; 
Trump's tweets have the potential of starting wars — Twitter has this huge influence on the world because of the type of its users.
Data from Twitter-storms is available in near real-time. This means we can learn about the big waves of thoughts and moods around the world as they arise. 
So of course, we are not going to miss the chance to analyze this treasure trove.
In this Project, you will use pre-downloaded datasets to understand the nuts and bolts of Twitter Data. In particular, you will do a thorough analysis of a hot-trend.

      Warning: Some of the tweets in the Twitter datasets contain explicit language.

### Project Tasks

#### 1. Local and global thought patterns

While we might not be Twitter fans, we have to admit that it has a huge influence on the world (who doesn't know about Trump's tweets).
Twitter data is not only gold in terms of insights, but Twitter-storms are available for analysis in near real-time. This means we can learn about the big waves of thoughts and moods around the world as they arise.

As any place filled with riches, Twitter has security guards blocking us from laying our hands on the data right away ⛔️ Some authentication steps (really straightforward) are needed to call their APIs for data collection. Since our goal today is learning to extract insights from data, we have already gotten a green-pass from security ✅ Our data is ready for usage in the datasets folder — we can concentrate on the fun part! 🕵️‍♀️🌎

![tweets_influence](https://user-images.githubusercontent.com/84151016/158491387-01b85d0b-1dfe-4d69-a42b-efe7f6129031.png)

Twitter provides both global and local trends. Let's load and inspect data for topics that were hot worldwide (WW) and in the United States (US) at the moment of query — snapshot of JSON response from the call to Twitter's GET trends/place API.

Note: [Here](https://developer.twitter.com/en/docs/twitter-api/v1/trends/trends-for-location/api-reference/get-trends-place) is the documentation for this call, and [here](https://developer.twitter.com/en/docs/api-reference-index) a full overview on Twitter's APIs.

#### 2. Prettifying the output

Our data was hard to read! Luckily, we can resort to the json.dumps() method to have it formatted as a pretty JSON string.
json.dumps() formats data as a JSON string. If you pass 'indent' to the method (a positive integer), then all the elements in the JSON array are printed with that indent level. This makes it easy to read the results — pretty-printed.

#### 3. Finding common trends

🕵️‍♀️ From the pretty-printed results (output of the previous task), we can observe that:

We have an array of trend objects having: the name of the trending topic, the query parameter that can be used to search for the topic on Twitter-Search, the search URL and the volume of tweets for the last 24 hours, if available. (The trends get updated every 5 mins.)

At query time #BeratKandili, #GoodFriday and #WeLoveTheEarth were trending WW.

"tweet_volume" tell us that #WeLoveTheEarth was the most popular among the three.

Results are not sorted by "tweet_volume".

There are some trends which are unique to the US.

It’s easy to skim through the two sets of trends and spot common trends, but let's not do "manual" work. We can use Python’s set data structure to find common trends — we can iterate through the two trends objects, cast the lists of names to sets, and call the intersection method to get the common names between the two sets.

#### 4. Exploring the hot trend

🕵️‍♀️ From the intersection (last output) we can see that, out of the two sets of trends (each of size 50), we have 11 overlapping topics. In particular, there is one common trend that sounds very interesting: #WeLoveTheEarth — so good to see that Twitteratis are unanimously talking about loving Mother Earth! 💚

Note: We could have had no overlap or a much higher overlap; when we did the query for getting the trends, people in the US could have been on fire obout topics only relevant to them.

![earth](https://user-images.githubusercontent.com/84151016/158491707-e3a00af7-1af4-4bb5-b908-90cbc9b21d63.jpg)

Image Source:Official Music Video Cover: https://welovetheearth.org/video/

We have found a hot-trend, #WeLoveTheEarth. Now let's see what story it is screaming to tell us!
If we query Twitter's search API with this hashtag as query parameter, we get back actual tweets related to it. We have the response from the search API stored in the datasets folder as 'WeLoveTheEarth.json'. So let's load this dataset and do a deep dive in this trend.

#### 5. Digging deeper

🕵️‍♀️ Printing the first two tweet items makes us realize that there’s a lot more to a tweet than what we normally think of as a tweet — there is a lot more than just a short text!

But hey, let's not get overwhemled by all the information in a tweet object! Let's focus on a few interesting fields and see if we can find any hidden insights there.


#### 6. Frequency analysis

🕵️‍♀️ Just from the first few results of the last extraction, we can deduce that:

We are talking about a song about loving the Earth.
A lot of big artists are the forces behind this Twitter wave, especially Lil Dicky.
Ed Sheeran was some cute koala in the song — "EdSheeranTheKoala" hashtag! 🐨
Observing the first 10 items of the interesting fields gave us a sense of the data. We can now take a closer look by doing a simple, but very useful, exercise — computing frequency distributions. Starting simple with frequencies is generally a good approach; it helps in getting ideas about how to proceed further.

Helpful links:

Counter [documentation](https://docs.python.org/2/library/collections.html)

#### 7. Activity around the trend

🕵️‍♀️ Based on the last frequency distributions we can further build-up on our deductions:

We can more safely say that this was a music video about Earth (hashtag 'EarthMusicVideo') by Lil Dicky.
DiCaprio is not a music artist, but he was involved as well (Leo is an environmentalist so not a surprise to see his name pop up here).
We can also say that the video was released on a Friday; very likely on April 19th.
We have been able to extract so many insights. Quite powerful, isn't it?!

Let's further analyze the data to find patterns in the activity around the tweets — did all retweets occur around a particular tweet?

If a tweet has been retweeted, the 'retweeted_status' field gives many interesting details about the original tweet itself and its author.

We can measure a tweet's popularity by analyzing the retweetcount and favoritecount fields. But let's also extract the number of followers of the tweeter — we have a lot of celebs in the picture, so can we tell if their advocating for #WeLoveTheEarth influenced a significant proportion of their followers?

Note: The retweet_count gives us the total number of times the original tweet was retweeted. It should be the same in both the original tweet and all the next retweets. Tinkering around with some sample tweets and the official documentaiton are the way to get your head around the mnay fields.

#### 8. A table that speaks a 1000 words

Let's manipulate the data further and visualize it in a better and richer way — "looks matter!"

#### 9. Analyzing used languages

🕵️‍♀️ Our table tells us that:

Lil Dicky's followers reacted the most — 42.4% of his followers liked his first tweet.
Even if celebrities like Katy Perry and Ellen have a huuge Twitter following, their followers hardly reacted, e.g., only 0.0098% of Katy's followers liked her tweet.
While Leo got the most likes and retweets in terms of counts, his first tweet was only liked by 2.19% of his followers.
The large differences in reactions could be explained by the fact that this was Lil Dicky's music video. Leo still got more traction than Katy or Ellen because he played some major role in this initiative.

Can we find some more interesting patterns in the data? From the text of the tweets, we could spot different languages, so let's create a frequency distribution for the languages.

#### 10. Final thoughts

🕵️‍♀️ The last histogram tells us that:

Most of the tweets were in English.
Polish, Italian and Spanish were the next runner-ups.
There were a lot of tweets with a language alien to Twitter (lang = 'und').
Why is this sort of information useful? Because it can allow us to get an understanding of the "category" of people interested in this topic (clustering). We could also analyze the device type used by the Twitteratis, tweet['source'], to answer questions like, "Does owning an Apple compared to Andorid influences people's propensity towards this trend?". I will leave that as a further exercise for you!



What an exciting journey it has been! We started almost clueless, and here we are.. rich in insights.

From location based comparisons to analyzing the activity around a tweet to finding patterns from languages and devices, we have covered a lot today — let's give ourselves a well-deserved pat on the back! ✋

![languages_world_map](https://user-images.githubusercontent.com/84151016/158492090-39f8ba99-af28-40a6-8f9f-856acd4ff78b.png)


Magic Formula = Data + Python + Creativity + Curiosity

![finish_line](https://user-images.githubusercontent.com/84151016/158492096-dd2e81cd-1967-4f33-9022-87a82bd766bc.jpg)

#### Helpful links:

[Twitter API Reference Index](https://developer.twitter.com/en/docs/api-reference-index)

[Twitter Developers Docs](https://developer.twitter.com/en/docs)

