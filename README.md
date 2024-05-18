# Song Lyric Classification and Recommendation System with Natural Language Processing
### [Data Source](https://www.kaggle.com/datasets/carlosgdcj/genius-song-lyrics-with-language-information): Song data for over 5 Million songs, taken from Genius.com by CarlosGDCJ
**__________________________________________________________________________________________________________________**
# Results:
## Recommendations:
<img width="524" alt="Screenshot 2024-05-18 at 3 33 43 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/7f985e7a-de14-46e5-85b6-5107fc13c480"><br/>

When called, generates a specified # of song recommendations for a given song & artist
- song recommendations are based on lyrical similarity, not audio similarity<br/><br/>
## Classification:
<img width="860" alt="Screenshot 2024-05-18 at 3 34 26 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/d40e7d39-8813-4c1b-908d-4f62aaceeb1d">
<img width="475" alt="Screenshot 2024-05-18 at 3 34 52 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/ecf0214a-ef8b-41b2-bc29-4ecc3d15922b">

A basic logistic regression model resulted in the best performance out of the models that I tested, classifying Artists correctly ~16% of the time & classifying Genre correctly ~71% of the time (with the best performance on rap songs as shown above)<br/><br/>
**__________________________________________________________________________________________________________________**
# Basic Methodology (after cleaning the dataset and tokenizing lyrics):
### Vector Representation of Lyrics:
<img width="598" alt="Screenshot 2024-05-18 at 3 35 30 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/0db7918b-69e4-44b5-87d6-661c4bbab79a">

Generates word embeddings for each token in the training data using Gensim's Word2Vec trained on the tokenized lyric data<br/><br/>
<img width="1144" alt="Screenshot 2024-05-18 at 3 35 41 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/fc8092d4-df9f-434a-b961-aa70c25893d8">

Represents the lyrics of each song as the average of the W2V embeddings for each token in the lyrics, resulting in a 100 dimension vector.<br/>
___________
### Recommendations Using Vector Representations:
<img width="1136" alt="Screenshot 2024-05-18 at 3 36 00 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/dec791ed-d7af-4f23-8fb6-dcb8c4e06f7b">

Calculates the Euclidian distance between the specified song and all other songs, then returns the top *num_reccomendations* closest songs<br/>
### Classification Using Vector Representations:
<img width="870" alt="Screenshot 2024-05-18 at 3 36 15 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/d6277b22-25df-456f-9ed1-f143cb83d9af">

Upsamples data to contain equal distributions among genres using Imblearn's RandomOverSampler<br/><br/>
<br/>
<img width="942" alt="Screenshot 2024-05-18 at 3 36 38 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/30486d02-a2c2-4be3-be5f-f5884ecbf968">

Using the above function, I tried multiple different classification models from scikit-learn to predict artist and genre, such as: K-Nearest Neighbors, a Multilayer Perceptron, and Logistic Regression.
As shown in the Results section, Logistic Regression performed the best for both tasks.
__________
# The Jupyter Notebook & Report included above contain more detailed information on the methodology and the results of this project.
