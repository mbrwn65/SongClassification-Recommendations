# Song Lyric Classification and Recommendation System with Natural Language Processing
### [Data Source](https://www.kaggle.com/datasets/carlosgdcj/genius-song-lyrics-with-language-information): Song data for over 5 Million songs, taken from Genius.com by CarlosGDCJ
**_______________________________________________________________________________________________________**
# Results:
## Recommendations:
<br/>
When called, generates a specified # of song recommendations for a given song & artist
- song recommendations are based on lyrical similarity, not audio similarity<br/><br/>
## Classification:
<img width="768" alt="Screenshot 2024-05-14 at 5 37 18 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/75655c5c-65d3-4247-92e3-bfe0f61accff"><br/>
<img width="460" alt="Screenshot 2024-05-14 at 5 34 55 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/212fb93c-b256-4c7a-92a9-b11941d53c48"><br/>
A basic logistic regression model resulted in the best performance out of the models that I tested, classifying Artists correctly ~16% of the time & classifying Genre correctly ~71% of the time (with the best performance on rap songs as shown above)<br/><br/>
**_______________________________________________________________________________________________________**
# Basic Methodology (after cleaning the dataset and tokenizing lyrics):
### Vector Representation of Lyrics:
<img width="512" alt="Screenshot 2024-05-14 at 5 44 52 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/517da891-0f2a-46fe-818f-faa9a30c7285"><br/>
Generates word embeddings for each token in the training data using Gensim's Word2Vec trained on the tokenized lyric data<br/><br/>
<img width="735" alt="Screenshot 2024-05-14 at 5 53 40 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/bd65b85e-dfe1-4941-a28f-3dcdc7564cd2"><br/>
Represents the lyrics of each song as the average of the W2V embeddings for each token in the lyrics, resulting in a 100 dimension vector.<br/>
___________
### Recommendations Using Vector Representations:
<img width="1037" alt="Screenshot 2024-05-14 at 5 09 43 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/7f12b64e-f2ca-4d03-bec3-ddd007789327"><br/>
Calculates the Euclidian distance between the specified song and all other songs, then returns the top *num_reccomendations* closest songs<br/>
### Classification Using Vector Representations:
<img width="741" alt="Screenshot 2024-05-14 at 6 12 25 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/b439e1d8-ff87-4317-8527-65bfd5c95b24"><br/>
Upsamples data to contain equal distributions among genres using Imblearn's RandomOverSampler<br/><br/>
<img width="916" alt="Screenshot 2024-05-14 at 6 17 17 PM" src="https://github.com/mbrwn65/SongClassification-Recommendations/assets/117549863/466d2d7b-20d9-4b2f-86ef-b3e7fab6e411"><br/>
Using the above function, I tried multiple different classification models from scikit-learn to predict artist and genre, such as: K-Nearest Neighbors, a Multilayer Perceptron, and Logistic Regression.
As shown in the Results section, Logistic Regression performed the best for both tasks.
__________
# The Jupyter Notebook & Report included above contain more detailed information on the methodology and the results of this project.
