# Goal: 
The goal of this project is to benchmark machine learning techniques when used to classify the sound files. 

# Project Breakdown
The dataset usspoken digits from 0 to 9. Each sound file is transformed into a spectrogram prior to classification so this project uses image recognition techniques to try and classify sounds. 

![image](https://user-images.githubusercontent.com/85899973/141192136-4e99f390-5a45-4fed-9dfe-183aee0da503.png)


Supervised ML Techniques used:  
* Gaussian Naive Bayes
* Decision Trees 
* K Nearest Neighbors 

Unsupervised ML Techniques used:  
* K Means

Benchmarking:

Cross validation combined with confusion matrices were the main benchmarks. K means has it's own way of benchmarking since it is an unsupervised technique and will be discussed later.

Cross Validation:

10-fold cross validation was used in each test. This means that each dataset was broken into 10 subsets and tested 10 times. In each test, one of the subsets would be considered as test data while the remaining 9 subsets would be considered as training data. 

Confusion Matrix:

The confusion matrix serves as a visual to see how well each machine learning technique performed. In my confusion matrices, the predicted labels are along the x-axis while the true labels are along the y-axis. Any number that is not along the diagonal of the matrix represents incorrect classifications.

Example Confusion Matrix: 

![image](https://user-images.githubusercontent.com/85899973/141202901-85c488f3-e3fb-4775-883d-dfa29b9328c5.png)

Gaussian Naive Bayes:
* How it works:  

Gaussian Naive Bayes is a model based supervised machine learning technique. It assumes that each class (or each of the spoken digits from 0 to 9) can be approximated by a Gaussian distribution (or equivalently, normal distribution). The training data is used to get the maximum likelihood estimators (MLE) for the parameters of each Gaussian distribution for each class.  

* Results: 

![image](https://user-images.githubusercontent.com/85899973/141359174-cc156ad7-0932-4303-ad91-1220cb8405cf.png)

Overall accuracy: 65.59%
