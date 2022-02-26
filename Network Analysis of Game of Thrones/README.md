# A Network Analysis of Game of Thrones
  Analyze the network of characters in Game of Thrones and how it changes over the course of the books.
  
  
# Project Description
Jon Snow, Daenerys Targaryen, or Tyrion Lannister? 
Who is the most important character in Game of Thrones? 
Let's see what mathematics can tell us about this!
We'll look at the character co-occurrence network and its evolution over the five books in R.R. Martin's hugely popular book series A Song of Ice and Fire (perhaps better known as the TV show Game of Thrones).
You will look at how the importance of the characters changes over the books using different centrality measures.
This project uses a dataset parsed by Andrew J. Beveridge and Jie Shan which is available [here](https://github.com/mathbeveridge/asoiaf).
For more information on this dataset have a look at the Network of [Thrones blog](https://networkofthrones.wordpress.com/).

# Project Tasks

### 1. Winter is Coming. Let's load the dataset ASAP!

If you haven't heard of Game of Thrones, then you must be really good at hiding.
Game of Thrones is the hugely popular television series by HBO based on the (also) hugely popular book series A Song of Ice and Fire by George R.R. Martin. 
In this notebook, we will analyze the co-occurrence network of the characters in the Game of Thrones books.
Here, two characters are considered to co-occur if their names appear in the vicinity of 15 words from one another in the books.
This dataset constitutes a network and is given as a text file describing the edges between characters, with some attributes attached to each edge.
![got_network](https://user-images.githubusercontent.com/84151016/155856212-a50e9f35-6ce0-4d51-8850-a7bd2a33be20.jpg)

#### 2. Time for some Network of Thrones

The resulting DataFrame book1 has 5 columns: Source, Target, Type, weight, and book. Source and target are the two nodes that are linked by an edge. 
A network can have directed or undirected edges and in this network all the edges are undirected.
The weight attribute of every edge tells us the number of interactions that the characters have had over the book, and the book column tells us the book number.
Once we have the data loaded as a pandas DataFrame, it's time to create a network. 
We will use networkx, a network analysis library, and create a graph object for the first book.

#### 3. Populate the network with the DataFrame

Currently, the graph object G_book1 is empty. Let's now populate it with the edges from book1.
And while we're at it, let's load in the rest of the books too!

#### 4. The most important character in Game of Thrones

To calculate degree centrality every node is assigned a number between 0 and 1 by computing the degree (the number of neighbors) 
and normalizing it by the total possible number of neighbors it can have, i.e n - 1 where n is the number of nodes in the network.

Is it Jon Snow, Tyrion, Daenerys, or someone else? Let's see! Network science offers us many different metrics to measure the importance of a node in a network.
Note that there is no "correct" way of calculating the most important node in a network, every metric has a different meaning.
First, let's measure the importance of a node in a network by looking at the number of neighbors it has, that is, the number of nodes it is connected to. 
For example, an influential account on Twitter, where the follower-followee relationship forms the network, is an account which has a high number of followers.
This measure of importance is called degree centrality.
Using this measure, let's extract the top ten important characters from the first book (book[0]) and the fifth book (book[4]).

#### 5. The evolution of character importance

According to degree centrality, the most important character in the first book is Eddard Stark but he is not even in the top 10 of the fifth book. 
The importance of characters changes over the course of five books because, you know, stuff happens… ;)
Let's look at the evolution of degree centrality of a couple of characters like Eddard Stark, Jon Snow, and Tyrion, 
which showed up in the top 10 of degree centrality in the first book.
![download](https://user-images.githubusercontent.com/84151016/155856454-1a8e28ea-e9fb-47ba-abda-eb7361bc80d1.png)

#### 6. What's up with Stannis Baratheon?

The intuition behind betweenness centrality is to find nodes which hold the network together, that is, if you remove such a node you are breaking apart the network. 
In a more mathematical way, 
***Betweenness centrality*** is calculated by finding shortest paths between all pairs of nodes and finding the node through which most of the paths pass.
We can see that the importance of Eddard Stark dies off as the book series progresses. 
With Jon Snow, there is a drop in the fourth book but a sudden rise in the fifth book.

Now let's look at various other measures like betweenness centrality and PageRank to find important characters in our Game of Thrones character co-occurrence network and see if we can uncover some more interesting facts about this network. 
Let's plot the evolution of betweenness centrality of this network over the five books.
We will take the evolution of the top four characters of every book and plot it.
![2](https://user-images.githubusercontent.com/84151016/155856476-e70f0540-1369-4f19-bcae-7e79b477dbc7.png)


#### 7. What does Google PageRank tell us about GoT?

We see a peculiar rise in the importance of Stannis Baratheon over the books. In the fifth book, 
he is significantly more important than other characters in the network, even though he is the third most important character according to degree centrality.

PageRank was the initial way Google ranked web pages. It evaluates the inlinks and outlinks of webpages in the world wide web, which is, essentially, a directed network. 
Let's look at the importance of characters in the Game of Thrones network according to PageRank.


#### 8. Correlation between different measures

Stannis, Jon Snow, and Daenerys are the most important characters in the fifth book according to PageRank. 
Eddard Stark follows a similar curve but for degree centrality and betweenness centrality: 
He is important in the first book but dies into oblivion over the book series.
We have seen three different measures to calculate the importance of a node in a network, and all of them tells us something about the characters and their importance in the co-occurrence network.
We see some names pop up in all three measures so maybe there is a strong correlation between them?
Let's look at the correlation between PageRank, betweenness centrality and degree centrality for the fifth book using Pearson correlation.

#### 9. Conclusion

We see a high correlation between these three measures for our character co-occurrence network.

So we've been looking at different ways to find the important characters in the Game of Thrones co-occurrence network. 
According to degree centrality, Eddard Stark is the most important character initially in the books. 
But who is/are the most important character(s) in the fifth book according to these three measures?

Jon-Snow
Stannis-Baratheon
Jon-Snow

