---
layout: single
permalink: /projects/
title: "Data Science Projects"
author_profile: true
header:
    image: "/images/chatt_header_img.jpg"
---

### NBA Career Longevity Prediction App
<div style="width:350px;height:350px;overflow:hidden;" >
    <a href="https://nba-clp.netlify.com/login">
        <img src="{{ site.url }}{{ site.baseurl }}/images/nba/nba_logo.jpg" width="350px" height="auto">
    </a>
</div>
The NBA career longevity app was a cross-functional team project, which was completed within a week. I was one of four data science students working on the project. Our objective was to create a model to predict an NBA player's career length based on their statistics. We also created a model to find the most similar player to the player selected by the end user. We then created an API with endpoints to send player stats and predictions to the frontend. My contributions:
* Web scraped [Basketball-Reference.com](https://www.basketball-reference.com/draft/NBA_2018.html) to get player images and relevant stats for years 1976-2018.
* Built the career longevity model using XGBoost regressor and hyperparameter tuning. Model results: R-sqared score of 0.85 and mean absolute error of 1.44.
* Built PostgreSQL database to store player stats with the output from both the career longevity and the k-nearest neighbors models.

### Twitoff Tweet Prediction App
<div style="width:350px;height:350px;overflow:hidden;" >
    <a href="https://jldaniel77-twitoff.herokuapp.com/">
        <img src="{{ site.url }}{{ site.baseurl }}/images/twitoff/twitter_logo.jpg" width="350px" height="auto">
    </a>
</div>
Twitoff is a beginning-to-end ETL (extract, transform, load) pipeline that compares the Tweets of two Twitter users to determine which user is most likely to Tweet a fake Tweet entered by the end user. The Twitter user's Tweets are extracted from the Twitter API, then saved in a PostgreSQL database. Next, the end user selects two twitter users to compare and types a fake Tweet in the text box. Once the end user clicks on the "compare users" button, each user's Tweets are converted to word embeddings using the Basilica API, then the word embeddings are run through a logistic regression model to determine which user is most likely to have Tweeted the fake text.

### Predictive Modeling Project: Tanzania Water Pump Challenge
<div style="width:350px;height:350px;overflow:hidden;" >
    <img src="{{ site.url }}{{ site.baseurl }}/images/water_pump_challenge/water_pump_pic.jpg" width="350px" height="auto">
</div>
The Tanzania Water Pump Challenge was a week long, in-class [Kaggle competition](https://www.kaggle.com/c/ds3-predictive-modeling-challenge/overview). The purpose of this project was to demonstrate beginning-to-end supervised learning skills, as well as an ability to communicate insights learned from the process. We were responsible for downloading the data, performing exploratory data analysis, data cleaning, feature engineering,training a model, and submitting predictions to the Kaggle competition. At the end of the week, we were required to publish a blog post detailing our findings with relevant visualizations. My post can be found [here](http://jeffdaniel.me/predictive-modeling-project/), and my GitHub repository can be found [here](https://github.com/JLDaniel77/Water-Pump-Project). 