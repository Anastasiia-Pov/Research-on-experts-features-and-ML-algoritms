# Research on experts features and ML-algoritms
This research is about influence of number of extracted features from audio-files and the quality of classification with the use of ML-algorithms

## Extracted features:
All the features were extracted with openSMILE: [openSMILE] (https://www.audeering.com/research/opensmile/)
The acoustic features that were used for the experiment are the following (in commas represented the number of features): GEMAPS(62), eGEMAPS(88), Interspeech 2009(384), Interspeech 2010(1582), Interspeech 2013(6373).
Form each audiofile were extracted the number of features that correlates with the set of features. Extraction of features was performed separetly from the common code of the experiment.

All the extracted features to repeat the experimnets are represented here: https://drive.google.com/drive/folders/1p_K0Nz_z4swBj7MWu47g6uqjG_TvwE-K?usp=sharing.

## The datasets:
The datasets that were used for the experimnent are Nonspeech7k: [zenodo] (https://zenodo.org/records/6967442) and Vocal Sound [github] (https://github.com/YuanGongND/vocalsound). 
In the Nonspeech7k dataset were represented 7 classes of events: breath-1850, cough-702, cry-1996, laugh-1273, scream-663, sneeze-266, yawn-264.
In the Vocal Sound dataset were representes 6 classes: laugh-3504, sigh-3504, cough-3504, sneeze-3504, sniff-3504, throatclearing-3504.

## The pipeline of expreiments:
1) Extraction of features.
2) Dimensionality reduction for each dataset of features (with PCA).
3) Classification with the chosen ML-algoritms: SVM (with three types of kernels(linear, rbf, sigmoid), LDA, kNN, Logistic Regression, Decision Tree, and Neural Network that was done with MLP-Classifier [sklearn] (https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPClassifier.html).

## Three sets of expreiments:
**First set of experiments:** 
was about testing how good ML-algorithms cope with the task of classification classes representd in the datasets**
Classification using Cross-Validation 5x2 with the count of confidence interval.
The metrics that were observed are: Precision, Recall, Average Precision and Recall, Accuracy.
The codes for these experiments can be observed in the following files: for Nonspeech7k - "Cross-validation for Nonspeech7k", for Vocal Sound - "Cross-validation for Vocal Sound".

**Second set of experiments:** 
was about comparing the original results with the results that were got with the chosen ML-approaches mentioned above. The split into test-train sets was used according to the original one. But to mention, as long as Vocal Sound dataset has 3 splits: train, validation and split, there were organised two kinds of spliting: a. train-test spliting (ommiting validation set), and b. train+validation set-test (train and validation sets were joined).
The codes for these experiments can be observed in the following files: for Nonspeech7k - "comparing with SOTA for Nonspeech7k", for Vocal Sound - "comparing with SOTA for Vocal Sound".
The metrics that were observed are: F1 for each class, Average Weighted Precision, Average Weighted Recall, Average Weighted F1, Accuracy.

**Third set of experiments:**
was about cross-corpus research. These datasets have in common 3 classes: laugh, cough, sneeze. Based on these classes was completed cross-corpus research. There were tested two options: 
a) Nonspeech for train set, Vocal Sound for test set; 
b) Vocal Sound for train, Nonspeech for test set.
The code for these experiments can be observed in the following file: for Nonspeech7k - "Cross-corpus research".
The metrics that were observed are: Precision, Recall, Average Precision and Recall, Accuracy.

## Results:
**1. First set of experiments:** 
1.1) The best results for Nonspeech7k were got with SVM-rbf and Nearal Network + Interspeech 2010 features. The results are the following:

**SVM-rbf:**
Accuracy Score = 0.860 ± 0.004  
|  Class         | Recall         | Precision     |
|----------------|----------------|---------------|
| breath/дыхание |  0.969 ± 0.004 | 0.944 ± 0.003 |
| cough/кашель   |  0.801 ± 0.018 | 0.788 ± 0.014 |
| cry/плач       |  0.891 ± 0.006 | 0.862 ± 0.017 |
| laugh/смех     |  0.822 ± 0.019 | 0.819 ± 0.014 |
| scream/крик    |  0.858 ± 0.007 | 0.765 ± 0.015 |
| sneeze/чихание |  0.424 ± 0.033 | 0.871 ± 0.017 |
| yawn/зевание   |  0.639 ± 0.028 | 0.901 ± 0.027 |
|Average Scores  |  0.772 ± 0.016 | 0.850 ± 0.015 |

**Neural Network:**
Accuracy Score = 0.855 ± 0.004
|  Class          | Recall         | Precision     |
|-----------------|----------------|---------------|
| breath/дыхание  |  0.962 ± 0.002 | 0.949 ± 0.004 |
| cough/кашель    |  0.793 ± 0.016 | 0.797 ± 0.014 |
| cry/плач        |  0.875 ± 0.007 | 0.861 ± 0.010 |
| laugh/смех      |  0.802 ± 0.014 | 0.800 ± 0.014 |
| scream/крик     |  0.827 ± 0.013 | 0.826 ± 0.016 |
| sneeze/чихание  |  0.575 ± 0.038 | 0.758 ± 0.029 |
| yawn/зевание    |  0.604 ± 0.028 | 0.698 ± 0.030 |
|Average Scores   |  0.708 ± 0.037 | 0.776 ± 0.024 |

1.2) The best results for Vocal Sound were got with LDA and Nearal Network + Interspeech 2013 features. The results are the following:

**LDA:**
Accuracy Score = 0.879 ± 0.002  
|  Class                    | Recall         | Precision     |
|---------------------------|----------------|---------------|
| cough/кашель              |  0.851 ± 0.006 | 0.840 ± 0.005 |
| laugh/смех                |  0.912 ± 0.006 | 0.920 ± 0.005 |
| sigh/вздох                |  0.900 ± 0.007 | 0.918 ± 0.005 |
| laugh/смех                |  0.875 ± 0.006 | 0.876 ± 0.007 |
| sniff/вдыхание носом      |  0.915 ± 0.005 | 0.911 ± 0.004 |
| throatcl./прочищение горла|  0.822 ± 0.007 | 0.813 ± 0.005 |
|Average Scores             |  0.754 ± 0.005 | 0.754 ± 0.004 |

**Neural Network:**
Accuracy Score = 0.872 ± 0.001 
|  Class                    | Recall         | Precision     |
|---------------------------|----------------|---------------|
| cough/кашель              |  0.831 ± 0.007 | 0.831 ± 0.006 |
| laugh/смех                |  0.907 ± 0.005 | 0.910 ± 0.002 |
| sigh/вздох                |  0.908 ± 0.007 | 0.906 ± 0.006 |
| laugh/смех                |  0.872 ± 0.005 | 0.869 ± 0.008 |
| sniff/вдыхание носом      |  0.914 ± 0.003 | 0.901 ± 0.006 |
| throatcl./прочищение горла|  0.800 ± 0.004 | 0.814 ± 0.005 |
|Average Scores             |  0.747 ± 0.004 | 0.747 ± 0.005 |

**2. Second set of experiments:** 
2.1) The best results for Nonspeech7k were got with SVM-rbf and Nearal Network (NN)+ Interspeech 2013 (IS13) features. It was possible to outclass the SOTA results. The results are the following:
**SVM-rbf:**
|  Class         | F1(SOTA)  | F1(SVM-rbf+IS13) |F1 (NN+IS13)|
|----------------|:---------:|:------------:|:------------:|
| breath/дыхание |0.85       | 0.91         | 0.91|
| cough/кашель   |  0.76     | 0.68         | 0.72|
| cry/плач       |  0.79     | 0.83         | 0.78|
| laugh/смех     |  0.78     | 0.83         | 0.87|
| scream/крик    |  0.83     | 0.85         | 0.82|
| sneeze/чихание |  0.65     | 0.65         | 0.61|
| yawn/зевание   |  0.77     | 0.79         | 0.82|
|Average Weighted Recall|  0.79   | 0.82 | 0.82 |
|Average Weighted Precision|  0.81   | 0.84 | 0.83 |
|Average Weighted F1|  0.80  | 0.84 | 0.82 |

2.2) The best results for Vocal Sound were got with LDA and Nearal Network (NN)+ Interspeech 2013 (IS13) features. The SOTA results were not outclassed The results are the following:

|Metrics |SOTA|LDA+IS13|NN+IS13|
|--------|:--:|:------:|:------:|
|Accuracy|90.5|87.4    |85.9    |

**3. Third set of experiments:** 
3) The best results were achieved in the following case: Vocal Sound for train set, Nonspeech7k for test set, LDA and Neural Network showed the best results woth Interpseech 2013.

**LDA:**
Accuracy = 0.73
|  Class         | F1-score  |Recall  |Precision|
|----------------|:---------:|:------:|:-------:|
| cough/кашель   |  0.74     |0.74    |0.75     |
| laugh/смех     |  0.80     |0.69    |0.95     |
| sneeze/чихание |  0.52     |0.85    |0.37     |
|Average Weighted Recall||  0.73 |
|Average Weighted Precision|||  0.81 |
|Average Weighted F1|  0.75 |


**Neural Network:**
Accuracy = 0.73 
|  Class         | F1-score  |Recall  |Precision|
|----------------|:---------:|:------:|:-------:|
| cough/кашель   |  0.75     |0.73    |0.78     |
| laugh/смех     |  0.80     |0.71    |0.93     |
| sneeze/чихание |  0.52     |0.86    |0.37     |
|Average Weighted Recall||  0.73 |
|Average Weighted Precision|||  0.82|
|Average Weighted F1|  0.75 |

