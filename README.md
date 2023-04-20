# USNewsHealth
Simply a repo for usnewshealth.txt and the formatting involved. Found in Health-News-Tweets.zip in https://archive.ics.uci.edu/ml/machine-learning-databases/00438/

Used the following Python script to make the formatting changes:
```py
import re

with open("usnewshealth.txt", "r", encoding="utf-8") as file:
    with open("usnewshealthformatted.txt", "w", encoding="utf-8") as new_file:
        for line in file:
            # Split the line by the "|" character
            split_line = line.split("|")
            # Get the tweet text (the last element in the split_line list)
            tweet_text = split_line[-1]
            # Remove any links from the tweet text
            tweet_text = re.sub(r'http\S+', '', tweet_text)
            # Remove all symbols from the tweet text
            tweet_text = re.sub(r'[^\w\s]', '', tweet_text)
            # Remove the new line at the end of tweet_text
            tweet_text = tweet_text.strip()
            # Remove RT
            tweet_text = re.sub('RT ', '', tweet_text)
            # Make every character lowercase
            tweet_text = tweet_text.lower()
            
            print (tweet_text)
            new_file.write(tweet_text + "\n")

```
