### Introduction
This report describes the Data Wrangling efforts made for the "We rate Dogs" twitter project which is a part of Udacity's Data Analyst Nanodegree program.

Data Wrangling consists of :

Gathering data
Assessing data
Cleaning data

### The Data
The WeRateDogs Twitter archive contains basic tweet data(like tweet ID, timestamp, text, etc.) for all 5000+ of their tweets. The csv file provided by Udacity (twitter_archive_enhanced.csv) also contains columns which were extracted programatically from each tweet text- the rating numerator, rating denominator, dog's name, and dog stages (doggo, floofer, pupper, and puppo).

The extraction wasn't good so the provided csv file is untidy and has many quality issues that needs to be assessedand cleaned.

### Process

#### Gather
Data is gathered from three pieces of data as described below in a Jupyter Notebook titled wrangle_act.ipynb

The WeRateDogs Twitter archive (df) - "twitter_archive_enhanced.csv" file is manually downloaded.

The tweet image predictions (images) i.e., what breed of dog (or other object, animal, etc.) is present in each tweet according to a neural network. The file "image_predictions.tsv" is downloaded programmatically using the Requests library with the following URL (https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv)

(tweets_df) Each tweet's retweet count and favorite ("like") count and any additional data you which was found interesting. Using tweet id's in the We rate dogs archive, the twitter API could be queried for each tweet's JSON data using Python's tweepy library and store each tweet's entire set of JSON data in a file called tweet_json.txt file.

Once all the data is gathered successfully, I copied the files for assessing and cleaning process.

#### Assessing
After gathering each of the above pieces of data, next step is to assess them viually and programatically to identify and document Quality and Tidiness Issues.

Quality Issues are completness, accuracy, validity and consistency issues found in the dataframe. While Tidiness Issues are nothing but untidy data which is structural issues.

Quality Issues

Eroneous datatypes in df_all_clean (like in_reply_to_status_id, in_reply_to_user_id, retweeted_status_id, retweeted_status_user_id, tweet_id, timestamp)
Rating numerators with decimals not showing full float
Rating denominator can be float
Names which do not look like names, eg. a, an, the.
Change sources to more readable categories.
Missing values in retweet_count and favorite_count.
p1, p2, p3 have underscores in some names.
Inconsistency in p1, p2, p3 names, some names don't start with capital letter.
Tidiness Issues

no tweet_id column in tweets_df table
df, tweets_df and images are three separate tables (all tables)
We might want to add a gender column to know if the respective dog is a male or female.
doggo, floofer, pupper, puppo which describes different stages of dog are in separate columns.

#### Cleaning

Cleaning data is the third step in Data Wrangling. It is where quality and tidiness issues are fixed that were identified in Assess.

First a copy of all the dataframe is made: df, tweets_df, images as df_clean, tweets_df_clean, images_clean. Data can be cleaned manually or programatically, however manually is not recommended. All the three datasets are joined into one dataset "df_all_clean" and then performed cleaning. Cleaning process has three steps, Define, Code and Test. All the above mentioned Issues are fixed here in the cleaning process.

### Store Data
Store the clean dataset "df_all_clean" in a csv file named "twitter_archive_master.csv".
