# Predicting Magnus Carlsen’s Rapid Chess Game Outcomes



### Overview

###### This project analyzes and models Magnus Carlsen’s Rapid chess games played on Chess.com with the goal of predicting whether he wins a game. The analysis progresses from a strong rating-based baseline to more advanced early-game feature engineering.

###### 

###### The focus is not on maximizing leaderboard scores, but on understanding what information meaningfully contributes to outcome prediction in Rapid chess.

### 

### Dataset

###### Source: Chess.com Public API (Uploaded by Dhrubang Talukdar)

###### Player: Magnus Carlsen

###### Game formats: Classical, Rapid, Blitz

###### Scope of this project: Rapid games only



### Key fields:

###### \- Player and opponent ratings

###### \- Game result

###### \- Player color

###### \- Game end date

###### \- Full move sequence in SAN notation

###### 

###### Only games played on Chess.com are included. Over-the-board and Lichess games are excluded.



### Problem Definition

###### The task is framed as a binary classification problem:

###### 

###### Win → 1

###### Loss or Draw → 0

###### 

###### Draws are grouped with losses due to their frequency in Rapid chess and the limited dataset size, which would make a multi-class formulation unstable.



###### The objective is to predict outcomes using:

###### \- Information available before the game

###### \- Limited early-game opening information (first 10 full moves)



### Methodology

#### 

#### 1\. Data Preparation

###### \- Filtered dataset to include Rapid games only

###### \- Created a binary target variable (target\_win)

###### \- Parsed game dates and sorted data chronologically

###### \- Implemented a time-based train–validation split to prevent future information leakage

#### 

#### 2\. Baseline Model (Pre-game Features)

###### A Logistic Regression model is trained using only pre-game information:

###### \- Player rating

###### \- Opponent rating

###### \- Rating difference

###### \- Player color

###### 

###### This model establishes a strong and interpretable baseline.

###### 

###### Evaluation is performed using F1-score due to class imbalance.



#### 3\. Early-game Feature Engineering

###### Features are extracted from the first 10 full moves of each game.

###### Only Magnus Carlsen’s moves are considered.

###### Opponent moves are excluded.

###### No midgame or endgame information is used.

###### 

###### Features include:

###### \- Early queen development

###### \- Kingside and queenside castling

###### \- Pawn and minor piece development

###### \- Early captures and checks



#### 4\. Model Comparison

###### Models evaluated:

###### \- Logistic Regression (pre-game only)

###### \- Logistic Regression (pre-game + early-game)

###### \- Random Forest (pre-game + early-game)

###### 

###### Results show that player rating remains the dominant predictor in Rapid chess.

### 

### Key Insights

###### \- Ratings dominate outcome prediction

###### \- Early-game features add limited predictive value

###### \- Non-linear models handle early-game structure better, but gains are modest

