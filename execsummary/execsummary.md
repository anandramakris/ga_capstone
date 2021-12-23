## Problem Statement

What aspects of a sentence can predict the time it takes to type it? This project will analyze whether such features the sentence's words and letters, its sentiment, and its length can be effective predictors.

## Goal

The goal for the project was to build a regressor model, using one or more aspects of a sentence, to accurately predict the time it takes to type the sentence.

Accuracy, using the score() function, was the statistic by which success was measured.

## Data

The data consists of sentences and typing times from [The Reverse Problem of Keystroke Dynamics](https://ieee-dataport.org/documents/dataset-reverse-problem-keystroke-dynamics-guessing-typed-text-keystroke-timings), a study by Nahuel Gonzalez of the Laboratorio de Sistemas de Información Avanzados of the University of Buenos Aires, specifically those from the PROSODY dataset.

## Process

In each of the four main steps, after doing a train-test split, I fit four models on the training data and scored them on both the training and test data.

The first three steps involved three different sets of predictors: words for the first step, attributes (length, topic, sentiment, and number of function keys) for the second step, and characters for the third step. In the final step, I chose the most important features from the previous models and made them the predictors for the final model.

## Results

The final model chosen was a random forest regressor with 21 predictors:
1. The 10 words with the highest coefficients for linear regression: 'thethe', 'tha', 'health', 'consenting', 'sandy', 'wouldn', 'hte', 'fof’, 'considering’, and 'walked’
2. The 9 letters with the highest feature importances in the character random forest regression model: 'E', 'I', 'T', 'R', 'O', 'A', 'S', 'N’, and ‘L’
3. The number of function keys used while typing each sentence
4. The sentiment of each sentence

Though the final model was slightly overfit, it had high accuracy for both the training and test sets (97.9% and 86.2% respectively).

The letter E had a much higher impurity-based feature importance than any other predictor in my final model, indicating that it had the highest effect on typing time.

## Recommendations for Further Study

Possible reasons for the dominance of the letter E are that E is such a common letter in the English language and that it is not in the center row of the QWERTY keyboard, so typists must do a little reaching to press the key. Further research should include a survey detailing the subjects' opinions on typing the letter E compared to and adjacent to others.

There are a few limitations to this project:
1. Since the data never had consecutive [BACK] instances, it is impossible to tell how many letters were deleted upon using backspaces, so my cleaned data might not be accurate.
2. The sentiment analyzer could not assign a score to misspelled words.

In future studies on this topic, I would like to have every instance of a function key recorded, especially since the number of function keys is the second-most important predictor in my model.

I also wish to compare the typed sentences to the sentences that the subjects were supposed to be typing to note the difference in sentiment scores.