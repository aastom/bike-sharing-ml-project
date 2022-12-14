# Report: Predict Bike Sharing Demand with AutoGluon Solution

#### Astom Ahashie

## Initial Training

### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?

I had to check for any negative numbers and replace them with zeros.
This is because Kaggle would reject the submission if the values were negative.
In my case there wer two negative numbers which were subtituted with zeros.

### What was the top ranked model that performed?

The top ranked model was WeightedEnsemble_L3, which has a fit_order of 20.

## Exploratory data analysis and feature creation

### What did the exploratory analysis find and how did you add additional features?

It was observed that the `season` and `weather` features were categorical features and not integers.

I decomposed the datetime field into `year`, `month`, `day`, `hour`, `minute`, `second`, creating them as separate columns.
I also converted the `season` and `weather` features into categories.

### How much better did your model preform after adding additional features and why do you think that is?

The model outperformed the initial model by 57.8%, from 1.76895 to 0.74636.
This is because the new features empower AutoGluon to increase the number of algorithms which are used to train the model.

## Hyper parameter tuning

### How much better did your model preform after trying different hyper parameters?

The model outperformed the new features-only model by 35.4% and the initial model by 72.7%.
The hyper parameter tuning model received a score of 0.48232, the new features model received a score of 0.74636, and the initial model received a score of 1.76895.

### If you were given more time with this dataset, where do you think you would spend more time?

I would spend more time hyper parameter tuning, experimenting with different eval metrics, time_limit, num_trials and the others.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.

| model        | num_bag_folds | num_bag_sets | num_stack_levels | score   |
| ------------ | ------------- | ------------ | ---------------- | ------- |
| initial      | 0             | 1            | 0                | 1.76895 |
| add_features | 0             | 1            | 0                | 0.74636 |
| hpo          | 5             | 1            | 1                | 0.48232 |

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score.png](img/model_test_score.png)

## Summary

This project shows that feature engineering and hyperparameter tuning can improves the performance of the model dramatically.
