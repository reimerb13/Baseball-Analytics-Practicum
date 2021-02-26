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

# Exploratory Data Analysis

The Fielding dataset was merged with the first and last name of players in the People dataset from the Lahman library.
The Fielding2 dataset had 143,046 observations with 19 variables. The 19th variable was the name of the players. 
The missing values that existed in the Fielding2 data was imputed with the mean value for each column so that the Fielding2 data
contained no missing values. 

A subset of the Fielding2 dataset was created that looked at the lgID that focused on the AL league. This subset was called 
Fielding2_AL. 


