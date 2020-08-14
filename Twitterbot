# Retweet bot for Twitter, using Python and Tweepy.
# Search query via hashtag or keyword.

#Setup twitter dev account
#Read this artical to know more https://docs.inboundnow.com/guide/create-twitter-application/

import tweepy
from time import sleep
import random

CONSUMER_KEY = ''
CONSUMER_SECRET = ''
ACCESS_KEY = ''
ACCESS_SECRET = ''

# change your Twitter application keys, tokens, and secrets


auth = tweepy.OAuthHandler(CONSUMER_KEY, CONSUMER_SECRET)
auth.set_access_token(ACCESS_KEY, ACCESS_SECRET)
api = tweepy.API(auth, wait_on_rate_limit=True, wait_on_rate_limit_notify=True)


FILE_NAME = 'last_seen_id.txt'

def retrieve_last_seen_id(file_name):
    f_read = open(file_name, 'r')
    last_seen_id = int(f_read.read().strip())
    f_read.close()
    return last_seen_id

def store_last_seen_id(last_seen_id, file_name):
    f_write = open(file_name, 'w')
    f_write.write(str(last_seen_id))
    f_write.close()
    return

    #q – the search query string
    #item(5) - how many of tweets you want to retweet
    #If you want to search multiple terms then separate it with OR keyword.
    #for single tearm search use q='example'

for tweet in tweepy.Cursor(api.search, q='#hashtag1 OR #hashtag2').items(100):
    randomlist = random.sample(range(0, 99), 99)
    int = random.choice(randomlist)
    print(int)
    #integer value can not be tweeted so
    #converting integer to string.
    string = f'{int}' 

    try:
        print('\nRT bot by @MrAkash3112' + ' ' + tweet.user.screen_name + '. ' + 'Attempting to retweet.')
        tweet.favorite()
        tweet.retweet()
        print('Retweet published successfully.')

        sleep(15)
        #sleep(15) - tweet interval (In Second)

    # Some basic error handling. Will print out why retweet failed, into your terminal.
    except tweepy.TweepError as error:
        print('\nError. Retweet not successful. Reason: ')
        print(error.reason)

    try:
        api.update_status('Your tweet should be included here @mentions #hashtags (should be less than 280 characters) ' + ' ' + string)
        print('Comment successful')
        
    except tweepy.TweepError as error:
        print('\nError. Tweet not Successful. Reason: ')
        print(error.reason)

    except StopIteration:
        break
