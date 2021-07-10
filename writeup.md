# Verve Group data science case study

**Submission by Vinitha Venugopal Savithri**

------------

> Imagine that you were asked to use this dataset to build a classification model, with gender as the target. Look at the information we have given you and identify 3-5 potential problems you can see with the provided dataset that might make building a classification model difficult.1. Imagine that you were asked to use this dataset to build a classification model, with gender as the target. Look at the information we have given you and identify 3-5 potential problems you can see with the provided dataset that might make building a classification model difficult.

1. device_name could be a strong indicator since name often reveals gender but only about 41% of the events have this information. Additionaly, it's possible that the user of the app is not the owner of the device, in which case the device_name is a poor indicator.
2. The top 4 most frequent values of app_category are News, Weather, Health and Dating. These App categories are not good predictors of gender as they are quite generic. However, they make up about 94% of the total data. Also we don't have information about the App category for nearly 2% of the events. The rest of the App categories namely Automotive, Sports, Fashion, Arts and crafts and Desserts and baking might be good predictors of gender based on traditional gender-assigned roles. However since they contain only about 4% of the total data, we can't build a good model due to lack of data.
3. There are some App categories which can clearly indicate the gender like Women's Health apps or Men's Health apps. The lack of these fine-grained category values diminishes the potential of this feature.
4. ad_category could have been of great value since the categories are quite granular and can indicate gender of the user. However, 99.5% of the data does not reveal anything significant as there is a high probability that the user might reject the ad despite it being gender-appropriate. Also since the remaining 18 events with Yes for click value are too few as compared to the total number of Ad categories (around 14), it is difficult to reveal any correlation of gender with ad_category.
5. The information about the interaction_with_app feature doesn't reveal anything about the gender as it depends on an individual and not their gender. However, in combination with the app_category, there might be more information hidden in this feature.


> Describe briefly how you would find the features that are likely to be the most important for your model.

1. Since the name of a person is a good indicator of gender, device_name can be considered as a good candidate for an important feature. However, to use this feature, it needs to be pre-processed. The names, if feasible, should be mapped to labels indicating the gender. This feature alone can cause overfitting. Hence we should also factor in other features.
2. It would be worth checking if  gender has a correlation with a combination of the features app_category and interaction_with_app. If yes, this could also be used as a good feature.
3. Though the individual features click and ad_category might not reveal gender, a combination of click and ad_category for the cases where the value of click is Yes, can be used as a good feature. In the specific summary, there's too little data from this combination but if there's more data, this can be very useful.

> Identify which model you would try first, and at least one advantage and disadvantage of this choice.Identify which model you would try first, and at least one advantage and disadvantage of this choice.

I would use Logistic regression because it is well suited for binary classification problems.
The following are the advantages:
1. It's easy to implement, especially with the scikit-learn package and is faster to train, compared to other models like Neural networks.
2. It's very easy to interpret since the trained weights tell us the importance of each feature, unlike Random forests and Neural networks.
3. The model can be easily updated to fit new data received after the initial training without affecting the model stability, unlike Decision trees.

The disadvantages are:
1. If the model is trained on little data with a large number of features, the model can overfit. This can be overcome to some extent by using regularization.
2. Since the decision boundary of Logistic regression is linear, the problem cannot be solved accurately if the problem is not linear.
3. Since the algorithm is sensitive to outliers, the correctness of the data should be guaranteed before using the algorithm.
