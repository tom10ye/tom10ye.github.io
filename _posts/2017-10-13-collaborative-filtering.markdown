---
layout:     post
title:      "Collaborative Filtering"
subtitle:   "Recommendation algorithm used by Amazon"
date:       2017-10-13
author:     "Tom"
layout:     post
header-img: "img/post-bg-digital-native.jpg"
tags:
    - Recommendation
---


# What is that?

When designing a recommendation system, there are two major ways to go about it. We’ve already talked about content-based filtering, but what do you do when your content is simply too massive or diverse to manually apply attributes? For that, there’s collaborative filtering, a technique that’s widely used across social media, retail, and streaming services. In this article, we’ll explore how collaborative filtering works, where it’s used, and what skills you might need to get started.

For all the sophisticated math and machine learning techniques involved, the concept behind collaborative filtering is pretty straightforward: It’s based on the idea that people who share an interest in certain things will probably have similar tastes in other things as well. You experience collaborative filtering first-hand every time you go online and see “Customers Who Bought This Item Also Bought,” or “Users like you also liked…”


# WHY COLLABORATIVE FILTERING?

The main difference between collaborative filtering and content-based filtering is conceptual. Where content-based filtering is built around the attributes of a given object, collaborative filtering relies on the behavior of users. This approach has some distinct advantages over content-based filtering:

>It benefits from large user bases. Simply put, the more people are using the service, the better your recommendations will become, without doing additional development work or relying on subject area expertise.

>It’s flexible across different domains. Collaborative filtering approaches are well suited to highly diverse sets of items. Where content-based filters rely on metadata, collaborative filtering is based on real-life activity, allowing it to make connections between seemingly disparate items (like say, an outboard motor and a fishing rod) that nonetheless might be relevant to some set of users (in this case, people who like to fish).

>It produces more serendipitous recommendations. When it comes to recommendations, accuracy isn’t always the highest priority. Content-based filtering approaches tend to show users items that are very similar to items they’ve already liked, which can lead to filter bubble problems. By contrast, most users have interests that span different subsets, which in theory can result in more diverse (and interesting) recommendations.

>It can capture more nuance around items. Even a highly detailed content-based filtering system will only capture some of the features of a given item. By relying on actual human experience, collaborative filtering can sometimes recommend items that have a greater affinity with one another than a strict comparison of their attributes would suggest.


# Two Methods: User-Item vs. Item-Item

There are two approaches to collaborative filtering, one based on items, the other on users. Item-item collaborative filtering was originally developed by Amazon and draws inferences about the relationship between different items based on which items are purchased together. The more often two items (say, peanut butter and jelly) appear in the same shopping cart or user history, the “closer” they’re said to be to one another. So, when someone comes and adds peanut butter to their cart, the algorithm will suggest things that are close, like jelly or white bread, over things that aren’t, like motor oil.

User-item filtering takes a slightly different approach. Here, rather than calculating the distance between items, we calculate the distance between users based on their ratings (or likes, or whatever metric applies). When coming up with recommendations for a particular user, we then look at the users that are closest to them and then suggest items those users also liked but that our user hasn’t interacted with yet. So, if you’ve watched and liked a certain number of videos on Facebook, Facebook can look at other users who liked those same videos and recommend one that they also liked but which you might not have seen yet.

The important point here is that in both the examples above, the system has no idea why any of these items are related to one another, it only knows that they either show up in the same basket together, or that they’re liked by people with similar preferences. In some cases, though, this can be a feature rather than a shortcoming, especially in cases where the items to be filtered are extremely heterogeneous, as in online retailers or social networks. (Note: This can also lead to some unanticipated situations, as when Amazon’s algorithm began unintentionally suggesting drug paraphernalia to users who bought a particular scale.)

# HOW TO CALCULATE SIMILARITY?
The above descriptions are meant to be general overviews of how collaborative filtering techniques are typically implemented. Behind each implementation there are a number of different techniques for measuring the similarity of two different items or users. Which one is right for a given recommender system depends on both the use case and the nature of the data involved.

When the data you’re working with is dense, a simple Euclidean distance measure can work. In reality, though, data (especially ratings) is often sparse. In these cases, cosine similarity is often used. There are other measures (Pearson correlation coefficient, k-nearest-neighbors, etc.). Fortunately, most of these functions are easily performed in Python (assuming you have the SciPy and scikit-learn libraries). Are you looking for a data scientist to build a recommendation engine? Create a job post on Upwork today.


# CHALLENGES OF COLLABORATIVE FILTERING

>Complexity and expense. Collaborative filtering algorithms can run into scalability problems when the number of users and items gets too high (think in tens of millions of users and hundreds of thousands of items), especially when recommendations need to be generated in real-time online. Potential solution: This is where distributed clusters of machines running Hadoop or Spark come in handy. Depending on your project, it may also be possible to calculate relationships offline overnight by way of batch processing, which makes serving recommendations much quicker even if they’re no longer being updated in real-time.

>Data sparsity. Many user signals are ambiguous. Just watching a video doesn’t tell YouTube whether you liked that particular video or not, and just eating at a restaurant doesn’t tell Yelp whether you liked it or not. That’s why ratings are so important in collaborative-filtering systems. But users don’t rate every item they interact with, and many users don’t rate anything at all. Potential solution: Depending on the nature of the data, there may be proxy measures that can be used. Another common technique is to assume that missing reviews are equivalent to average reviews, though this is a very strong assumption in most cases.

>The “cold start” problem. As we’ve seen, collaborative-filtering can be a powerful way of recommending items based on user history, but what if there is no user history? This is called the “cold start” problem, and it can apply both to new items and to new users. Items with lots of history get recommended a lot, while those without never make it into the recommendation engine, resulting in a positive feedback loop. At the same time, new users have no history and thus the system doesn’t have any good recommendations. Potential solution: Onboarding processes can learn basic info to jump-start user preferences, importing social network contacts.

# RELEVANT SKILLS AND TECH
Building a recommender system with collaborative filtering is a major project that involves both data science and engineering challenges. Solving these challenges may require expertise with data processing and storage frameworks like Hadoop or Spark. When it comes to implementing algorithms, data-oriented programming languages like Python, Java, and Scala support libraries that make it easy to perform an array of machine learning and statistical analysis tasks.

