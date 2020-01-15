# hackru-f19

Inspiration
Sales price prediction challenge by Colgate. We are a bunch of Data Science Master's students always seeking data to play with. What's better than Colgate's data challenge for us to practice our skills and provide value to Colgate by estimating the price of a product based on location, brand, and ingredients of the product.

What it does
It estimates product sales prices based on location, brand, and ingredient of the product.

How we built it
Step 1: Data Preprocessing: We started by creating a vocab of ingredients. Then count vectorized the ingredient vocab.

Step 2: Exploratory Data Analysis: We performed a univariate analysis of all features. Based on this we binned brand (into 7 bins) and location (into 3) features. For the ingredient list, we limited the count of ingredients to 30 based on no of ingredient distribution for each product, as 90 percentile of the data contains less than 30 ingredients. Next, we created 30 columns for ingredients and filled it with a count of ingredient using count vectorized lookup table. Finally, we looked at the target feature price per unit whose value is below 10 for 90 percentile of the data, so we remove the outliers from the table.

The reason behind binning countries into continents was because of the reason that some same ingredients were called by different names in countries like India and China which can cause the model to consider them as two different ingredients.

Step 3: Data Visualization Performed visualization of data using Tableau. Dominating companies in each country, dominating countries for each company, average prices in each continent, all these were visualized in tableau using heatmaps.

Step 4: Model Training Using the above-generated feature set, we training the XGBoost model. We performed hyperparameter tuning to improve the algorithm's evaluation criteria ie MAE.

Step 5: Model Evaluation We used Mean Absolute Error as our evaluation criteria as its a regression problem. We brought the MAE of our model down to 1.38 using Cross-Validation for k=5 folds.

Step 6: Model Deployment We used Google's collab notebooks to work on this problem set. And we have used the same for future predictions.

Challenges we ran into
Feature space for ingredients is ~9000 words which translate into +9000 column if we take the one-hot encoded brute force approach. We faced resource constraints while training this model on the collab, so we used lasso regression to bring down the feature set and then use this feature set for further modeling using XGBoost Regressor. Still, we got far superior performance in terms of MAE and computation time using the approach mentioned above in step 2 which only has <50 features to work with.

Accomplishments that we're proud of
Our model performance, using only 50 features gave MAE = 1.38.

What we learned
It was a great challenge to work on. We learned a lot, especially how to work with 9000+ feature space.

What's next for Sales Price Prediction Model
Using multilingual word2vec models for ingredients.
