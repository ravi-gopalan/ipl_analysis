# Analysis of data from the Indian Premier League (20/20 Cricket tournament)
## Data downloaded from cricsheet.org as YAML files
* 756 YAML files were processed - one for each IPL match
## YAML files were wrangled and processed into pandas csv
* 2 csv files were created
1. one that showed match summaries i.e. who played, who won, venue etc.
2. one with details - for each delivery, who was the bowler, batsman, how many runs were scored etc.
## Analysis of Batting Performances
### Batting performances were analyzed to identify
1. The top 10 run-makers were identified
2. Features such as Batting Strike Rates, Batting Economy Rates
3. [Who is the most valuable batsman in the IPL?](https://medium.com/@ravi_gopalan/is-ms-dhoni-the-most-valuable-batsman-in-the-ipl-the-richest-cricket-franchise-in-the-world-4772ab5ee75a)
3. Batsmen were analyzed along multiple parameters
4. Batting performances were then analyzed over other time periods such as the last 3 years and only 2019 to identify top batsmen
## Analysis of Bowling Performances
1. The top 10 wicket-takers were identified
2. Features such as Bowling Strike Rates, Bowling Economy Rates
3. Bowlers were analyzed along multiple parameters
4. [Is Malinga the best bowler in the IPL?](https://medium.com/@ravi_gopalan/is-slinga-malinga-the-best-ever-bowler-in-the-ipl-11f4fba63403) 
5. Bowling performances were then analyzed over other time periods such as the last 3 years and only 2019 to identify top batsmen
## Analysis of Fielding Performances
1. Similarly players with the most catches, stumpings and run-outs were then idenified
## Build a model to predict a winner in a match
### The base predictor would be 50% (either you win a match or lose a mach irrespective of how many runs you scored)
### The key variables that matter would be
1. How many runs were scored?
2. How many wickets were lost?
3. Could we break up an inning to see the performance by each quarter?
4. How many deliveries that couldn' be scored off could be another parameter 
### These were then identified
### To determine the best model the following steps were used
1. 7 different classifiers were tested:
* *Logistic Regression*
* *Support Vector Machines*
* *Decision Tree*
* *AdaBoost*
* *RandomForest*
* *Gradient Boost*
* *MultiLayerPerceptron*
2. These models were put through a Pipeline with the following steps:
* *Simple Imputer to impute values to NaN*
* *Standard Scaler to scale the values*
* *PCA to reduce the variables to principal components that explain over 99%*
* *Classifier was then grid searched to get the right model hyper parameters*
3. The net effect was that a 75% accuracy was obtained with minor differences between the classifiers
