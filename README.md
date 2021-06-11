# Building a recommendation engine: NMF-Cosine Movie Recommender

We develop a hybrid algorithm to generate recommendations that combines: 

* the collaborative filtering approach of NMF (non-negative matrix factorization): recommends items that are similar to those that that a
user rated highly. This provides logical recommendations but is unlikely to expose a user to new
items outside their preferences that they might also enjoy.
* the content filtering approach of cosine similarity: makes
recommendations based on a matrix of user-item ratings, without regard for any other information
about the items or users themselves. This approach has the advantage of exposing a user to new
content they may like, but the recommendations it makes may be surprising.

The algorithm is used to make movie recommendations based on information about the movies and the available user ratings from the movies and the available user ratings. 

The main dependencies are scikit-learn (for cosine similarity) and surprise (for NMF). Initially, the scikit-learn decomposition module’s implementation of NMF was
used, but it required that missing ratings be filled in with a numerical value.
Replacing missing values with a numeric value has a high impact on the model’s
predictions; early tests showed that populating missing values with zero resulted in
predictions close to zero. Clearly, this is unacceptable in a recommendation algorithm.
As a result, we used the Surprise package which is designed for recommendation
algorithms and which calculates the decomposition matrices without any assumptions
about the missing values.
