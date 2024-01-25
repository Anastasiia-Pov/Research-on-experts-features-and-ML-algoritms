# Research on experts features and ML-algoritms
This research is about influence of number of extracted features from audio-files and the quality of classification with the use of ML-algorithms

## Extracted features:
All the features were extracted with openSMILE: (https://www.audeering.com/research/opensmile/)
The acoustic features that were used for the experiment are the following (in commas represented the number of features): GEMAPS(62), eGEMAPS(88), Interspeech 2009(384), Interspeech 2010(1582), Interspeech 2013(6373).
Form each audiofile were extracted the number of features that correlates with the set of features. Extraction of features was performed separetly from the common code of the experiment.

All the extracted features to repeat the experimnets are represented here: (https://drive.google.com/drive/folders/1p_K0Nz_z4swBj7MWu47g6uqjG_TvwE-K?usp=sharing)

## The datasets:
The datasets that were used for the experimnent are Nonspeech7k: (https://zenodo.org/records/6967442) and Vocal Sound (https://github.com/YuanGongND/vocalsound). 
In the Nonspeech7k dataset were represented 7 classes of events: breath-1850, cough-702, cry-1996, laugh-1273, scream-663, sneeze-266, yawn-264.
In the Vocal Sound dataset were representes 6 classes: laugh-3504, sigh-3504, cough-3504, sneeze-3504, sniff-3504, throatclearing-3504.

## The pipeline of expreiments:
1) Dimensionality reduction for each dataset of features.
2) Classification with the chosen ML-algoritms: SVM (with three types of kernels(linear, rbf, sigmoid), LDA, kNN, Logistic Regression, Decision Tree, and Neural Network that was done with MLP-Classifier [sklearn] (https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPClassifier.html).

## Three sets of expreiments:
**First set of experiments:** 
was about testing how good ML-algorithms cope with the task of classification classes representd in the datasets**
Classification using Cross-Validation 5x2. Ml-algorithms that were used: 
The metrics that were observed are: Precision, Recall, Average Precision and Recall, Accuracy.
The codes for these experiments can be observed in the following files: for Nonspeech7k - "Crocc-validation for Nonspeech7k", for Vocal Sound - "Crocc-validation for Vocal Sound".

**Second set of experiments:** 
was about comparing the original results with the results that were got with the chosen ML-approaches mentioned above. The split into test-train sets was used according to the original one. But to mention, as long as Vocal Sound dataset has 3 splits: train, validation and split, there were organised two kinds of spliting: a. train-test spliting (ommiting validation set), and b. train+validation set-test (train and validation sets were joined).
The codes for these experiments can be observed in the following files: for Nonspeech7k - "SOTA for Nonspeech7k", for Vocal Sound - "SOTA for Vocal Sound".

**Third set of experimnets:**
was about cross-corpus research. These datasets have in common 3 classes: laugh, cough, sneeze. Based on these classes was completed cross-corpus research.
The code for these experiments can be observed in the following file: for Nonspeech7k - "Cross-corpus research".

## Results:
**First set of experiments:** 
1) The best results for Nonspeech7k were got with SVM-rbf and Nearal Network + Interspeech 2013 features. The results are the following:

**SVM_RBF:**
Accuracy Score = 0.854 ± 0.004   
|  Class         | Recall         | Precision     |
|----------------|----------------|---------------|
| breath/дыхание |  0.972 ± 0.004 | 0.931 ± 0.006 |
| cough/кашель   |  0.759 ± 0.016 | 0.780 ± 0.021 |
| cry/плач       |  0.884 ± 0.010 | 0.848 ± 0.017 |
| laugh/смех     |  0.815 ± 0.017 | 0.830 ± 0.021 |
| scream/крик    |  0.862 ± 0.013 | 0.766 ± 0.020 |
| sneeze/чихание |  0.487 ± 0.032 | 0.911 ± 0.030 |
| yawn/зевание   |  0.593 ± 0.043 | 0.883 ± 0.034 |
|Average Scores  |  0.767 ± 0.019 | 0.850 ± 0.021 |

       

**Neural Network:**
Accuracy Score = 0.855 ± 0.004 
|  Class          | Recall         | Precision     |
|-----------------|----------------|---------------|
| breath/дыхание  |  0.973 ± 0.002 | 0.945 ± 0.004 |
| cough/кашель    |  0.771 ± 0.025 | 0.777 ± 0.020 |
| cry/плач        |  0.876 ± 0.010 | 0.843 ± 0.017 |
| laugh/смех      |  0.813 ± 0.019 | 0.813 ± 0.017 |
| scream/крик     |  0.824 ± 0.011 | 0.842 ± 0.007 |
| sneeze/чихание  |  0.575 ± 0.038 | 0.758 ± 0.029 |
| yawn/зевание    |  0.666 ± 0.031 | 0.828 ± 0.039 |
|Average Scores   |  0.786 ± 0.019 | 0.829 ± 0.019 |

                    



