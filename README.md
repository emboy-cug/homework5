# MovieLens 100k Dataset Analysis and Genre-Based Recommendation

## Overview
This project applies two methodologies to analyze the MovieLens 100k dataset. The first task involves building a user-based collaborative filtering system to recommend items based on user similarity. The second task focuses on building genre-based user profiles and using cosine similarity to recommend a movie based on genre alignment.

## Problem 1: MovieLens 100k Dataset Analysis

### Methodology
- **Data Loading**: The MovieLens 100k dataset is loaded and processed using Python's `Pandas` library. The ratings data (`u.data`) is extracted into a DataFrame.
- **Utility Matrix Construction**: A user-item utility matrix is constructed using the `pivot_table` function in Pandas.
- **Centering Ratings**: To account for user biases, the ratings are centered by subtracting the mean rating of each user across all items.
- **Cosine Similarity Calculation**: Cosine similarity is calculated between users using the centered ratings.
- **Identifying Similar Users**: The top 10 most similar users to a target user (user 1) are identified based on cosine similarity.
- **Expected Rating Calculation**: The expected rating for item 508 for user 1 is computed as the average rating from the most similar users.

### Visualizations
Three plots were generated to visualize the results:
1. **Ratings for Item 508 by Top 10 Similar Users**: Shows how the top 10 similar users rated item 508.
2. **Cosine Similarities of Top 10 Users**: Visualizes the cosine similarities between user 1 and the top 10 similar users.
3. **Average Ratings of User 1 and Top 10 Similar Users**: Compares average ratings of user 1 and the top 10 similar users.

### Results
- The top 10 similar users were identified, with their cosine similarity scores ranging from 0.18 to 0.20.
- The expected rating for item 508 for user 1 was calculated to be 4.2, based on the ratings of the similar users.

### Conclusion
The analysis successfully identified the most similar users to user 1 and predicted an expected rating for item 508 using collaborative filtering. Future improvements could include incorporating movie genres and exploring more advanced techniques such as matrix factorization to handle sparsity in the data.

---

## Problem 2: Genre-Based Recommendation

### Methodology
- **Data Loading**: The ratings (`u.data`) and movie genres (`u.item`) were loaded into Pandas DataFrames.
- **Utility Matrix**: A user-item matrix is created from the ratings data.
- **Centering Ratings**: The ratings are centered by subtracting the mean of each user's ratings.
- **User Profiles**: 19-dimensional profile vectors were constructed for users 200 and 15, where each genre is weighted based on user preferences.
- **Movie 95 Vector**: A binary genre vector was extracted for movie 95, indicating whether the movie belongs to each of the 19 genres.
- **Cosine Similarity and Distance**: Cosine similarity and distance are calculated to compare users' genre preferences with movie 95's genre vector.
- **Recommendation**: Movie 95 is recommended to the user with the higher cosine similarity to the movie's genre profile.

### Visualizations
Three visualizations were generated:
1. **Cosine Metrics Bar Plot**: Displays cosine similarities and distances between users 200 and 15 with movie 95.
2. **User Profiles Bar Plot**: Compares genre preferences for users 200 and 15.
3. **Profiles vs. Movie 95 Line Plot**: Shows the genre alignment between user profiles and movie 95.

### Results
- **User 200**: Profile dominated by Sci-Fi (0.5126) and Action (0.4717), with negative preferences for Comedy and Children’s genres.
- **User 15**: Profile dominated by Drama (0.5394) and Romance (0.5079), with negative preferences for Children’s and Comedy genres.
- **Movie 95**: Has genres including Animation, Children’s, Comedy, and Musical.
- Based on cosine similarity, movie 95 was recommended to user 200, with a similarity of -0.2652, which was higher than user 15's -0.3259.

### Conclusion
The analysis successfully constructed genre-based user profiles and computed cosine similarities to recommend a movie to the user with the higher similarity. The recommendation was made to user 200 based on their relatively higher similarity to movie 95. Future improvements could explore advanced methods such as weighted genre vectors or matrix factorization.

