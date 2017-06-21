--- 
 
# required metadata 
title: "Machine Learning Sentiment Analyzer Transform" 
description: "Scores natual language text and creates a column that" 
keywords: "transform text sentiment nlp" 
author: "Microsoft Corporation Microsoft Technical Support" 
manager: "" 
ms.date: "06/21/2017" 
ms.topic: "reference" 
ms.prod: "microsoft-r" 
ms.service: "" 
ms.assetid: "" 
 
# optional metadata 
ROBOTS: "" 
audience: "" 
ms.devlang: "" 
ms.reviewer: "" 
ms.suite: "" 
ms.tgt_pltfrm: "" 
ms.technology: "r-server" 
ms.custom: "" 
 
---

# get_sentiment

microsoftml.modules.text_analytics.get_sentiment(cols: dict, **kargs)



## Description

Scores natual language text and creates a column that
contains probabilities that the sentiments in the text are positive.


## Details

The ``get_sentiment`` transform returns the probability
that the sentiment of a natural text is positive. Currently supports
only the English language.


## Parameters


### vars

A character vector or list of variable names to transform. If
named, the names represent the names of new variables to be created.


### kargs

Additional arguments sent to compute engine.


## Returns

A ``maml`` object defining the transform.


## Author

Microsoft Corporation [Microsoft Technical Support](https://go.microsoft.com/fwlink/?LinkID=698556&clcid=0x409)


## See also

[``rx_fast_trees``](rx_fast_trees#microsoftml.modules.fast_trees.rx_fast_trees),
``rx_fast_forest()``,
``rx_neural_net()``,
``rx_one_class_svm()``,
[``rx_logistic_regression``](rx_logistic_regression#microsoftml.modules.logistic_regression.rx_logistic_regression),
``rx_fast_linear()``.


## Example



```
# Create the data
CustomerReviews <- data.frame(Review = c(
  "I really did not like the taste of it",
  "It was surprisingly quite good!",
  "I will never ever ever go to that place again!!"),
  stringsAsFactors = FALSE)

# Get the sentiment scores
sentimentScores <- rxFeaturize(data = CustomerReviews, 
                               mlTransforms = getSentiment(vars = list(SentimentScore = "Review")))

# Let's translate the score to something more meaningful
sentimentScores$PredictedRating <- ifelse(sentimentScores$SentimentScore > 0.6, 
                                          "AWESOMENESS", "BLAH")

# Let's look at the results
sentimentScores
```
