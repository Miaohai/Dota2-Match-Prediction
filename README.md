# Dota2-Match-Prediction
Predicting win rate of Dota2 matches and Recommending Heroes based on team composition using Neural Network

# Motivation
1. After reviewing the available literature review, we realised that the current models that predicted the win rate of the Dota2 matches overlook certain features, such as Hero Counter rate and synergy, that we believe are influential to increasing the accuracy of their models. Therefore, we are trying to improve current predictor models by adding those feactures and use different machine learning models to provide best results.

2. Build a Hero recommendation system which can recommend to the player the best 5 Heroes that maximizes their chances of winning a match.

# Dataset
We used the dataset provided on Kaggle by the user Devin Anzelmo which contained 50000 Dota matches. While the dataset itself was quite rich, with over 186 different columns (split into 18 different csv files)

Kaggle:  URL:https://www.kaggle.com/devinanzelmo/dota-2-matches
 
# File Structures:
        1. All_CSV_Files 
                - Contains all the data files
        2. EDA - Exploratory Data Analysis 
                - Most popular Dota2 Hero, Hero Map, Statistics about position in Dota2)
        3. Feature Engineering
                - Counter Rate
                - Synergy
        4.Win Preditor Models 
                - Base model (Logistic Regression)
                - Decision Tree
                - Logistic Regression
                - Neural Network
                - Random Forest
        5. Recommender
                - Creating dataset for recommender model
                - Recommender
           
# Prerequisites
What things you need to install the software

* Download Anaconda
* Install packages
  * jupyter notebook
  * numpy
  * pandas
  * matplotlib
  * os
  * seaborn
  * sklearn
  * itertools
  * tensorflow


# Methodology  
Based on our literature review, we realised that most of the research authors used Logistic Regression for their models. We used the logistic regression model provided by the SKlearn python library as our baseline model from which we compared our future model’s accuracy against to determine the effectiveness of our features and models.

## Feature Engineering

With limited relevant features, our team had to create new features for the win/loss predictor. The proposed features were Hero selection, Hero counter, Hero synergy and skill Rating.

![image](https://user-images.githubusercontent.com/47818397/84619282-39f1c800-af07-11ea-9b8b-334e81dde4c8.png)

![image](https://user-images.githubusercontent.com/47818397/84619326-54c43c80-af07-11ea-8bfb-c1460828d56f.png)


## Classifiers

Based on past literature review and course materials, our team decided to test out the following models: Neural Network, Logistic Regression, Decision Tree and Random Forest. In addition, a recommendation model to provide players with the best Hero to choose based on team and opponent composition is built using the best of these models.

![image](https://user-images.githubusercontent.com/47818397/84619354-66a5df80-af07-11ea-8744-e91c31bd88ac.png)

## Recommender

The objective of the model here is when given a team of 4 radiant and 5 dire team members, we recommend the last radiant Hero with the 5 Heroes with the highest win rate. Using a dataset where the Hero selection variables are already set, we run through to generate the team synergy and counter rates using the values calculated in the feature engineering above. 
Using these values, we run it through the Neural Network model to predict the win rate for each Hero lineup excluding those 9 Heroes already selected. We then loop through the results to take the 5 Heroes with the highest win rate to recommend to the player.


![image](https://user-images.githubusercontent.com/47818397/84619375-76252880-af07-11ea-82c5-09b9fdde3dc6.png)

![image](https://user-images.githubusercontent.com/47818397/84619407-8a692580-af07-11ea-9244-05cba6dbeaa7.png)

# Results and Discussion
In this section, we will be discussing the different evaluation metrics used (such as accuracy and f1-score) to evaluate the performance of the different algorithms

## Accuracy

![AccuracyJPG](https://user-images.githubusercontent.com/47818397/84618704-863c0880-af05-11ea-8746-c28755c46399.JPG)

The accuracy rate for each of the features, ‘Synergy’, ‘Counter’, ‘Synergy with Counter’, were generated based on 4 models (Neural Network, Logistic Regression, Random Forest and Decision Tree). The highest accuracy rate for ‘Synergy’ feature was based on the Logistic Regression Model with 66.97%, while Neural Network produced the highest accuracy rate for ‘Counter’ and ‘Synergy with Counter’ features with 79.8% and 81.5% respectively.

## Model Performance Evaluation

![image](https://user-images.githubusercontent.com/47818397/84618861-006c8d00-af06-11ea-9346-49344d7e8f43.png)

After evaluating the accuracy of our features based on our models, the models’ performance was evaluated with F1-Score, Recision, Recall, Logloss and AUC, which will be further elaborated on later. Logloss was slightly different as the neural network used cross-hinged loss to optimise the model so the value was significantly lower than the other models.

From the table above, amongst the four models, Neural Network performed the best across all metrics . 

# Conclusion and Future Work

A limitation of our current model is that it fails to take into account the Heroes banned in the Hero selection phase. In Dota2 competitions, the matches played in Captain Draft mode which further divides the Hero selection phase into two additional phases - picking and banning. During this phase, teams will also take turns banning Heroes from the Hero pool and similar to the picking phase, once the Hero is banned, no other player may choose that Hero. Unfortunately, our dataset did not provide us with the information on the Heroes that were banned as it only contained ranked All Pick matches rather than Captain Draft matches. 

Thus, for our Hero recommender model to be used in competitive matches, we need to take into account the Heroes banned. However, due to time constraints, we were unable to obtain the game data from the Dota2 APi. As such, a possible future work would be to obtain the matches from dota2 api to obtain the relevant Captain Draft matches to incorporate these features in our Hero prediction model and subsequently into our Hero recommender model. 

In addition, our current recommendation model is based only on the Neural network model as this provides us with the best results based on all the performance metrics. Therefore, a possible future work is to implement our recommender model with the rest of the predictor models like Logistic Regression and Random Forest. Doing so would allow us to compare differences to see if Logistic Regression or Random Forest will contribute to a better recommender system. Future work can also be done where we can collect data on the success of the recommenders and analyse the datasets there to observe which models are the best in providing the Hero recommendation. 

By only using the Heroes picked by each player at the start of a Dota2 match, our prediction models were able to predict the winners of any given Dota2 match with an accuracy rate of 81.5%. This was mainly due to our feature engineering process whereby we were able to create features such as “Synergy” and “Counter” to capture the innate strengths and weaknesses of each individual Hero, allowing us to train our models to such a high degree of accuracy. Our Neural Network model provides a recommendation that the average player to use for their casual Dota2 matches to improve their gameplay while providing a great baseline model for future work to be done to incorporate bans for future use in competitive Dota2 matches.

# Team
 * Jamie Chua Hui Yi
 * Lim Si Ling
 * Miao Hai
 * Tan Si Kit
 * Teo Wei Jian Autumn
