# Movie-Recommendation-System-(Python,Pandas) -User-Based-Collaborative-Filtering

The Dataquest movie recommendation project is built on two primary technical concepts: Natural Language Processing (NLP) for searching and User-Based Collaborative Filtering for generating recommendations.

***1. Data Architecture***:  

The project uses the MovieLens 25M dataset, which is structured into two primary tables:
  •	Movies Metadata: (movieId, title, genres) - Used for the search engine.
  •	Ratings Data: (userId, movieId, rating, timestamp) - Used for the recommendation engine.  
  

  

***2. Search Engine: TF-IDF & Vector Space Modeling***:  

The search engine is the "Entry Point." It uses a technique called Vectorization to understand text.
The Math behind the Search
The system builds a TF-IDF Matrix ($Term Frequency \times Inverse Document Frequency$).
 •	Term Frequency ($TF$): Counts how many times a word appears in a title.
 •	Inverse Document Frequency ($IDF$): Decreases the weight of words that appear too frequently (like "The", "Man", "Movie") and increases the weight of unique words (like "Interstellar").

Similarity Metric
When a user types a query, it is converted into a vector. The system then calculates the Cosine Similarity between the query vector ($A$) and every movie title vector ($B$):

$$\text{similarity} = \cos(\theta) = \frac{\mathbf{A} \cdot \mathbf{B}}{\|\mathbf{A}\| \|\mathbf{B}\|}$$

This measures the cosine of the angle between two vectors. An angle of $0^\circ$ ($\cos = 1$) means the titles are identical.  




***3. Recommendation Logic: Collaborative Filtering*** :  

Once a movie is selected, the system switches from "text analysis" to User-Based Collaborative Filtering.
Phase A: Finding Similar Users
The engine filters the 25 million ratings to find users who:
 1.	Rated the input movie.
 2.	Gave it a score of $> 4$ stars.
This creates a subset of "Tastemakers" who like exactly what you like.
Phase B: The Recommendation Scoring Algorithm
This is the most critical part of the code. The system calculates a Score to rank potential recommendations:
 1.	Overlap Percentage: What percentage of "Tastemakers" liked Movie X?
 2.	Global Percentage: What percentage of all users in the entire 25M dataset liked Movie X?
 3.	The Ratio (Relative Popularity): 

      Score = (SimilarUsersLikeX%) / (GeneralUsersLikeX%)

    

***4. UI Implementation: The Observer Pattern***:  

The project uses ipywidgets to create a reactive loop:
 1.	Input Widget: A text box that monitors "on_type" events.
 2.	Observer Function: Every time the text changes, it triggers a Python function.
 3.	Display Engine: Uses IPython.display to clear the previous output and render a new HTML table of the top 10 movies.
    

    

***5. Technical Stack Summary***:  

  •	Pandas: Vectorized operations on 25M rows.  
 
  •	Scikit-Learn: Tfidf Vectorizer for text processing.  
 
  •	NumPy: np.argpartition for high-speed sorting of recommendation scores.
 
  •	Regex: String cleaning to prevent search misses due to punctuation.







