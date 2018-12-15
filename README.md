# Introduction to Market Basket Analysis in Python

## Introduction

There are many data analysis tools in the market and it can be challenging to know which ones to use in a particular situation. A useful (but somewhat overlooked) technique is called association analysis which attempts to find common patterns of items in large data sets. One specific application is often called market basket analysis. The most commonly cited example of market basket analysis is the so-called “beer and diapers” case. The basic story is that a large retailer was able to mine their transaction data and find an unexpected purchase pattern of individuals that were buying beer and baby diapers at the same time.

While these types of associations are normally used for looking at sales transactions; the basic analysis can be applied to other situations lik online recommendation engines.

If you have some basic understanding of the python data science world, your first inclination would be to look at scikit-learn for a ready-made algorithm. However, scikit-learn does not support this algorithm. Fortunately, the very useful `MLxtend` library by **Sebastian Raschka** has a a an implementation of the `Apriori` algorithm for extracting frequent item sets for further analysis.

The rest of this article will walk through an example of using this library to analyze a relatively large online retail data set and try to find interesting purchase combinations. By the end of this article, you should be familiar enough with the basic approach to apply it to your own data sets.


## Why Association Analysis?

In today’s world, there are many complex ways to analyze data (clustering, regression, Neural Networks, Random Forests, SVM, etc.). The challenge with many of these approaches is that they can be difficult to tune, challenging to interpret and require quite a bit of data prep and feature engineering to get good results. In other words, they can be very powerful but require a lot of knowledge to implement properly.

Association analysis is relatively light on the math concepts and easy to explain to non-technical people. In addition, it is an unsupervised learning tool that looks for hidden patterns so there is limited need for data prep and feature engineering. It is a good start for certain cases of data exploration and can point the way for a deeper dive into the data using other approaches.

As an added bonus, the python implementation in MLxtend should be very familiar to anyone that has exposure to scikit-learn and pandas. For all these reasons, I think it is a useful tool to be familiar with and can help you with your data analysis problems.

One quick note - technically, market basket analysis is just one application of association analysis. In this post though, I will use association analysis and market basket analysis interchangeably.

### Association Analysis 101

Association rules are normally written like this: {Diapers} -> {Beer} which means that there is a strong relationship between customers that purchased diapers and also purchased beer in the same transaction.

In the above example, the {Diaper} is the **antecedent** and the {Beer} is the **consequent**. Both antecedents and consequents can have multiple items. In other words, {Diaper, Gum} -> {Beer, Chips} is a valid rule.

**Support** is the relative `frequency` that the rules show up. In many instances, you may want to look for high support in order to make sure it is a useful relationship. However, there may be instances where a low support is useful if you are trying to find “hidden” relationships.

**Confidence** is a measure of the `reliability` of the rule. A confidence of .5 in the above example would mean that in 50% of the cases where Diaper and Gum were purchased, the purchase also included Beer and Chips. For product recommendation, a 50% confidence may be perfectly acceptable but in a medical situation, this level may not be high enough.

**Lift** is the ratio of the observed support to that expected if the two rules were `independent`. The basic rule of thumb is that a lift value close to 1 means the rules were completely independent. Lift values > 1 are generally more “interesting” and could be indicative of a useful rule pattern.

### Note

The specific data for this article comes from the UCI Machine Learning Repository and represents transactional data from a UK retailer from 2010-2011. This mostly represents sales to wholesalers so it is slightly different from consumer purchase patterns but is still a useful case study.

## Don't forget!

If you like this notebook or have anything to share or improvise, [tweet me](http://www.twitter.com/sh0kat) (@sh0kat) and I'll get back to you asap.

Keep learning,

Shokat Ali
<br>
https://www.linkedin.com/in/shokatsaifi/
