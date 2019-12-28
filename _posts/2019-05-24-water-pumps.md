---
title: "Predictive Modeling Project"
date: 2019-05-24
tags: [machine learning, data wrangling, data science]
header:
    image: "/images/water_pump_challenge/water_pump_pic.jpg"
---

### Using Machine Learning to Solve Real-World Problems

Ten weeks into my [Lambda School](https://learn.lambdaschool.com/) experience, and we
have completed an end-to-end machine learning project. The project was set up as
a week-long Kaggle competition within our class, using Tanzania water pump data
from [DrivenData.org](https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/page/24/).
Our goal was to build a classification model to predict whether the water pumps
were functional, functional in need of repair, or non-functional based on the
given data.

This project tested the knowledge we’ve gained thus far: data acquisition, data
exploration, data wrangling, building a model, hyper-parameter optimization,
model validation, model interpretation, and creating visualizations. This blog
post will focus on model interpretation. If you are interested in seeing the
more technical aspects, you can find the notebooks in my GitHub repository
[here](https://github.com/JLDaniel77/Water-Pump-Project).

#### Insights From Data Exploration

<img src="/images/water_pump_challenge/permutation_importance.jpg">

After building a model, I ran a permutation importance report. This report
indicates that water quantity has the greatest impact on the model. Water
quantity is broken down into five categories: enough, insufficient, dry,
seasonal, and unknown. Looking at the graph below, we see that there are over
5,000 functioning water pumps with enough water. However, there are more than
2,000 water pumps with enough water, but non-functional.

<img src="{{ site.url }}{{ site.baseurl }}/images/water_pump_challenge/status_based_on_quantity.jpg">

From the chart above, we also see that the non-functioning pumps have the
highest number of dry water sources. This makes sense because a dry well would
be abandoned and neglected.

<img src="{{ site.url }}{{ site.baseurl }}/images/water_pump_challenge/status_based_on_quality.jpg">

The chart above shows more than 4,000 non-functioning water pumps have a water
quality of good. It is quite possible that some or all of the 2,000
non-functioning water pumps with a sufficient water supply (from the previous
chart) could also have drinkable water.

<img src="{{ site.url }}{{ site.baseurl }}/images/water_pump_challenge/status_based_on_quality_and_quantity.jpg">

From the chart above, we see that there are close to 2,000 water pumps that are
non-functional with water quality of good and water quantity of enough. Surely,
these water pumps would be a priority for repair, but how would you know which
pumps to repair first?

You could choose a sample of water pumps at random and visit each one to see if
they are in need of repairs. This may seem logical, but it might be a complete
waste of time and resources. In fact, based on the distribution of water pump
status in the training data seen below, we know that we have approximately a 46%
chance of correctly choosing to visit a water pump that is non-functional or
functional needs repair. Those are horrible odds.

<img src="{{ site.url }}{{ site.baseurl }}/images/water_pump_challenge/value_counts.jpg">

#### How do we improve results?

We need to build a predictive model to increase our ability to correctly
classify water pumps based on new data. With limited resources, it is not
possible to visit all 14,000+ water pumps, so a targeted approach is required.

<img src="{{ site.url }}{{ site.baseurl }}/images/water_pump_challenge/confusion_matrix.jpg">

The two charts above are a classification report and a confusion matrix. I have
combined non-functional and functional needs repair for the sake of simplicity.
The classification chart shows our model’s precision, recall, and f1-score; and
the confusion matrix shows the number of true positives, true negatives, false
positives, and false negatives based on our model.

As seen in the image below, precision is the percentage of predicted positives
that were true positives, and recall is the percentage of actual positives that
were correctly classified by our model. The confusion matrix shows that our
model correctly predicted 6,805 water pumps as functional and 5,030 water pumps
as non-functional. However, the model incorrectly predicted 1,530 non-functional
water pumps as functional, and it predicted 993 functional water pumps were
classified as non-functional.

The f1-score is the average of the precision and recall ratios. We use these
three metrics to test the accuracy of our model.

<img src="{{ site.url }}{{ site.baseurl }}/images/water_pump_challenge/precision_recall.jpg">

#### How does this relate to business?

Assume that we only have enough resources to visit 2,000 water pumps to make
repairs. We want to ensure that we are only sending out service crews to
non-functioning pumps. We run our model and sort our predicted values, so we are
selecting the top 2,000 pumps that our model has predicted as non-functional.

<img src="{{ site.url }}{{ site.baseurl }}/images/water_pump_challenge/actual_vs_predicted.jpg">

From the list of our top 2,000 predictions, we find that our model has correctly
predicted 1,982 water pumps as non-functional; this is 99.1% accuracy. Compared
to our earlier random sample where we only had 46% accuracy. If we had sent
service crews out based on our random sample, we would have sent them to 1,080
pumps that didn’t need repairs. That is a total waste of time, money, and labor.
With a predictive model, we can minimize costs and maximize resource
utilization.