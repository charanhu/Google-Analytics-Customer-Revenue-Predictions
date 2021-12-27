# [Google Analytics Customer Revenue Prediction](https://www.kaggle.com/c/ga-customer-revenue-prediction/data)
The 80/20 rule has proven true for many businesses–only a small percentage of customers produce most of the revenue. As such, marketing teams are challenged to make appropriate investments in promotional strategies.

![alt text](https://github.com/charanhu/Google-Analytics-Customer-Revenue-Prediction/blob/main/google_store.jpg)

In this competition, you’re challenged to analyze a Google Merchandise Store (also known as GStore, where Google swag is sold) customer dataset to predict revenue per customer. Hopefully, the outcome will be more actionable operational changes and a better use of marketing budgets for those companies who choose to use data analysis on top of GA data.

### Important Note: We have now updated the data to work with the new forward-looking problem formulation. 

Note that in this competition you will be predicting the target for ALL users in the posted test set: test_v2.csv, for their transactions in the future time period of December 1st 2018 through January 31st 2019.

## What files do I need?
You will need to download train_v2.csv and test_v2.csv. These contain the data necessary to make predictions for each fullVisitorId listed in sample_submission_v2.csv.

Unfortunately, due to time constraints, the BigQuery version of this data will not be made available immediately.

## What should I expect the data format to be?
Both train_v2.csv and test_v2.csv contain the columns listed under Data Fields. Each row in the dataset is one visit to the store. Because we are predicting the log of the total revenue per user, be aware that not all rows in test_v2.csv will correspond to a row in the submission, but all unique fullVisitorIds will correspond to a row in the submission.

## IMPORTANT: 
Due to the formatting of fullVisitorId you must load the Id's as strings in order for all Id's to be properly unique!
There are multiple columns which contain JSON blobs of varying depth. In one of those JSON columns, totals, the sub-column transactionRevenue contains the revenue information we are trying to predict. This sub-column exists only for the training data.

## What am I predicting?
We are predicting the natural log of the sum of all transactions per user. Once the data is updated, as noted above, this will be for all users in test_v2.csv for December 1st, 2018 to January 31st, 2019. For every user in the test set, the target is:

![alt text](https://github.com/charanhu/Google-Analytics-Customer-Revenue-Prediction/blob/main/performance_matric.png)

Note that the dataset does NOT contain data for December 1st 2018 to January 31st 2019. You must identify the unique fullVisitorIds in the provided test_v2.csv and make predictions for them for those unseen months.

## How are the Public & Private Leaderboards calculated?
sample_submission_v2.csv is composed of all fullVisitorIds for the 5/1/18 to 10/15/18 time period. The public leaderboard submission for this file is based on a separate timeframe than the private leaderboard.

The Public LB is being calculated for those visitors during the same timeframe of 5/1/18 to 10/15/18. This is all publicly-available for the target prediction, but intended to provide some means of signal for those who wish to use it in that way. The Private LB is being calculated on the future-looking timeframe of 12/1/18 to 1/31/19 - for those same set of users.

Therefore, your submission that is intended for the public LB timeframe will be different from the private LB timeframe, which will be rescored/recalculated on the future timeframe.

Knowing this, competitors should be making explicit final submission selections for those submissions which represent what they expect those future-looking predictions to be. These final submission selections for which this competition permits 2, per the rules, can be made under "My Submissions" by the final submission deadline.

## File Descriptions
train_v2.csv - the updated training set - contains user transactions from August 1st 2016 to April 30th 2018.

test_v2.csv - the updated test set - contains user transactions from May 1st 2018 to October 15th 2018.

sample_submission_v2.csv - a updated sample submission file in the correct format. Contains all fullVisitorIds in test_v2.csv. Your submission's PredictedLogRevenue column should make forward-looking predictions for each of these fullVisitorIds for the timeframe of December 1st 2018 to January 31st 2019. Review "What am I predicting?" above for details.

## Data Fields
fullVisitorId- A unique identifier for each user of the Google Merchandise Store.

channelGrouping - The channel via which the user came to the Store.

date - The date on which the user visited the Store.

device - The specifications for the device used to access the Store.

geoNetwork - This section contains information about the geography of the user.

socialEngagementType - Engagement type, either "Socially Engaged" or "Not Socially Engaged".

totals - This section contains aggregate values across the session.

trafficSource - This section contains information about the Traffic Source from which the session originated.

visitId - An identifier for this session. This is part of the value usually stored as the _utmb cookie. This is only unique to the user. For a completely unique ID, you should use a combination of fullVisitorId and visitId.

visitNumber - The session number for this user. If this is the first session, then this is set to 1.

visitStartTime - The timestamp (expressed as POSIX time).

hits - This row and nested fields are populated for any and all types of hits. Provides a record of all page visits.

customDimensions - This section contains any user-level or session-level custom dimensions that are set for a session. This is a repeated field and has an entry for each dimension that is set.

totals - This set of columns mostly includes high-level aggregate data.

## External Data
External data is permitted for this competition, per this forum post. This includes the Google Merchandise Store Demo Account. Although the Demo Account contains the predicted variable, final standings will not benefit from access to this external data, because it requires future-looking predictions.

(https://gist.github.com/charanhu/9aaf5bf07b42e0d1999d0afaa361fb83)
