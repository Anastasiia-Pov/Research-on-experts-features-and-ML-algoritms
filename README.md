# Research on experts features and ML-algoritms
This research is about influence of number of extracted features from audio-files and the quality of classification with the use of ML-algorithms

## Extracted features:
All the features were extracted with openSMILE: (https://www.audeering.com/research/opensmile/)
The acoustic features that were used for the experiment are the following (in commas represented the number of features): GEMAPS(62), eGEMAPS(88), Interspeech 2009(384), Interspeech 2010(1582), Interspeech 2013(6373).
Form each audiofile were extracted the number of features that correlates with the set of features. Extraction of features was performed separetly from the common code of the experiment.
----
## The dataset:
The dataset that was used for the experimnent is Nonspeech7k: (https://zenodo.org/records/6967442). 
In the dataset were represented 7 classes of events: breath-1850, cough-702, cry-1996, laugh-1273, scream-663, sneeze-266, yawn-264.
----
## The pipeline of expreiment:
1) Extraction of features.
2) Dimensionality reduction for each dataset of features.
3) Classification using Cross-Validation 5x2. Ml-algorithms that were used: SVM (with three types of kernels(linear, rbf, sigmoid), LDA, kNN, Logistic Regression, Decision Tree, and Neural Network that was done with MLP-Classifier [sklearn] (https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPClassifier.html).
4) The metrics that were observed are: Precision, Recall, Average Precision and Recall, Accuracy.
