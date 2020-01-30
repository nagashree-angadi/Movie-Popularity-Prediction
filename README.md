# Movie-Popularity-Prediction

The purpose of the project is to build a model that predicts the contemporary popularity (p) of a movie based on parameters known at the time of release. The model will enable us to analyze the longevity of the movie from the time of its release.

## Data Collection
1. Box Office Mojo
2. Internet Movie Database ( IMDb )
3. The Movie Database ( TMDb )

## Data Cleaning and Merging
1. Inflation adjustment for Revenue and Gross.
2. Creating custom variables such as total number of awards, popularity season.
3. Imputing null values.
4. Merging features such as vote average and vote count to get more meaning full feature.
5. Merging all the datasets.

## Modelling
### Custom scoring model
The decay law is best suited for our prediction model. The initial popularity is calculated using custom scoring function. According to our objective, we selected set of features that shows the prevalence of a movie before and just after the release of the movie. These relevant features are obtained after careful exploratory data analysis.

The popularity metric of the movie M is given by,
p(M) = initial_popularity(M)* e<sup>-m</sup>

Where, m is the number of passed months from the release date to current date, initial_popularity(M) for each movie is calculated using the custom scoring function. The weights are assigned to each features based on the correlation with the current popularity. initial popularity(M) = c<sub>1</sub>*f<sub>1</sub> +c<sub>2</sub>*f<sub>2</sub> + ···+c<sub>n</sub>*f<sub>n</sub>

### Borda count model
In this model the contemporary popularity of the movie is calculated using a combination of Borda Count and Decay Law. In decay law we need to define the popularity of movie just after the release of the movie. We choose the set of features that shows the popularity of a movie before and just after the release of the movie, these are mentioned in Feature Engineering section. The contemporary popularity of movie M is defined by, p(M) = borda_count(M ) ∗ e<sup>−m</sup>

### Ensemble
 We obtained the best results by using ensemble as outlined below:
1. Split the train set into 10 parts.
2. We used two base models DecisionTreeRegressor and KNeighborsRegressor
3. The base models are fitted on the training dataset.
4. For both the base models, predictions are made on the test set. We obtain the predictions for train and test data corresponding to each of the base models.
5. We then created a third model, RandomForestRegressor, on the predictions of the decision tree and knn models.

## Analysis
Performed analysis on the following,
1. Top performing movies every decade
2. Impact of the actor’s popularity on the success of the movie.
3. Genre trend analysis over the years.
4. Impact of awards on the success of the movie.

## Conclusion
We successfully explored and analyzed the movie data over the years. We built a comprehensive dataset by scraping data from IMDb, TMDb, boxofficemojo.com and google trends. We determined the popularity metric based on the release time features which helped us analyze the longevity of the movie from the time of its release. We built the prediction model after careful data munging and deriving insights from the elaborative exploratory data analysis. We determined the contemporary popularity of the movie by the Borda Count Ranking model coupled with decay law. We validated our derived popularity score by using several machine learning algorithms.


