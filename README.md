# Capstone Project: Predicting the Typing Time of a Sentence

### Problem Statement

What aspects of a sentence can predict the time it takes to type it? This project will analyze whether such features the sentence's words and letters, its sentiment, and its length can be effective predictors.

### Data & Resources

The data consists of results from [The Reverse Problem of Keystroke Dynamics](https://ieee-dataport.org/documents/dataset-reverse-problem-keystroke-dynamics-guessing-typed-text-keystroke-timings), a study by Nahuel Gonzalez of the Laboratorio de Sistemas de Información Avanzados of the University of Buenos Aires. Specifically, it consists of sentences and user typing times for the PROSODY dataset, which contains three main topics: gay rights, gun rights, and restaurant reviews.

In addition, I have used other resources to help with the coding, which are linked at the relevant points in the code files.

### Repository Layout

The code folder is broken up into five parts:

1. [Cleaning & EDA](code/1. Cleaning & EDA.ipynb)
2. [Word Modeling](code/2. Word Modeling.ipynb) (using Natural Language Processing to figure out the effect of each word)
3. [Attribute Modeling](code/3. Attribute Modeling.ipynb) (examining length, topic, sentiment, and the number of function keys such as shift and backspace)
4. [Character Modeling](code/4. Attribute Modeling.ipynb) (finding the effect of each character in the dataset on typing times)
5. [Final Modeling](code/5. Final Modeling.ipynb) (creating a final model for predictions)

The data folder contains the three original datasets as .txt files (GAY-SENTENCES, GUN-SENTENCES, and REVIEW-SENTENCES). In addition, it also includes the results of code notebooks 1-4 above (respectively, they are data_cleaned, data_with_words, data_with_sentiment, and data_with_letters).

### Libraries

The libraries I used for my work include pandas, matplotlib, seaborn, sklearn, and ntlk, as well as three non-standard libraries: [wordcloud](https://amueller.github.io/word_cloud/) (for creating a word cloud for the sentence data), [enchant](http://pyenchant.github.io/pyenchant/) (which checks to make sure words are real), and [collections](https://docs.python.org/3.9/library/collections.html) (specifically for the Counter function which returns the frequency of each character in a string).

### Conclusion

The best-performing model for predicting typing time is the random forest regressor with the predictors being the 10 most impactful words, the 9 most impactful letters, the number of function keys, and the sentiment.