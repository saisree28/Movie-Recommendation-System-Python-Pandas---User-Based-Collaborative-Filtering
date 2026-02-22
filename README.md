# Movie-Recommendation-System-(Python,Pandas) -User-Based-Collaborative-Filtering


The project is based on Collaborative Filtering, specifically a User-Based Collaborative Filtering approach combined with a Search Engine built using NLP techniques.

The project is structured around two main logical components:

1. Movie Search Engine (Content Search)
Before recommending movies, the system needs to find the specific movie you are talking about.

Concept: TF-IDF (Term Frequency-Inverse Document Frequency) and Cosine Similarity.

How it works: It cleans the movie titles (using Regex) and converts them into a matrix of numbers using TfidfVectorizer. When you type a movie name, it calculates the "distance" (Cosine Similarity) between your search term and the titles in the database to find the closest match.

2. Recommendation Engine (Collaborative Filtering)
Once a movie is selected, the system finds recommendations based on user behavior rather than just movie genres.

Concept: User-Item Interaction.

The Logic:

Find similar users: It identifies users who watched the movie you searched for and gave it a high rating (e.g., > 4 stars).

Find their other favorites: It looks at all other movies those "similar users" also liked.

Filter by Popularity: It identifies movies that are frequently liked by these similar users but less frequently liked by the general population. This "score" ensures you get recommendations that are specifically relevant to that movie's fans, rather than just globally popular movies like The Avengers.

Summary of Tools Used:
Pandas: For data manipulation and reading the MovieLens 25M dataset.

Scikit-learn: For the TfidfVectorizer and cosine_similarity functions.

Ipywidgets: To create the interactive search and recommendation box directly inside the Jupyter Notebook.
