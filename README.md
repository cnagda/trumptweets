# trumptweets
Go to https://twitter.com/R3alFakeDonald (our twitter bot) or your make own
bot to see your madness unfurl.

## Overview

### Data
Our models use the 13,444 tweets found in `trumptweets_unclean.csv`. We removed punctuation, links, and mentions before tokenizing. 

### Model
We used the Microsoft Azure Text Analysis API to tag each tweet with keyphrases. For each key phrase we use the corresponding tweets to train a trigram language model. This allows us to generate more comprehensible tweets relevant to specific topics.

### Generation
The tweet generator takes a keyphrase or topic as input. A "seed word" is chosen randomly from the first tokens in all tweets related to the phrase. The next word in the sentence is predicted using the language model corresponding to the topic. We randomly capitalize some words and add punctuation to make the tweets more realistic. The Twitter bot randomly chooses a topic from a static list.

## Installation
Our project uses Python 3. Install dependendies using
```
pip install -r requirements.txt
```

## Usage

### Print a Tweet
To print a tweet for a keyphrase run
```
python3 model.py <keyphrase>
````

### Run Twitter Bot
Make your own config.py file with API keys for Twitter and Microsoft
Azure Text Analytics. You will need a Twitter developer account.

Set the following variables for Microsoft Azure:
* `subscription_key = "..."`
* `endpoint = "..."`
* `filename = "..."`
Set the following variables for Twitter
* `auth = tweepy.OAuthHandler("...")`
* `auth.set_access_token("...")`

Then run
```
python3 trumptweets.py
```
You can change the time interval between tweets in the code.

## Next Steps
To unleash it on the world, and possibly put it on an AWS or Azure cloud instance to run indefinitely.

## Credits
This project was made for CruzHacks 2020 by Garrett Webb and Chandni Nagda. 
Devpost listing is [here](https://devpost.com/software/what-would-trump-tweet-ds6wxl)
