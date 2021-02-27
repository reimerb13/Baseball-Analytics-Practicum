# Player Decline of Major League Baseball (MLB) Players by Position

# Project Summary

Determine the data that can be used to predict the relative length, measured in years, of the expected productivity for baseball players by position before an organization is required to execute a replacement plan for players by position.  This project assumes normal baseball operations and does not account for the impact that injuries, free agency or other factors that might influence player productivity.  Gaining insight into this dilemma will help MLB organizations draft and develop players according to the length and maximum output at the position.

# Data Collection

The data was collected from the Lahman library in R. The data used was the Fielding dataset.

# The Fielding Data

The Fielding data has 143,046 observations with 18 variables. The classification for the variables included factors, characters,
and integers. The variables for the Fielding data consist of the following:

playerID: Player ID code

yearID: Year

stint: Player's stint (number of appearances a player made with a team during the season)

teamID: The name of the team (this variable was classified as a factor)

lgID: A factor variable that classified the league a player played in (AA, AL, FL, NL, PL, and UA)

POS: Position of a player (1B, 2B, SS, 3B, C, P, and OF)

G: Number of games a player played

GS: Number of games a player started

InnOuts: Time a player played in the field expressed as outs

PO: Number of putouts a player made

A: Number of assists a player made

E: Number of errors a player made

DP: Number of double plays a player made

PB: Number of passed balls by the catcher

WP: Number of wild pitches by the catcher

SB: Number of stolen bases by an opposing player off of a catcher

CS: Number of opponents caught stealing by a catcher

ZR: Zone Rating

# Data Preparation

The Fielding dataset was merged with the first and last name of players in the People dataset from the Lahman library.
The Fielding2 dataset had 143,046 observations with 19 variables. The 19th variable was the name of the players. 

A subset of the Fielding2 dataset was created that looked at the lgID that focused on the AL league. This subset was called 
Fielding2_AL.

A second subset of the Fielding2 dataset was created that looked at the lgID that focused on the nL league. This subset was called 
Fielding2_NL.

The Fielding2_AL and Fielding2_NL datasets were merged together to create an entire new dataset. The dataset was renamed Fielding3.

The Fielding3 data was filtered by specific positions. A subset of the Fielding3 data was created by looking at the POS variable by corner fielding positions: 1B and 3B. The subset of data that focused on the 1B position was called Fielding3_1B. Another subset of the Fielding3 data was created by looking at the POS variable that focused on the 3B position. This subset was called Fielding3_3B. The Fielding3_1B and Fielding3_3B datasets were merged to create a new dataset that was named Fielding3_Corner.

A subset of the Fielding3 data was created by looking at the POS variable by middle fielding positions: 2B and SS. The subset of data that focused on the 2B position was called Fielding3_2B. Another subset of the Fielding3 data was created by looking at the POS variable that focused on the SS position. This subset was called Fielding3_SS. The Fielding3_2B and Fielding3_SS datasets were merged to create a new dataset that was named Fielding3_Middle.

A subset of the Fielding3 data was created by looking at the POS variable by outfield and catcher positions: OF and C. The subset of data that focused on the OF position was called Fielding3_OF. Another subset of the Fielding3 data was created by looking at the POS variable that focused on the C position. This subset was called Fielding3_C. The Fielding3_OF and Fielding3_C datasets were merged to create a new dataset that was named Fielding3_OFC and later renamed OFC.

# Exploratory Data Analysis

There was exploratory data analysis conducted on the following datasets: Fielding2, Fielding2_AL, Fielding2_NL, Fielding3, Fielding3_1B, Fielding3_3B, Fielding3_Corner, Fielding3_2B, Fielding3_SS, Fielding3_Middle, Fielding3_OF, Fielding3_C, and Fielding3_OFC. Summary statistics and histograms were created to determine if any missing values existed in the datasets and how many outliers existed in the histograms. All missing values were imputed with the mean value for each column in the data.

After viewing the histograms of Fielding3_Corner, Fielding3_Middle, and Fielding3_OFC, the outliers were removed from the dataset. 

Before outliers were removed, the Fielding3_Corner dataset contained 27,405 observations. The Fielding3_Corner data was renamed Corner. After outliers were removed, the Fielding3_Corner dataset contained 24,302 observations. This new dataset was named 'x' and then renamed Corner2.

Before outliers were removed, the Fielding3_Middle dataset contained 23,966 observations. After outliers were removed, the Fielding3_Corner dataset contained 24,302 observations. This new dataset was named 'y' and then renamed M.

Before outliers were removed, the Fielding3_OFC dataset contained 38,331 observations. After outliers were removed, the Fielding3_Corner dataset contained 35,527 observations. This new dataset was named 'z' and renamed OFC2.

# Machine Learning Models

Machine learning models were created for Corner, Corner2, Fielding3_Middle, M, OFC, and OFC2. The variables used to create the models were stint, POS, G, GS, InnOuts, PO, A, E, and DP. There were three types of models created looking at each data: linear, radial, and polynomial. The data was sampled into a 70:30 ratio for training and testing datasets. The Kappa value, accuracy rate, and error rate were calculated for each model based on each dataset.

Corner Machine Learning Model Results

|SVM Type|Correct 1B Predictions|Correct 3B Predictions|Kappa Value|Accuracy Rate|Error Rate|
|:-------|---------------------:|---------------------:|----------:|------------:|----------:|
|Linear|3,647|4,083|0.88|94.0%|6.0%|
|Radial|3,612|3,888|0.82|91.2%|8.8%|
|Polynomial|3,377|3,727|0.73|86.4%|13.6%|

The results from the Corner machine learning models showed that the results were in very good agreement with the linear and radial models. The results were in good agreement with the polynomial model.

Corner 2 Machine Learning Model Results

|SVM Type|Correct 1B Predictions|Correct 3B Predictions|Kappa Value|Accuracy Rate|Error Rate|
|:-------|---------------------:|---------------------:|----------:|------------:|----------:|
|Linear|3,442|3,429|0.89|94.2%|5.8%|
|Radial|3,579|3,113|0.84|91.8%|8.2%|
|Polynomial|3,299|2,682|0.64|82.0%|18.0%|

The results from the Corner2 machine learning models showed that the results were in very good agreement with the linear and radial models. The results were in good agreement with the polynomial model.




