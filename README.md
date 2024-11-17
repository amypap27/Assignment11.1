# Assignment11.1
This is CBMLAI assignment 11.1 Practical Application 2

[Link to Jupyter Notebook](/prompt_II.ipynb)


Summary of Findings
The goal of this project was to develop a machine-learning model that would effectively predict the used car price
given a set of features as input.

In the first part of the project, I explored the vehicles dataset. After running some statistics on the columns
and using a variety of visualizations, including box plots, histograms, scatterplots, and heatmaps, I felt like
I understood the dataset a bit better and was ready to make some decisions in preparation for building the models.

I eliminated columns such as ID and VIN that had no relationship to price.  I also eliminated some rows that seemed to have
corrupt data with unreasonably large prices or odometer readings, as well as rows with zero prices.  I noticed that most of the 
data columns were categorical and eliminated columns where either there were a large number of categories, or columns where almost
all of the rows had the same value.  I also eliminated data with null values.

I then used one-hot encoding for the remaining categorical features and then added polynomial features for degree 2 and
scaled the data in preparation for creating the models.  

I initially created Linear Regression, Ridge Regression and Lasso models with just the original degree 1 data.  However, I discovered
that the Linear Regression and Ridge Regression models had much better R2 scores when I added the polynomial degree 2 data.  I was 
not able to do this with the Lasso model, however, as it had convergence errors with all of the additional features.  This was definitely a limitation that led to the Lasso model having less predictive value than the other models.

Overall of the models that I used, the Linear Regression Model had the highest R2 score. After tuning the Ridge Regression model using GridSearchCV, it's alpha was lowered and it performed better. However, with the alpha of 0.01, this model behaved more similarly to the Linear Regression model than it did when it had a higher alpha hyperparameter.

Examining the coefficients in the Lasso model (which is a bit simpler given that they are just degree 1 columns) suggests that some of the factors that contribute to a higher used car price are: • lower odometer readings, • more recent year, • better condition, • higher number of cylinders In addition, certain car types, such as coupes, convertibles, pickups and trucks also tend to predict a higher price than other car types

However, none of the models I was able to build did a great job predicting price.  This suggests that the next steps might be finding either cleaner data or perhaps data with additional features. In particular, the dataset I used had very few numeric fields.  Given the importance for numeric data in regression models, perhaps using a dataset with more numeric fields could improve these models. Or perhaps other models types might be more effective for predicting used car price.
