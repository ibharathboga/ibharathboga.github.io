---
title: "Kaggle - Titanic Spaceship - A Novice Attempt - 72%"
date: 2023-02-04T11:25:18+05:30
draft: true
---
Hey there, hope your day is going well. In this post, I shall document my journey on how i was going through and tried to solve the Titanic Spaceship problem on Kaggle.  

[Click here to go through the problem](https://www.kaggle.com/competitions/spaceship-titanic/)

### What did I understand after reading the problem ?  
People from various planets were on their way to other plants in an interstellar spaceship. They were caught in an anomaly (some kind of cloud). Due to the anomaly almost half of the people got into another dimension.  
We are given the problem to predict the passengers that got into another dimension using the data stored in the main computer of the spaceship.  
[It was now that i decided to have a look into the available data.]

### What did I understand after going through the available data ?  
I suggest you go through the data on your own once, to understand better.  
Three datasets are provided in csv format.  
**train.csv**  
The data upon which our model is to be trained. This dataset contains the target variable called "transported" a boolean value. So we can say this as labelled data. Hence, this problem is associated with supervised learning and also since target variable i.e transported is binary value, it comes under binary classification.  
**test.csv**  
The data that is to be processed by our trained model to make prediction.

The above two datasets have missing values. In order to train our model, we have to deal with the missing values in the train.csv file first. 

**sample_submission.csv**  
To let us know in what way our submission (prediction/answer) should be presented.  

### How did I handle missing values ?
[Reference - Dealing With Missing Data, Harvard](https://harvard-iacs.github.io/2021-CS109A/lectures/lecture09/presentation/Lecture19_Missingdata_np.pdf)  
I chose the simplest approach. Imputing the missing values with most frequent value for each feature.

```python
#to impute we import SimpleImputer
from sklearn.impute import SimpleImputer
#there are 4 available strategies for SimpleImputer.
freqImputer = SimpleImputer(strategy = "most_frequent")  
df = pd.DataFrame(freqImputer.fit_transform(df),columns = df.columns)  
```