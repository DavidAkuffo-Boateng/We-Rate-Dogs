# We-Rate-Dogs
Data wrangling on tweets made by WeRateDogs twitter account

## Introduction
This is a data wrangling project on a twitter account called WeRateDogs. This account tweets about dogs with pictures of the dogs attached, and are rated by followers. The sub-process of the data wrangling stage was followed through in getting the data and meta-data on this account.

## Gathering
Gathering of data came in three forms and in three different ways of gathering. The first dataset was a csv file already provided by Udacity, which contained basic tweets information. One notable variable in this dataset was the text column, which was made up of tweet texts, which the other variables (ratings, dog name, etc) was extracted. The dataset was further filtered for tweets with only ratings. the dataset was read by using pandas read_csv to load into a dataframe.

The second dataset was about meta_data predicting images of dog, using a neural network algorithm. The dataset was downloaded via the request- library, then reading the data with pandas read_csv using "\t" as the seaparator, since it was a tsv file.

The third dataset was also a meta_data, and made of tweet information (retweet_count and favorite_count). The gathering could be done in two forms:1. one was to query Twitter's API using the tweepy library. This would be done by creating an API object, which will be used to query each tweet's ID to get the intended data. Then you will write the JSON data from the query to a file named tweet_json.txt, with each tweet's JSON data on its own line. Then the the file is read line by line to create a pandas dataframe. This is done by applying for Twitter's developer account 2. The second option, which I opted for, was that the tweet_json.txt was already provided by Udacity. So I created an empty list and followed through with the reading of the JSON data line by line. Then I appended the list to a dictionary, and then converted that dictionary to a pandas dataframe.

## Assessing
This was done by visual and programmatic assessments. Visual assessment was done by using a text editor (Sublime Text). Programmatic assessments was done by using pandas functions like, describe, head, value_counts(), etc. After these assessments, some quality and tidiness issues were made known. Some of the quality issues were:

Incorrect input of ratings.
The text column containing retweets and replies.
Wrong dog names.
"None" values.
Some images were not dog images.

Some tidiness issues were as follows:
Dog type widened into four columns, instead of one.
One conscise breed of dog, instead of three.
Dataframes need to be joined to have one observational unit.

## Cleaning
Before cleaning was done, copies of the original dataset was made, and copies were therin cleaned for the quality and tidiness issues. For instance, incorrect ratings were cleaned by extracting both the numerator and denominator ratings from the text column, with the use of regular expression and .str.extract and .str.split. Another cleaning was removing all the retweets and replies values in the text column, in order to get only tweets. This was done by filtering retweets-related columns with non-null values, then droping those values. Solving the second tidiness issue, which was to get a conscise breed of dog, was by querying the dog predictions using a logical operator.

## Storing
The three datasets were merged using tweet_id as the commom key, and was saved in a csv file called twitter_archive_master.
