# twitter-data-wrangling
Project 4 from Udacity Data Analyst Nanodegree
# Introduction
In this project I gathered, assessed and cleaned data from the WeRateDogs twitter
account.

# Data Gathering
The data was gathered from three different sources:
● The twitter-archive-enchaced.csv was downloaded manually and I used the
pandas function read_csv to read it into a dataframe.
● The image-prediction.tsv was downloaded programmatically using the
requests library and I used the pandas function read_csv to read it into a
dataframe.
● The tweet-json.txt was gathered using the Twitter API and the tweepy library.
Data Assessing
After gathering the data and loading it into three different dataframes, I assessed it
both visually and programmatically and the following quality and tidiness issues were
found:

## Quality issues
1. The `tweet_id` column in the `df_image_prediction` and in the `df_twitter_archive`
is an int, while it is a string in the other dataframe.
2. The `retweet_count` and the `favorite_count` in the `df_api` are strings, they
should be int as they represent numbers.
3. The `df_twitter_archive` has rows of tweets that were retweets. We only want
original ratings from the WeRateDogs account.
4. The `timestamp` column in the `df_twitter_archive` dataframe should be of
datetime type.
5. The `rating_denominator` in the `df_twitter_archive` is not always equal to 10.
6. The `name`, `doggo`, `floffer`, `pupper` and `puppo` columns in the
`df_twitter_archive` dataframe have the string value 'None' instead of the null value
for null values.
7. Dogs named 'a' and 'the' in the `df_twitter_archive`.
8. The `df_twitter_archive` has rows of tweets that were replys. We only want original
ratings in the dataframe.
## Tidiness issues
1. As all tables are about the tweets, we should have a single dataframe.
2. The `doggo`, `floffer`, `pupper` and `puppo` columns in the `df_twitter_archive`
dataframe should be just one categorical column.
# Data Cleaning
Finally, I copied the original data and cleaned it using a range of Python and pandas
functions such as:
● Replacing incorrect values with the null value using replace
● Dropping rows that weren't useful for the analysis, such as retweets and
replies from the WeRateDogs account
● Used the melt function from pandas to create a categorical column for the
different types of dogs (doggo, floffer, pupper and puppo)
● Converted data types from columns that were int and should be strings
● Converted data types from columns that were strings and should be int
● Joined all the three dataframes into a single master dataframe
● Converted columns with information about date and time to the datetime data
type
● Replaced names of dogs that weren't correct with the null value
● Corrected the rating denominator so that it would be 10 for all cases, as
expected
