# Project - Movie Recommender System

## Contents
* [Background](#background)
* [Dataset](#dataset)
* [Results](#results)

## Background
Recommender System is a system that predict ratings or preferences user may give to this item. It is a method to recommend things to people based on their past behaviour. We often sort or present as "top-N" recommendations which means recommendating people a set of N items from a large collection of items. There are many metrics to evaluate the results of this techniques. In this project, we mainly use `surprise` module to build differnent recommender system which can use to predict moving rating and provide recommendations.

## Dataset
This data come from [Kaggle MovieLen](https://www.kaggle.com/snehal1409/movielens). 

It contains 671 user, 9125 movies and 100004 ratings and there are no missing values in `ratings.csv` and `movies.csv`. The range of rating is between 0.5 and 5 and most user give score 3 or 4.

|   |userId	|movieId |rating	|timestamp |
|:-:|:-----:|:------:|:------:|:--------:|
|0	|1	    |31	     |2.5     |1260759144|
|1	|1	    |1029	   |3.0     |1260759179|
|2	|1	    |1061	   |3.0     |1260759182|

<em>Table 1: `ratings.csv` file.</em>

|   |movieId|title                    |genres                                         |
|:-:|:-----:|:-----------------------:|:---------------------------------------------:|
|0  |1      |Toy Story (1995)         |Adventure, Animation, Children, Comedy, Fantasy|
|1  |2      |Jumanji (1995)           |Adventure, Children, Fantasy                   |
|2  |3      |Grumpier Old Men (1995)  |Comedy, Romance                                |

<em>Table 2: `movies.csv` file.</em>

## Results
We build some models toward this data set and the result shows as following.

|Algorithm  |RMSE      |MAE       |HitRate   |cHitRate  |ARHR      |
|  :----:   |  :----:  |  :----:  |  :----:  |  :----:  |  :----:  |
|SVD        |0.9034    |0.6978    |0.0298    |0.0340    |0.0112    |
|SVD tuned  |0.9005    |0.6961    |0.0387    |0.0438    |0.0156    |
|User KNN   |0.9961    |0.7711    |0.0000    |0.0000    |0.0000    |
|Item KNN   |0.9995    |0.7798    |0.0000    |0.0000    |0.0000    |
|RBM        |1.1794    |0.9842    |0.0000    |0.0000    |0.0000    |
|AutoEncoder|2.0317    |1.6709    |0.0060    |0.0102    |0.0025    |

Auto Encodeer has the largest RMSE and MAE. SVD tuned has the highest HitRate, cHitRate and ARHR. If we consider hyperparameter or different topologies, the result may be different.

For the userID 85, different algorithms provide different recommendations.


|Algorithm  |Recommendations   |Algorithm  |Recommendations   |
|  :----:   |:----             |  :----:   |:----             |
|SVD        |All About Eve (1950) <br> Lord of the Rings: The Fellowship of the Ring (2001) <br> Lord of the Rings: The Two Towers (2002) <br> Lawrence of Arabia (1962) <br> Princess Bride(1987) <br> Casablanca (1942) <br> Crimes and Misdemeanors (1989) <br> American History X (1998) <br> Roman Holiday (1953) <br> Spirited Away (Sen to Chihiro no kamikakushi) (2001)|SVD tuned  |Lawrence of Arabia (1962) <br> Duck Soup (1933) <br> Happiness (1998) <br> Chinatown (1974) <br> All About Eve (1950) <br> Singin' in the Rain (1952) <br> African Queen, The (1951) <br> Wallace & Gromit: A Close Shave (1995) <br> Cool Hand Luke (1967) <br> Raging Bull (1980) |
|User KNN   |One Magic Christmas (1985) <br> Return from Witch Mountain (1978) <br> Taste of Cherry (Ta'm e guilass) (1997) <br> King Is Alive (2000) <br> MaelstrÃ¶m (2000)<br> Last Seduction (1994)<br> Faust (1926) <br> Seconds (1966) <br> Wages of Fear (1953) <br> Sergeant York (1941) |Item KNN   | Hearts and Minds (1996) <br> Black Narcissus (1947) <br> Punchline (1988) <br> Best Little Whorehouse in Texas (1982) <br> Under Suspicion (2000) <br> Asterix and the Gauls (AstÃ©rix le Gaulois) (1967) <br> Find Me Guilty (2006) <br> Asterix and the Vikings (AstÃ©rix et les Vikings) (2006) <br> From the Sky Down (2011) <br> Jason Bourne (2016) |
|RBM        |White Stripes Under Great White Northern Lights (2009) <br> Rocketship X-M (1950) <br> Love & Sex (2000) <br> Deterrence (1999) <br> Criminal Lovers (1999) <br> Amazon Women on the Moon (1987) <br> Innocence (2000) <br> Medium Cool (1969) <br> Year One (2009) <br> Steam of Life (Miesten vuoro) (2010) |AutoEncoder | Sleepless in Seattle (1993) <br> Bambi (1942) <br> Mystery Men (1999) <br> Toy Story (1995) <br> Field of Dreams (1989) <br> Finding Forrester (2000) <br> Top Gun (1986) <br> Unbreakable (2000) <br> Bridget Jones's Diary (2001) <br> Reign of Fire (2002)|
