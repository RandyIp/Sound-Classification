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

![image](https://user-images.githubusercontent.com/85899973/141837490-3a6f4309-cdb4-4e4a-8a51-b0b60ba785a2.png)![image](https://user-images.githubusercontent.com/85899973/141837550-1688f50b-07fa-42b7-bc48-52215c6109cb.png)![image](https://user-images.githubusercontent.com/85899973/141837606-f4fdf3f6-5037-43ca-9219-a19be0102bab.png)

* Conclusion:  
Overall, Gaussian Naive Bayes performed poorly. It has an overall accuracy of 65.59% which is a little better than pure random guessing. 
  * The accuracy can be further analyzed by looking at the accuracy given a true label and the accuracy give a predicted label. Given any true label, the accuracy fluctuates between 46% and 77%. This isn't very impressive as it suggests for digits like 2,5 and 7 the model is just purely guessing and even for it's best digit (spoken digit 8) it only does ok at best. 
  * A similar analysis can be done given that the model has predicted a spoken digit. Given any predicted label the accuracy fluctuates between 46% and 82%. This is also a poor result. Given that the model predicts a digit like 2,5 or 9, it is as good as a random guess. Given digits like 0,4 or 6 the model performs ok at best.
Deeper analysis shows that this particular model overpredicts 9 as the spoken digit. Within the code are tests using this model without the spoken digit 9 but since the results did not improve much, they were not added to this document. 
