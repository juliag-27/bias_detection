# bias_detection README
<h2> Project Overview </h2>
This project is a machine learning pipeline for detecting bias in Reddit comments, with the hope that it can be extended to clean text comments in datasets before training LLMS. It primarily uses BERT (Bidirectional Encoder Representations from Transformers) for sequence classifications and is evaluated with K-Fold Cross-Validation. 

<h3> Files </h3>

- Bias_Detection : Trained and fine-tuned model pipeline
- Preprocessing + Visualization : Early preprocessing and visualizing work with pandas
- Meta 1A : Slidedeck presentation for my fellowship

<h2> Methods </h2>
<h3> Data </h3>
See more about the data from the original dataset here: https://github.com/umanlp/RedditBias
Dataset includes annotated Reddit comments on the following dimensions:

- Orientation (LGBTQ+ related comments)
- Gender (comments involving women and female roles)
- Religion (comments related to the Jewish and Muslamic)
- Race (comments related primarily to Black individuals)
The size of the unprocessed dataset was 28,133 rows.

<h3> Tools and Libraries </h3>
Language: Python 3.7+
Libraries: HuggingFace Datasets and Transformers and BERT, pandas, numpy, sklearn, PyTorch

This project was primarily worked on in Google Colab, using the T4 GPU. 

<h3> Preprocessing </h3>
Irrelevant and mislabelled rows were removed. Duplicate/spam comments that consisted of less than 1% of the dataset were kept. Nonbinary labels were also removed. After preprocessing, the resulting dataset was 12,166 comments. 

- Gender: 2,976
- Orientation: 1,983
- Race: 3,000
- Jewish Religion: 2,095
- Muslim Religion: 2,112

<h3> Tokenization </h3>
The data was split into a 70/20/10 train, validation, and test set. Conversion into HuggingFace Dataset was necessary for input into the BERT AutoTokenizer. 

<h3> Modelling/Evaluation </h3>
Accuracy: accuracy_score metric from SciKit-Learn
Optimization: AdamW optimizer and linear scheduler 

- Model 1: 3 Epochs, Learning Rate 5e-5, Test Accuracy of 0.59
- Model 2: 10 Epochs, Learning Rate 0.05, Test Accuracy of 0.56
- Model 3: 2 folds, 10 Epochs, Learing Rate 2e-5, Test Accuracy of 0.71

<h3> Conclusions </h3>

Understanding bias in online platforms and rapid evaluation in datasets will be crucial as LLMs and digital work continue to be utilized across industries, especially in areas like healthcare diagnoses. 

