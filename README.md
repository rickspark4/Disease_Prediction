# Disease_Prediction

Since the dataset wasn't provided to Build this tool i used dataset available on Kaggle (https://www.kaggle.com/kaushil268/disease-prediction-using-machine-learning).


### DataSet Description:

1) Dataset contains total 4920 Rows and 133 Columns.
2) Dataset contains total 41 unique Diseases to predict.
3) Dataset has 133 columns and each column representing unique Symptom.
4) Each dataset column contain 2 unique values i.e, (0 & 1). If symptom has particular role to cause that disease then it considered as 
   1 otherwise it will be 0.

(Note- Dataset doesn't contain symptoms for Covid-19)


### Data Preparation:

1) Dataset doesn't contain any Null value.
2) Values in dataset ranges between 0 & 1 so there is no need to use any Standardization method.
3) Dataset is balanced.
4) Almost all the Symptoms has very weak linear corelation in between, so we can consider all the feature for our model.


### How to use Tool :


1) Tool is in the form of .py file

2) To get Disease as a output user has to Enter total number of symtoms he/she wants to enter. After entering number user can enter their
symptoms one by one.

3) after Entering symptoms top 3 most probable disease will return in the decending order of the probablity.


### Algorithm:

Choosing algorithm is wholely depend upon the type of data we have, in my case the dataset which i used is small dataset and contained specific number of rows, all the columns are 
categorical in nature. Since my dataset was small i decided to use Random Forest and Naive Bayes, for the smaller datasets these two algorithm works very well, Small datasets always 
leads to overfiiting which we can avoid using Random Forest, since Random forest uses multiple decision tree which trains on small chunks of data and uses voting method to process its 
output at the end which avoids overfitting other than that Naive bayes is also best for small datasets and Multi-Class Classification, since our dataset is small and all of the our 
feature are categorical in nature and it allows independent and equal contribution of each feature in decision making which makes this algorithm best for this kind of task.

Since, I got 100% Accuracy on both of the algorithm for my test dataset other than that precision and recall is also same for both of the algorithm.
but i decided to use Naive Bayes in my actual tool, due to its special ability to treat each feature as an indepent and its works well on High Dimentional data since we have 133 columns 
in our dataset which is actually high dimensional data.Other than that Our all features are categorical in nature which actually best for Naive bayes and it is also faster than Random
Forest.


### Actual Working of the Algorithm & ML Tool:

I will try to explain it in Lehman's way

Naïve Bayes is a probabilistic machine learning algorithm which works on principle of Bayes Theorem.

P(A|B) = (P(B|A) * P(A)) / P(B)

Which tells us: how often A happens given that B happens, written P(A|B) also called posterior probability, 
When we know: how often B happens given that A happens, written P(B|A) and how likely A is on its own, written P(A) and how likely B is on its own, written P(B).

But Naive Bayes made one Assumption in Bayes Theorem this what "Naive" reflects in Naive Bayes.

The fundamental Naïve Bayes assumption is that each feature makes an:

independent & equal contribution to the outcome.


lets see, how it actually works practically,

In our dataset we have 133 feature and 41 outpiut column so naive bayes will calculate probablity with respect to each class.

lets see how,

I am writting some of the feature,

Note: we have only two variable in each column either 1 or 0, 

lets suppose user chose 7 symptoms, so only those symptoms will be considerd as 1 otherwisw it will be 0.

Note: We dont consider term in denominator since while calculating probablity we divides every calculation with equal term i.e P(B).

P(Covid | Itching(0), headache(1), cold(1),...,133th feature(0)) = P( Itching | Covid ) * P( Headche | Covid) *....* P( 133th feature | Covid ) * P(Covid)

P( Maleria | Itching(0), headache(1), cold(1),...,133th feature(0)) = P( Itching | Maleria ) * P( Headche | Maleria ) *...* P( 133th feature | Maleria  ) * P(Maleria)

P(Typhoid | Itching(0), headache(1), cold(1),...,133th feature(0)) = P( Itching | Typhoid) * P( Headche | Typhoid ) *...* P( 133th feature | Typhoid) * P(Typhoid)

.
.
.
Likewise we calculate probablity for each and every class and whichever class has highest probablity will be return as ouput.

In Training Phase what Naive bayes does is  create a Frequency Table for each attribute against the target. Then, molding the frequency tables to Likelihood Tables 
and finally, use the Naïve Bayesian equation to calculate the (Final) posterior probability for each class. 


Note- I also attached Word file  to explain Naive Bayes with Dummy Example


















