# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Datascraping and Modelling Subreddits

### Table of Contents
[Problem Statement](#Problem-Statement)  
  
[Executive Summary](#Executive-Summary)  
  
[Table of Contents](#Table-of-Contents)  
  
[Data Dictionary and Glossary](#Data-Dictionary-and-Glossary)  
[Glossary and Definitions](#Glossary-and-Definitions)  
[Data Dictionary](#Data-Dictionary)  
  
[Imports and Cleaning](#Imports-and-Cleaning)  
[Module Import](#Module-Import)  
[Data Import & Cleaning](#Data-Import-&-Cleaning)  
[Data Preparation](#Data-Preparation)  
  
[EDA](#EDA)  
[Generate "Common Words" Function](#Generate-"Common-Words"-Function)  
[Determining Keywords for Analysis](#Determining-Keywords-for-Analysis)  
[Possible Data Imbalance](#Possible-Data-Imbalance)  
  
[Model Generation and Selection](#Model-Generation-and-Selection)  
[Creating the X and y Variables](#Creating-the-X-and-y-Variables)  
[Baseline Model](#Baseline-Model)  
[Logistic Regression Models](#Logistic-Regression-Models)  
[Naive Bayes Models](#Naive-Bayes-Models)  
[Model Selection](#Model-Selection)  
  
[Model Evaluation](#Model-Evaluation)  
  
[Conclusions](#Conclusions)  
  
[References](#References)

### Problem Statement:

We at Wookiepedia are the preeminent Star Wars knowledge base on the Internet, and have been helping the moderator team at r/StarWars with some fact-checking and moderation duties. Unfortunately, an engineer at Reddit merged the Star Trek and Star Wars Reddits by accident! Everybody knows that the Star Wars and Star Trek fandoms get along like Womp Rats and Rancors, so need to filter out the impure Star Trek content from the good Star Wars content, before the fans burn all of Reddit down arguing.
  
We are faced with a challenge though. Both universes are popular sci-fi epics with common terminology. We can't just look for "Star" or "Galaxy" and try to sort them apart that way. We need to dig deeper, to sort the Enterprises from our Endors, the Picards from our Plo-Koons, and the Romulans from our R2s.

### Executive Summary:

Our project was a success! After building 5 models (One baseline, two Logistic Regression, and two Naive Bayes), we chose to use a TFIDF Vectorizer Logistic Regression model. With a **Cross Val Score of .9329** across five tests, our model accurately predicted the subreddit 93.29% of the time. We would recommend making this tool available to the moderator community in r/StarWars and r/startrek for regular use if any cross-subreddit contamination happens again, or to possibly assess for trolls.

---

### Dataset

The below dataset as generated for the project.

- [Subreddit Datascrape](../datasets/scrape_results.csv)


---

### Data Dictionary
| Data Name  | Data Type  | Description  |
|---|---|---|
| title  |  object | The title of a given post  |
| selftext  |  object | The body of the post  |
| subreddit  |  object | The subreddit the post was in |
| num_comments  | integer  | The number of comments on the post  |
| score  | integer  |  The sum of the upvotes (positive ingegers) and downvotes (negative integers) on the post (higher is better) |  
  
### Glossary and Definitions  
A quick primer on what an r/anything is. Reddit is a giant communal forum, with a number of sub forums called subreddits. Each subreddit is denoted by r/, and each subreddit has its own rules, unique community, and moderating staff. Users can upvote or downvote a post, and the sum of those postiive and negative votes denotes the score of the post. High-scoring posts may be moved to Reddit's homepage, which is self-styled as the "front page of the Internet."  
  
Our data pulls from r/StarWars and r/startrek, the predominant subreddits for these two intellectual properties. It should be noted that both subreddits are considered "SFW", or Safe For Work, meaning that we didn't need to worry about possible cleaning of erotic or otherwise 'vulgar' content. While we are not morally judging that sort of content, there are a number of words in NSFW content that we'd further need to clean out, so are thankful that the moderating communities at our chosen subreddits did that work for us.  
  
While I would hope that a primer on what *Star Trek* and *Star Wars* aren't needed, we shall provide a brief overview. Both properties are cultural touchstone science fiction universes, composed of movies and television shows. They came to prominence in the 1970s, and have developed huge multi-generational followings that include global conventions, and in the case of *Star Wars*, which is a Disney property, an amusement park.