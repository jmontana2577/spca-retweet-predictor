# SPCA Retweet Predictor
This is the first phase of my capstone project for <a href="https://generalassemb.ly/education/data-science-immersive">General Assembly's Data Science Immersive</a> course. 

## Contents of Repo
- `data` folder: contains most of the pickle files used in this project (some were too large to include in repo)
- `ipynb` folder: contains 9 jupyter notebooks, one for each step of the project (except two notebooks for first step)
- `src` folder: contains a <a href="https://github.com/Jefferson-Henrique/GetOldTweets-python">repo</a> from Jefferson Henrique that was used to gather tweets. I modified the `got3` functionality some to work in Python 3.
- `non-tech-summary.pdf`: 13-page PDF printout of Google Slides non-technical summary presentation (includes notes)
- `non-tech-summary-google-slides.md`: a markdown file that contains a link to the <a href="https://docs.google.com/presentation/d/1g8UZ5UNSWR-gyqtMHZb2e5vkQFJl9hq3tPrGgMc3DK0/edit?usp=sharing">Non-technical Summary Presentation</a>

## Project Background Info
My wife and I volunteered for 5 years at the San Francisco SPCA and when we could no longer keep the time commitment, we remained donors to the organization. We also adopted <a href="https://photos.app.goo.gl/m74JvdTSZyvDNxbK2">Kahlua</a> in April 2015 when she was 8 months old. I embarked upon this project in an effort to use my data science skills to benefit the SF SPCA. 

## Project Steps
### Notebooks 1a and 1b:
This step is all about gathering tweets. Notebook `1a-get-tweets-got3.ipynb` uses Jefferson's GetOldTweets functionality to gather tweets for 9 SPCA organizations in the US and Canada. The tweets dated back to each organization's Twitter account creation and were gathered during the last week of August 2017 (over 90,000 in all). Notebook `1b-get-tweets-streaming.ipynb` was used to pull tweets from the Twitter Streaming API over the weekend of September 9, 2017. I pulled a little over 1 million tweets from random Twitter accounts in the US and Canada. These tweets would eventually be used to build the encoder to transform the text of the SPCA tweets.

### Notebook 2:
This step was for intial engineering of the data.
- Convert pandas timestamp on tweets to datetime aware object adjusted for time zone
- Added features: country, year, month, hour, day of week
- Combined all the individual organization data frames into one
- Create new column that has both hashtags and mentions

### Notebook 3:
Do some exploratory data analysis on the non-text aspects of the tweets and formulate next steps.

### Notebook 4:
I decided to fit models on three different portions of tweet data: the text, the metadata (time, date, presence of hashtags, etc.) and the hashtags/mentions. This notebook splits the data into the necessary sets for a stacked model (50% layer 1 training set, 13% for layer 1 test set, 30% for blender training set, and 7% for blender test set) and then fits models on the text portion using natural language processing techniques.

### Notebook 5:
This notebook fits models on the metadata of the tweets.

### Notebook 6:
Also uses natural language processing techniques to fit models to the text in the hashtags and mentions of the tweets.

### Notebook 7:
This is the final piece of the model, where the results from the previous three notebooks are the input for the blender model. The blender model delivers a final prediction of retweets for each tweet.

### Notebook 8:
This notebook is where the results of the overall model are analyzed.

## Next Steps
1. Try to tune the various models to get better results.
1. Create a web interface where users can enter a draft tweet and have its retweets predicted (and possibly recommend improvements to be made to the tweet for more retweets).
1. Attempt to connect number of retweets for these organiations to adoptions, donations and/or volunteer sign-ups.
1. Add another portion to the stacked model that will incorporate photo analysis to the predictions.
