# MOVIE RECOMMENDATION SYSTEM

## OVERVIEW

Subject: Create a recommender system using specific datasets that predicts movies both of two users will enjoy.

For my project, I explored three different methods to develop a movie recommendation system. The aim was to predict movies that both selected users would likely appreciate. Initially, I attempted to implement a Random Forest model that utilized various user and movie features, including genres. However, due to extended training times and limited effectiveness in recommendation tasks, I abandoned this approach midway. Instead, I focused on two primary methods that rely solely on user ratings to predict movie preferences. One approach employs embeddings to represent users and movies, which simplifies learning patterns and enhances predictive accuracy. The other method utilizes a traditional neural network architecture, which showed slightly less promising results during testing. 

## Preprocessing Steps:

1. Initial Examination of Datasets:

Initially, I reviewed the contents of five datasets: Movie ratings, Movie details, IMDb titles, User details, and IMDb names (which was ultimately not used).

2. Column Removal:

Removed columns from the datasets that were deemed unnecessary or irrelevant to the recommender system.

3. Column Type Checking and Title Reformatting:

Checked the data types of columns across all datasets and standardized movie titles across different datasets to facilitate merging.

4. Merging Datasets:

Merged relevant columns from Movie ratings, Movie details, IMDb titles, and User details datasets. Special attention was given to properly fuse genre information across these datasets.

5. Final process

After giving up RandomForest, I relized I only needed UserID, ratings and MovieID so I created a copy of my main dataframe that I preprocessed so it could be used easily by neural networks.

## Experimentaion

### Models

1. RandomForest

Given up

2. Embeding


The Embedding method was chosen for its effectiveness in capturing latent factors and relationships between users and movies based on their interactions. It is a good choice for recommendation systems.

3. Dense Neural Network

A Dense Neural Network (DNN) was employed to explore a more traditional approach to recommendation systems. I mostly did it out of interest and desire to compare with the first method.

### Algorithm

1. Retrieve Movies Watched:

Filters copy_df to find all movies watched by both user_id_1 and user_id_2.

2. Identify Movies Not Watched:

Creates a list of movies that neither user has watched by comparing all movie IDs with those watched by either user.

3. Encode Users:

Maps user_id_1 and user_id_2 to their respective encoded representations (user_encoder_1 and user_encoder_2) using user2user_encoded.

4. Create User-Movie Interaction Arrays:

Constructs arrays (user_movie_array_1 and user_movie_array_2) where each row corresponds to a movie not watched by the respective user, paired with the user's encoded ID.

5. Compute Predicted Ratings: 

Compute predicted ratings for each user-movie pair using the trained model. This is done for both the users.

6. Average Ratings:

Computes the average predicted rating for each movie by averaging the predictions for user_id_1 and user_id_2.

7. Recommend Top Movies:

Identifies the top 10 movie recommendations based on the highest average ratings.

8. Display Recommendations:

Retrieves the title and genre information for the top recommended movie using get_movie_title_and_genres.
Prints the recommended movie title and it's genre.

9. Return Recommendations:

Returns a list (recommended_movie_ids) of the top recommended movie IDs so that I can analyse better what my algorithm recommended and check if it is consistent.

## Choices

I opted for methods like SVD and user-item interaction matrices as they usually good for recommendation systems and result in better recommendations. RandomForest, while versatile, was set aside due to its limitations in capturing nuanced user preferences and the complexity it introduced during implementation.

## Results

Both models have an accuracy of around 0.23. For the embeding method, the results are coherent and seem good. For exemple, the genre seem to match more often than not what the 2 users liked. For the DNN however, it seems that the answers it gives are not that similar to the 2 users preference.
However, these result where seen when testing for only 10-15 different user combination.A better benchmark would be needed to test the difference in performance.

## Conclusion

In conclusion, the Embedding method has proven to be highly effective for our movie recommendation system. It successfully captures complex patterns and latent factors in user-movie interactions, resulting in recommendations that align closely with users preferences. On the other hand, while the Dense Neural Network (DNN) approach was informative to explore, its recommendations seem to be slightly worse and it takes more time to train, indicating its limitations in this context. Moving forward, focusing on further optimizing the Embedding method could enhance the system's performance and provide even more accurate and personalized movie recommendations.