# Goal: 
The goal of this project is to benchmark machine learning techniques when used to classify sound files. 

Supervised Machine Learning Techniques used:  
* Gaussian Naive Bayes
* Decision Trees 
* K Nearest Neighbors 

Unsupervised Machine Learning Techniques used:  
* K Means
# Dataset
 
The dataset used can be found in the repository and is called MNIST_Spoken_Digits.rar. This dataset contains spoken digits from 0 to 9. There are 3000 .wav files in the dataset and each individual spoken digit has 300 .wav files. Each sound file is transformed into a spectrogram prior to classification so this project uses image recognition techniques to try and classify sounds. 

![image](https://user-images.githubusercontent.com/85899973/141192136-4e99f390-5a45-4fed-9dfe-183aee0da503.png)

# Benchmarking

Cross validation combined with confusion matrices were the main benchmarks. K means has it's own way of benchmarking since it is an unsupervised technique and will be discussed later.

**Cross Validation:**

10-fold cross validation was used in each test. This means that each dataset was randomly divided into 10 subsets and 10 tests were used. In each test, one of the subsets would be considered as test data while the remaining 9 subsets would be considered as training data. 

**Confusion Matrix:**

The confusion matrix serves as a visual to see how well each machine learning technique performed. In my confusion matrices, the predicted labels are along the x-axis while the true labels are along the y-axis. Any number that is not along the diagonal of the matrix represents incorrect classifications.

# Gaussian Naive Bayes:
* How it works:  

Gaussian Naive Bayes is a model based supervised machine learning technique. It assumes that each class (or each of the spoken digits from 0 to 9) can be approximated by a Gaussian distribution (or equivalently, normal distribution). The training data is used to get the maximum likelihood estimators (MLE) for the parameters of each Gaussian distribution for each class.  

* Result: 

![image](https://user-images.githubusercontent.com/85899973/141359174-cc156ad7-0932-4303-ad91-1220cb8405cf.png)

Overall accuracy: 65.59%

* Deeper Analysis: 

![image](https://user-images.githubusercontent.com/85899973/141378584-3c5c27cc-4285-4608-9dfb-393386f4184d.png)![image](https://user-images.githubusercontent.com/85899973/141378621-54096a8c-a7a0-4ff7-80e9-f3a6c4f4bfe5.png)![image](https://user-images.githubusercontent.com/85899973/141378667-c3b0a529-76ed-416f-9a7a-8658e6faa510.png)

* Conclusion:

