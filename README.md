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

# Libraries Used in R

Here is the list of libraries used to complete the baseball project in R:
- Lahman
- dplyr
- ggplot2
- outliers
- class
- gmodels
- caret
- randomForest
- tseries
- forecast
- Metrics

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

Before outliers were removed, the Fielding3_Middle dataset contained 23,966 observations. The Fielding3_Middle data was renamed Middle. After outliers were removed, the Fielding3_Corner dataset contained 24,302 observations. This new dataset was named 'y' and then renamed M.

Before outliers were removed, the Fielding3_OFC dataset contained 38,331 observations. After outliers were removed, the Fielding3_Corner dataset contained 35,527 observations. This new dataset was named 'z' and renamed OFC2.

# Support Vector Machines

Machine learning models were created for Corner, Corner2, Middle, M, OFC, and OFC2. The variables used to create the models were stint, POS, G, GS, InnOuts, PO, A, E, and DP. There were three types of models created looking at each data: linear, radial, and polynomial. The data was sampled into a 70:30 ratio for training and testing datasets. The Kappa value, accuracy rate, and error rate were calculated for each model based on each dataset. This is the interpretation of the Kappa value:

<0: No agreement
0 —.20: Slight
.21 —.40: Fair
.41 —.60: Moderate
.61 —.80: Substantial
.81–1.0: Perfect

Corner SVM Model Results

|SVM Type|Correct 1B Predictions|Correct 3B Predictions|Kappa Value|Accuracy Rate|Error Rate|
|:-------|---------------------:|---------------------:|----------:|------------:|----------:|
|Linear|3,647|4,083|0.88|94.0%|6.0%|
|Radial|3,612|3,888|0.82|91.2%|8.8%|
|Polynomial|3,377|3,727|0.73|86.4%|13.6%|

The results from the Corner machine learning models showed that the results were in perfect agreement with the linear and radial models. The results were in substantial agreement with the polynomial model.

Corner 2 SVM Model Results

|SVM Type|Correct 1B Predictions|Correct 3B Predictions|Kappa Value|Accuracy Rate|Error Rate|
|:-------|---------------------:|---------------------:|----------:|------------:|----------:|
|Linear|3,442|3,429|0.89|94.2%|5.8%|
|Radial|3,579|3,113|0.84|91.8%|8.2%|
|Polynomial|3,299|2,682|0.64|82.0%|18.0%|

The results from the Corner2 machine learning models showed that the results were in perfect agreement with the linear and radial models. The results were in substantial agreement with the polynomial model.

Middle SVM Model Results

|SVM Type|Correct 2B Predictions|Correct SS Predictions|Kappa Value|Accuracy Rate|Error Rate|
|:-------|---------------------:|---------------------:|----------:|------------:|----------:|
|Linear|3,363|1,616|0.37|69.2%|30.8%|
|Radial|3,397|1,656|0.39|70.3%|29.7%|
|Polynomial|3,762|672|0.19|61.7%|38.3%|

The results from the Middle machine learning models showed that the results were in fair agreement with the linear and radial models. The results were in slight agreement with the polynomial model.

M SVM Model Results

|SVM Type|Correct 2B Predictions|Correct SS Predictions|Kappa Value|Accuracy Rate|Error Rate|
|:-------|---------------------:|---------------------:|----------:|------------:|----------:|
|Linear|3,202|1,265|0.34|68.2%|31.8%|
|Radial|3,116|1,415|0.36|69.2%|30.8%|
|Polynomial|3,493|497|0.16|61.0%|39.0%|

The results from the M machine learning models showed that the results were in fair agreement with the linear and radial models. The results were in slight agreement with the polynomial model.

OFC SVM Model Results

|SVM Type|Correct C Predictions|Correct OF Predictions|Kappa Value|Accuracy Rate|Error Rate|
|:-------|---------------------:|---------------------:|----------:|------------:|----------:|
|Linear|2,614|8,222|0.85|94.2%|5.8%|
|Radial|2,572|8,233|0.84|94.0%|6.0%|
|Polynomial|2,152|8,249|0.74|90.4%|9.6%|

The results from the OFC machine learning models showed that the results were in perfect agreement with the linear and radial models. The results were in substantial agreement with the polynomial model.

OFC2 SVM Model Results

|SVM Type|Correct C Predictions|Correct OF Predictions|Kappa Value|Accuracy Rate|Error Rate|
|:-------|---------------------:|---------------------:|----------:|------------:|----------:|
|Linear|1,959|8,040|0.82|93.8%|6.2%|
|Radial|1,942|8,054|0.82|93.8%|6.2%|
|Polynomial|1,588|8,067|0.71|90.6%|9.4%|

The results from the OFC2 machine learning models showed that the results were in perfect agreement with the linear and radial models. The results were in substantial agreement with the polynomial model.

## kNN Nearest Neighbor Models with Five Nearest Neighbors

A second type of machine learning model that was created was a kNN nearest neighbor model that used five nearest neighbors. The kNN models were created for the Corner, Corner2, Middle, M, OFC, and OFC2 datasets.

Corner kNN Model Results

|Correct 1B Predictions|Correct 3B Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|3,878|4,057|0.93|96.5%|3.5%|

The Kappa value for the kNN model was 0.93. The Kappa value indicates that there is a perfect agreement amongst the model and the results.

Corner2 kNN Model Results

|Correct 1B Predictions|Correct 3B Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|3,630|3,434|0.94|96.9%|3.1%|

The Kappa value for the kNN model was 0.94. The Kappa value indicates that there is a perfect agreement amongst the model and the results.

Middle kNN Model Results

|Correct 2B Predictions|Correct SS Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|2,728|2,045|0.32|66.4%|35.6%|

The Kappa value for the kNN model was 0.32. This would indicate that there is a fair agreement between the model and results.

M kNN Model Results

|Correct 2B Predictions|Correct SS Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|2,532|1,740|0.30|65.3%|34.7%|

The Kappa value for this model was 0.3. This would indicate that there is a fair agreement of the results of the model.

OFC kNN Model Results

|Correct C Predictions|Correct OF Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|2,894|8,166|0.90|96.2%|3.8%|

The Kappa value for this model was 0.90. This would indicate that there is a perfect agreement of the results of the model.

OFC2 kNN Model Results

|Correct C Predictions|Correct OF Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|2,262|7,991|0.89|96.2%|3.8%|

The Kappa value for this model was 0.89. This would indicate that there is a perfect agreement of the results in the model.

# Random Forest Models

A third and final machine learning model that was created were Random Forest models. Random Forest models were created for the Corner, Corner2, Middle, M, OFC, and OFC2 datasets. 

The Random Forest model for the Corner data focused on using the POS variable as a factor variable in relation to the following eight variables: stint, G, GS, InnOuts, PO, A, E, and DP. 

Corner.rf Random Forest Results

|Correct 1B Predictions|Correct 3B Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|3,962|4,033|0.94|97.2%|2.8%|

 The Kappa value is 0.94. This indicates that there is a perfect agreement between the model and the results. The top 4 variables with the most importance were G, DP, A, and PO. 
 
 <img width="675" alt="image" src="https://user-images.githubusercontent.com/79723505/109395096-03ae7a00-78d7-11eb-9a26-8e202ca10803.png">

A second Random Forest model was created for the Corner data looking at the POS variable in relation to the G, DP, A, and PO variables.

Corner.rf2 Random Forest Results

|Correct 1B Predictions|Correct 3B Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|3,944|4,002|0.93|96.6%|3.4%|

 The Kappa value is 0.93. This indicates that there is a perfect agreement between the model and the results. The Corner.rf2 accuracy rate was a little bit less accurate than the Corner.rf accuracy.
 
 <img width="675" alt="image" src="https://user-images.githubusercontent.com/79723505/109395175-80d9ef00-78d7-11eb-95aa-70871eb88536.png">

The Random Forest model for the Corner2 data focused on using the POS variable as a factor variable in relation to the following eight variables: stint, G, GS, InnOuts, PO, A, E, and DP. 

Corner2.rf Random Forest Results

|Correct 1B Predictions|Correct 3B Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|3,676|3,393|0.94|97.0%|3.0%|

The Kappa value is 0.94. This indicates that there is a perfect agreement between the model and the results. The top 4 variables with the most importance were G, DP, A, and PO. 

<img width="675" alt="image" src="https://user-images.githubusercontent.com/79723505/109395269-f8a81980-78d7-11eb-9480-37c47b0cb3c3.png">

A second Random Forest model was created for the Corner2 data looking at the POS variable in relation to the G, DP, A, and PO variables.

Corner2.rf2 Random Forest Results

|Correct 1B Predictions|Correct 3B Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|3,667|3,360|0.93|96.3%|3.7%|

 The Kappa value is 0.93. This indicates that there is a perfect agreement between the model and the results. The Corner2.rf2 accuracy rate was a little bit less accurate than the Corner2.rf accuracy.
 
 <img width="675" alt="image" src="https://user-images.githubusercontent.com/79723505/109395355-5a688380-78d8-11eb-9bbb-027b5e4e9533.png">

The Random Forest model for the Middle data focused on using the POS variable as a factor variable in relation to the following eight variables: stint, G, GS, InnOuts, PO, A, E, and DP. 

Middle.rf Random Forest Results

|Correct 2B Predictions|Correct SS Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|3,013|2,082|0.41|70.9%|29.1%|

The Kappa value for the random forest model was 0.410. This would indicate that there is a moderate agreement amongst the results and the model. The top 4 variables with the most importance were PO, A, InnOuts, and E.

<img width="685" alt="image" src="https://user-images.githubusercontent.com/79723505/109395485-22157500-78d9-11eb-9a7c-8e37b79dac2d.png">

A second Random Forest model was created for the Middle data looking at the POS variable in relation to the E, InnOuts, A, and PO variables.

Middle.rf2 Random Forest Results

|Correct 2B Predictions|Correct SS Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|2,818|2,145|0.38|69.0%|31.0%|

The Kappa value for the random forest model was 0.38. This would indicate that there is a fair agreement amongst the results and the model. The Middle.rf2 accuracy rate was a little less than the Middle.rf accuracy rate.

<img width="685" alt="image" src="https://user-images.githubusercontent.com/79723505/109395590-a0721700-78d9-11eb-8797-d962caab27d7.png">

The Random Forest model for the M data focused on using the POS variable as a factor variable in relation to the following eight variables: stint, G, GS, InnOuts, PO, A, E, and DP. 

M.rf Random Forest Results

|Correct 2B Predictions|Correct SS Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|2,806|1,723|0.37|69.2%|30.8%|

The Kappa value for this model was 0.370. This would indicate that their is a fair agreement of the results of the model. The top 4 variables with the most importance were G, InnOuts, A, and PO.

<img width="685" alt="image" src="https://user-images.githubusercontent.com/79723505/109395699-38700080-78da-11eb-81d8-d37cdc7c4878.png">

A second Random Forest model was created for the M data looking at the POS variable in relation to the G, InnOuts, A, and PO variables.

M.rf2 Random Forest Results

|Correct 2B Predictions|Correct SS Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|2,599|1,684|0.30|65.4%|34.6%|

The Kappa value for this model was 0.30. This would indicate that their is a fair agreement of the results of the model. The top 4 variables with the most importance were G, InnOuts, A, and PO.

<img width="685" alt="image" src="https://user-images.githubusercontent.com/79723505/109395757-86850400-78da-11eb-9bd5-b749d651c35e.png">

The Random Forest model for the OFC data focused on using the POS variable as a factor variable in relation to the following eight variables: stint, G, GS, InnOuts, PO, A, E, and DP.

OFC.rf Random Forest Results

|Correct C Predictions|Correct OF Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|2,888|8,201|0.91|96.4%|3.6%|

The Kappa value for this model was 0.91. This would indicate that there is a perfect agreement of the results of the model. The top 4 variables with the most importance were G, InnOuts, A, and PO.

<img width="685" alt="image" src="https://user-images.githubusercontent.com/79723505/109395864-0f9c3b00-78db-11eb-8f4e-b510608f91ef.png">

A second Random Forest model was created for the OFC data looking at the POS variable in relation to the G, InnOuts, A, and PO variables.

OFC.rf2 Random Forest Results

|Correct C Predictions|Correct OF Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|2,946|8,174|0.92|96.7%|3.3%|

The Kappa value for this model was 0.92. This would indicate that there is a perfect agreement of the results in the model. The results for the OFC.rf2 were a little more accurate than the results from the OFC.rf model.

<img width="685" alt="image" src="https://user-images.githubusercontent.com/79723505/109396089-63f3ea80-78dc-11eb-88d7-96c17d2f2327.png">


The Random Forest model for the OFC2 data focused on using the POS variable as a factor variable in relation to the following eight variables: stint, G, GS, InnOuts, PO, A, E, and DP.

OFC2.rf Random Forest Results

|Correct C Predictions|Correct OF Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|2,214|8,028|0.89|96.1%|3.9%|

The Kappa value for this model was 0.89. This would indicate that there is a perfect agreement of the results in the model. The top 4 variables with the most importance were G, InnOuts, A, and PO.

<img width="685" alt="image" src="https://user-images.githubusercontent.com/79723505/109395966-bda7e500-78db-11eb-802e-d46b351a9e50.png">

A second Random Forest model was created for the OFC2 data looking at the POS variable in relation to the G, InnOuts, A, and PO variables.

OFC2.rf2 Random Forest Results

|Correct C Predictions|Correct OF Predictions|Kappa Value|Accuracy Rate|Error Rate|
|---------------------:|---------------------:|---------------------:|----------:|-------:|
|2,277|7,985|0.90|96.3%|3.7%|

The Kappa value for this model was 0.90. This would indicate that there is a perfect agreement of the results in the model. The results from the OFC2.rf2 Random Forest model was marginally better than the results from the OFC2.rf Random Forest model.

<img width="685" alt="image" src="https://user-images.githubusercontent.com/79723505/109396036-17101400-78dc-11eb-823f-6b42fca42086.png">

# Time Series Analysis of Corner and Corner2 Data

A univariate time series analysis was conducted on the four most important variables in the Corner and Corner2 datasets. The four most important variables for Corner and Corner2 from the Random Forest models were G, DP, A, and PO. After a time series was created by each specific variable, the Augmented Dickey-Fuller (ADF) test was conducted to determine if the time series was stationary. Here is the null and alternative hypotheses for the ADF test:

Ho: Time series is non-stationary 

Ha: Time series is stationary

Once the ADF test was completed for the time series, the Box-Ljung test was conducted to determine if the residual values were independently distributed.  Here is the null and alternative hypotheses for the Box-Ljung test:

Ho: The residuals are independently distributed.

Ha: The residuals are not independently distributed.

A forecast of the next 20 years for the residuals was conducted and then the next 20 observations for the data related to the specific variable was predicted.

Predictions for Corner Time Series Data

|Forecasted Variables|High 80%|High 95%|RMSE|
|:-------|---------------------:|---------------------:|----------:|
|Residuals of CornerG.ts|86|116|44.5|
|Games of CornerG.ts|89|120|46.1|
|Residuals of CornerPO.ts|880|1,195|461.4|
|Putouts of CornerPO.ts|395|596|296|
|Residuals of CornerA.ts|51|70|27.3|
|Assists of CornerA.ts|133|180|68.2|
|Residuals of CornerDP.ts|48|65|25.0|
|Double Plays of CornerDP.ts|39|56|26.4|

Predictions for Corner2 Time Series Data

|Forecasted Variables|High 80%|High 95%|RMSE|
|:-------|---------------------:|---------------------:|----------:|
|Residuals of Corner2G.ts|50|66|23.2|
|Games of Corner2G.ts|68|91|35.3|
|Residuals of Corner2PO.ts|499|664|242.4|
|Putouts of Corner2PO.ts|340|513|255.5|
|Residuals of Corner2A.ts|32|42|15.7|
|Assists of Corner2A.ts|89|117|41.2|
|Residuals of Corner2DP.ts|26|34|12.5|
|Double Plays of Corner2DP.ts|34|51|23.9|

# Time Series Analysis of Middle and M Data

A univariate time series analysis was conducted on the four most important variables in the Corner and Corner2 datasets. The four most important variables for Middle and M from the Random Forest models were E, InnOuts, A, and PO. After a time series was created by each specific variable, the Augmented Dickey-Fuller (ADF) test was conducted to determine if the time series was stationary. Here is the null and alternative hypotheses for the ADF test:

Ho: Time series is non-stationary 

Ha: Time series is stationary

Once the ADF test was completed for the time series, the Box-Ljung test was conducted to determine if the residual values were independently distributed.  Here is the null and alternative hypotheses for the Box-Ljung test:

Ho: The residuals are independently distributed.

Ha: The residuals are not independently distributed.

A forecast of the next 20 years for the residuals was conducted and then the next 20 observations for the data related to the specific variable was predicted.

Results of Middle Time Series Data

|Forecasted Variables|High 80%|High 95%|RMSE|
|:-------|---------------------:|---------------------:|----------:|
|Residuals of MiddleG.ts|93|125|45.5|
|Games of MiddleG.ts|103|136|48.6|
|Residuals of MiddlePO.ts|216|290|107.5|
|Putouts of MiddlePO.ts|176|243|99.5|
|Residuals of MiddleE.ts|26|35|12.3|
|Errors of MiddleE.ts|18|26|10.9|
|Residuals of MiddleInnOuts.ts|2,279|3,000|1,059|
|Inn Outs of MiddleInnOuts.ts|2,396|3,145|1,104.3|
|Residuals of MiddleA.ts|273|366|135.4|
|Assists of MiddleA.ts|288|388|146.6|

Results of M Time Series Data

|Forecasted Variables|High 80%|High 95%|RMSE|
|:-------|---------------------:|---------------------:|----------:|
|Residuals of MG.ts|57|75|26.2|
|Games of MG.ts|111|148|41.5|
|Residuals of MPO.ts|130|174|61.3|
|Putouts of MPO.ts|151|206|81.1|
|Residuals of MiddleInnOuts.ts|1,320|1,645|473.9|
|Inn Outs of MiddleInnOuts.ts|2,258|2,933|995.3|
|Residuals of MA.ts|160|212|76.7|
|Assists of MA.ts|252|333|120.2|

# Time Series Analysis of OFC and OFC2 Data

A univariate time series analysis was conducted on the four most important variables in the OFC and OFC2 datasets. The four most important variables for Middle and M from the Random Forest models were G, InnOuts, A, and PO. After a time series was created by each specific variable, the Augmented Dickey-Fuller (ADF) test was conducted to determine if the time series was stationary. Here is the null and alternative hypotheses for the ADF test:

Ho: Time series is non-stationary 

Ha: Time series is stationary

Once the ADF test was completed for the time series, the Box-Ljung test was conducted to determine if the residual values were independently distributed.  Here is the null and alternative hypotheses for the Box-Ljung test:

Ho: The residuals are independently distributed.

Ha: The residuals are not independently distributed.

A forecast of the next 20 years for the residuals was conducted and then the next 20 observations for the data related to the specific variable was predicted.

Results of OFC Time Series Data

|Forecasted Variables|High 80%|High 95%|RMSE|
|:-------|---------------------:|---------------------:|----------:|
|Residuals of OFCG.ts|87|109|32.8|
|Games of OFCG.ts|108|140|47.8|
|Residuals of OFCPO.ts|430|515|154.9|
|Putouts of OFCPO.ts|275|378|152.4|
|Residuals of OFCInnOuts.ts|1,633|2,118|685.0|
|Inn Outs of OFCInnOuts.ts|2,474|3,206|1,078.6|
|Residuals of OFCA.ts|107|138|76.7|
|Assists of OFCA.ts|23|33|16.0|

Results of OFC2 Time Series Data

|Forecasted Variables|High 80%|High 95%|RMSE|
|:-------|---------------------:|---------------------:|----------:|
|Residuals of OFC2G.ts|53|69|23.1|
|Games of OFC2G.ts|110|143|45.6|
|Residuals of OFC2PO.ts|230|302|106.2|
|Putouts of OFC2PO.ts|239|324|125.2|
|Residuals of OFC2InnOuts.ts|1,250|1,557|446.2|
|Inn Outs of OFC2InnOuts.ts|2,422|3,125|1,035.7|
|Residuals of OFC2A.ts|60|79|28.7|
|Assists of OFC2A.ts|15|21|9.9|

# Conclusions from Results


# References

Chen, Y.S. (2019). Interpretation of Kappa Values. Retrieved February 23, 2021 from 
	https://towardsdatascience.com/interpretation-of-kappa-values-2acd1ca7b18f.
	
Lahman, S. (2021). Fielding [Data set]. Sean Lahman. Retrieved January 17, 2021 from
	http://www.seanlahman.com/baseball-archive/statistics/.
	
R-bloggers.com. (2020). How to Remove Outliers in R. John. Retrieved February 3, 2021 from 
	https://www.r-bloggers.com/2020/01/how-to-remove-outliers-in-r/.
