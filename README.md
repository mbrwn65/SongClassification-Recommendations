# Song Lyric Classification and Recommendation System with Natural Language Processing
### [Data Source](https://www.kaggle.com/datasets/carlosgdcj/genius-song-lyrics-with-language-information): Song data for over 5 Million songs, taken from Genius.com by CarlosGDCJ
**_______________________________________________________________________________________________________**
# Results:
## Recommendations:
<br/>
When called, generates a specified # of song recommendations for a given song & artist
- song recommendations are based on lyrical similarity, not audio similarity<br/><br/>
## Classification:
<br/>
<br/>
A basic logistic regression model resulted in the best performance out of the models that I tested, classifying Artists correctly ~16% of the time & classifying Genre correctly ~71% of the time (with the best performance on rap songs as shown above)<br/><br/>
**_______________________________________________________________________________________________________**
# Basic Methodology (after cleaning the dataset and tokenizing lyrics):
### Vector Representation of Lyrics:
<br/>
Generates word embeddings for each token in the training data using Gensim's Word2Vec trained on the tokenized lyric data<br/><br/>
<br/>
Represents the lyrics of each song as the average of the W2V embeddings for each token in the lyrics, resulting in a 100 dimension vector.<br/>
___________
### Recommendations Using Vector Representations:
<br/>
Calculates the Euclidian distance between the specified song and all other songs, then returns the top *num_reccomendations* closest songs<br/>
### Classification Using Vector Representations:
<br/>
Upsamples data to contain equal distributions among genres using Imblearn's RandomOverSampler<br/><br/>
<br/>
Using the above function, I tried multiple different classification models from scikit-learn to predict artist and genre, such as: K-Nearest Neighbors, a Multilayer Perceptron, and Logistic Regression.
As shown in the Results section, Logistic Regression performed the best for both tasks.
__________
# The Jupyter Notebook & Report included above contain more detailed information on the methodology and the results of this project.
