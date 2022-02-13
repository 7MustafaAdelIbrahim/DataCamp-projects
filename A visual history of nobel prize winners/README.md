## Project Description

The Nobel Prize is perhaps the world's most well known scientific award. Every year it is given to scientists and scholars in chemistry, literature, physics, medicine, economics, and peace. The first Nobel Prize was handed out in 1901, and at that time the prize was Eurocentric and male-focused, but nowadays it's not biased in any way. Surely, right?
Well, we're going to find out! The Nobel Foundation has made a dataset available of all prize winners from the start of the prize, in 1901, to 2016.
![Nobel_Prize](https://user-images.githubusercontent.com/84151016/152651517-8982763c-6c11-43fb-94a6-8efbda60b677.png)


Well, let's find out! What characteristics do the prize winners have? Which country gets it most often? And has anybody gotten it twice? It's up to you to figure this out. [The dataset used in this project is from The Nobel Foundation on Kaggle.](https://www.kaggle.com/nobelfoundation/nobel-laureates)

## Context

This dataset includes a record for every individual or organization that was awarded the Nobel Prize since 1901 till 2016. The Nobel Prizes and the Prize in Economic Sciences were awarded 579 times to 911 people and organizations. The Nobel Prize is an international award administered by the Nobel Foundation in Stockholm, Sweden, and based on the fortune of Alfred Nobel, Swedish inventor and entrepreneur. In 1968, Sveriges Riksbank established The Sveriges Riksbank Prize in Economic Sciences in Memory of Alfred Nobel, founder of the Nobel Prize. Each Prize consists of a medal, a personal diploma, and a cash award.

A person or organization awarded the Nobel Prize is called Nobel Laureate. The word "laureate" refers to being signified by the laurel wreath. In ancient Greece, laurel wreaths were awarded to victors as a sign of honor.  The Nobel laureate dataset was acquired from the Nobel Prize API.

## Inspiration

Which country has won the most prizes in each category? What words are most frequently written in the prize motivation? Can you predict the age, gender, and nationality of next year's Nobel laureates? Is the share of female Nobel prize winners becoming more equal over time?
From which country origin most Nobel prize winners?
How does your country rank with respect to the number of Nobel prize winners in history?
What is the trend in age with respect to Nobel prize winners (per prize category)?
Which generations are generating most Nobel prize winners?


## Dealing with missingness.
We've 911 entries, One row per each Nobel lautreates.
We've alot of missingness in our dataset , Specialy in motivation, birth_date, birth_country, birth_city, sex, organization_name, organization_city, organization_country, death_date, death_city, death_country columns. WE found out more about missingness, reasons and batterns.
Here is  the percentage of misssingness in our dataset and visualize it.

![the percentage of missingness](https://user-images.githubusercontent.com/84151016/153751059-f13f9f1b-0a34-4ff8-8c3e-f14d6db17a88.jpeg)

The fully correlation between missingness in our dataset.

![coorelation](https://user-images.githubusercontent.com/84151016/153751088-54cdbfa4-6e9d-4e88-86ec-9324a8ebfafd.jpeg)

To interpret this graph, read it from a top-to-down perspective.Cluster leaves which are linked together at a distance of zero.
What looks clear from the dendrogram is that the missingness of our dataset are heighly correlated and can be mentioned as missing not at rondom:

The death date, death city and death country columns are highly correlated, as the Nobel laureates in these samples are still alive.
The organization name, organization city and organization country columns. stand alone and their contributions did not belong to an organization.
The birth_date, birth_city, birth_country and sex columns. It might be because Nobel laureates had Emigrated to anther country.
So, It makes sense for all these values and data to be missed.
The missingness in motivations can be considered as Missing Completely at Random.

More additional information about the correlation of missingness.

![correlation with numbers](https://user-images.githubusercontent.com/84151016/153751109-1a9f3c89-3d95-49e7-8341-c76bb0275b81.jpeg)

Nullity correlation ranges from -1 to 1, where -1 means if one variable appears the other definitely does not, 0 means if variables appearing or not appearing have no effect on one another, 1 means if one variable appears the other definitely also does. As we can see there's a strong relation between missingnes in Skin_fold and serum_Insulin.

We've found out that missingness're very related to each in all columns, which we can mention that as missing not at random, and our plan's to simply explore and analyze to extract some information. So, we're not going to deal with missingness.

## EDA

Prize column contains the prize given to Nobel laureate, and It's very related to the category, Which in it's turn makes it does not add value or certian information*. and we  investigated to prove our idea by using reguler expression to remove the year from the prize column.
As the Nobel laureate dataset was acquired from the Nobel Prize API. So, we can say that "category and year columns has been exteacted form prize column and now prize column dows not contain any useful information" , which makes sense.
So simple we're goining to drop the prize column for memory space reason. And we'll drope laureate_id column too, as it does not cotain useful information.

#### Who gets the Nobel Prize?
Just looking at the first couple of prize winners, or Nobel laureates as they are also called, we already see a celebrity: Wilhelm Conrad Röntgen, the guy who discovered X-rays. And actually, we see that all of the winners in 1901 were guys that came from Europe. But that was back in 1901, looking at all winners in the dataset, from 1901 to 2016, which sex and which country is the most commonly represented?

(For country, we will use the birth_country of the winner, as the organization_country is NaN for all shared Nobel Prizes.)


![bar- percentage](https://user-images.githubusercontent.com/84151016/153751267-61437d7f-fbc8-4c2e-b9bb-90f0ed45ec63.jpeg)


Focus on females.


![pipe of pipe](https://user-images.githubusercontent.com/84151016/153751279-c90a65f2-0f3c-4ff9-aa15-62a9caee5419.jpeg)


### What about birth country !

![world](https://user-images.githubusercontent.com/84151016/153751303-e0ceba3f-9bd7-4673-94af-10f33ea41154.jpeg)

### prize sharing.


![prize share](https://user-images.githubusercontent.com/84151016/153751328-95d24b7e-8b9e-43fb-bb2b-d236fbd6c3aa.jpeg)


