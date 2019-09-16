# Analysis of data from the Indian Premier League (20/20 Cricket tournament)
## The objective was to look at data from the Indian Premier League, analyze the data and come up with the following:
1. Top Batsmen and their performance metrics
2. Top Bowlers and their performance metrics
3. Build a model to predict the winner of an IPL match

## Understanding IPL T20 and Cricket performances
IPL is a treasure trove of cricket data and hence analyzing IPL results could well prove to be interesting. Its played in the exciting 20–20 format. The 12th edition of IPL completed on May 12 with the Mumbai Indians winning an easy win.

## Understanding Data
IPL Data in Kaggle was available only till 2017. I then looked at Cricsheet and got a zip file for all 12 years. Data however was in the YAML format.
Google Colab was used for GPU and Kaggle API was used to download data from within Colab. 
There are 3 files in the Github repo
1. `README.md` (this file)
2. `ipl_yaml_data_processing.ipynb` - a file that is used to convert the raw YAML data files into 2 `csv` files providing summary and detailed information
3. `ipl_analysis.ipynb` - this file processes he 2 csv files provided into meaningful data, analysis, insights and a predictive model


### Data was downloaded from cricsheet.org as YAML files
* 756 YAML files were processed - one for each IPL match

### Libraries required
* YAML file processing - `ruamel.yaml`
* Data Processing - `pandas`, `numpy`, `datetime`, `joblib`, `timeit` 
* Data Visualization - `matplotlib.pyplot`, `matplotlib.gridspec`, `seaborn` 
* Folder Operations - `pathlib`
* Modeling - `sklearn` (`model_selection`, `linear_model`, `tree`, `ensemble`, `neural_network`, `pipeline`, `preprocessing`, `impute`, `metrics`, `decomposition`)

### YAML files were wrangled and processed into pandas csv by the `ipl_yaml_data_processing.ipynb`
* 2 csv files were created
1. one that showed match summaries i.e. who played, who won, venue etc.
2. one with details - for each delivery, who was the bowler, batsman, how many runs were scored etc.

## Preparation of Data
Various features were created to enrich the raw data such as 
1. mapping names of various categories, 
2. Batting performance metrics such as batting averages, strike rates, top performances - 200s, 100s, 50s etc., boundary_rate, farm_rate, dot_rate, comparison across multiple time periods (i.e. all 12 seasons, the last 3 seasons or just the last 1 year)
3. Bowling performance metrics such as bowling averages, strike rates, top performances - # wickets in a match, comparisons across time periods etc.
4. Each Innings was divided into 4 quarters to see how momentum plays a part in victories

### Analysis of Batting Performances
#### Batting performances were analyzed to identify
1. The top 10 run-makers were identified
2. Features such as Batting Strike Rates, Batting Economy Rates
3. [Who is the most valuable batsman in the IPL?](https://medium.com/@ravi_gopalan/is-ms-dhoni-the-most-valuable-batsman-in-the-ipl-the-richest-cricket-franchise-in-the-world-4772ab5ee75a)
3. Batsmen were analyzed along multiple parameters
4. Batting performances were then analyzed over other time periods such as the last 3 years and only 2019 to identify top batsmen
### Analysis of Bowling Performances
#### Bowling performances were analyzed to identify
1. The top 10 wicket-takers were identified
2. Features such as Bowling Strike Rates, Bowling Economy Rates
3. Bowlers were analyzed along multiple parameters
4. [Is Malinga the best bowler in the IPL?](https://medium.com/@ravi_gopalan/is-slinga-malinga-the-best-ever-bowler-in-the-ipl-11f4fba63403) 
5. Bowling performances were then analyzed over other time periods such as the last 3 years and only 2019 to identify top batsmen
### Analysis of Fielding Performances
1. Similarly players with the most catches, stumpings and run-outs were then idenified

## A model was then built to predict a winner in a match
### The base predictor would be 50% (either you win a match or lose a mach irrespective of how many runs you scored)
### The key variables that matter would be
1. How many runs were scored?
2. How many wickets were lost?
3. Could we break up an inning to see the performance by each quarter?
4. How many deliveries that couldn' be scored off could be another parameter 
### These were then identified
There were no categorical variables that were defined as part of the model. Any missing values were imputed through SimpleImputer.

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
3. The models were then saved as pickle files
## Results
A 75% test accuracy was obtained with very minor differences between the classifiers.
Compared to the base predictor of 50%, a 75% accurate model is a big improvement.
