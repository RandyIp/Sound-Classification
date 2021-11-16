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

* Sample Spectrogram:

![image](https://user-images.githubusercontent.com/85899973/141873639-577d985b-b4f3-4bb4-b5eb-ffc04f355a90.png)

# Benchmarking

Cross validation combined with confusion matrices were the main benchmarks. K means has it's own way of benchmarking since it is an unsupervised technique and will be discussed later.

**Cross Validation:**

10-fold cross validation was used in each test. This means that each dataset was randomly divided into 10 subsets and 10 tests were used. In each test, one of the subsets would be considered as test data while the remaining 9 subsets would be considered as training data. 

**Confusion Matrix:**

The confusion matrix serves as a visual to see how well each machine learning technique performed. In my confusion matrices, the predicted labels are along the x-axis while the true labels are along the y-axis. Any number that is not along the diagonal of the matrix represents incorrect classifications. (Note: There are 10 different tests so the confusion matrices being shown are a sum total of all 10 confusion matrices.)

# Gaussian Naive Bayes:
* How it works:  

Gaussian Naive Bayes is a model based supervised machine learning technique. It assumes that each class (or each of the spoken digits from 0 to 9) can be approximated by a Gaussian distribution (or equivalently, normal distribution). The training data is used to get the maximum likelihood estimators (MLE) for the parameters of each Gaussian distribution for each class.  

* Result: 

![image](https://user-images.githubusercontent.com/85899973/141873676-2d11c4d8-c974-4a30-916c-019c8b66863a.png)

Overall Accuracy: 65.59%

* Deeper Analysis: 

![image](https://user-images.githubusercontent.com/85899973/141874037-c5984dce-9cb9-4218-8bcc-8c083d9b59f1.png)![image](https://user-images.githubusercontent.com/85899973/141874057-59737032-b699-4f13-8b0e-9586bbc679fc.png)![image](https://user-images.githubusercontent.com/85899973/141874074-8b09e37a-d418-4f02-8a37-f568ffe0d412.png)

* Conclusion:  
Overall, Gaussian Naive Bayes performed poorly. It has an overall accuracy of 65.59% which is a little better than pure random guessing. 

  * The accuracy can be further analyzed by looking at the accuracy given a true label and the accuracy give a predicted label. Given any true label, the accuracy fluctuates between 46% and 77%. This isn't very impressive as it suggests for digits like 2,5 and 7 the model is just purely guessing and even for it's best digit (spoken digit 8) it only does ok at best. 
  * A similar analysis can be done given that the model has predicted a spoken digit. Given any predicted label the accuracy fluctuates between 46% and 82%. This is also a poor result. Given that the model predicts a digit like 2,5 or 9, it is as good as a random guess. Given digits like 0,4 or 6 the model performs ok at best.
  * This particular model overpredicts 9 as the spoken digit. Within the code are tests using this model without the spoken digit 9 but since the results did not improve much, they were not added to this document. 

# Decision Tree: 
* How it works:
 
Decision Trees try to classify data points by separating each data point by their features (or equivalently the columns in this case). Generally, decision trees perform better when the features are highly correlated to the class that is being predicted. This means that decision trees generally do not perform well for image recognition such as our tests with spectrograms. Each pixel of the spectrogram is a feature in this case but each pixel also contains very little information about the classification of the overall data point. 

Even though the results are expected to be poor, the goal of this project is to benchmark each technique. This particular experiment is to verify the expected result. 

* Result: 

![image](https://user-images.githubusercontent.com/85899973/141873280-ff75db0d-c255-44eb-8654-6dbc6b3ac796.png)

Overall Accuracy: 62.13%

* Deeper Analysis: 

![image](https://user-images.githubusercontent.com/85899973/141874494-ccfa54f9-9a08-4b5d-bd81-147c0bff367b.png)![image](https://user-images.githubusercontent.com/85899973/141874499-e370a302-292e-43e9-b653-82d72804957f.png)![image](https://user-images.githubusercontent.com/85899973/141874508-69135351-41c4-4816-ba9b-74243a9cca2f.png)

* Conclusion:

# K Nearest Neighbors

Result: 

![image](https://user-images.githubusercontent.com/85899973/141875026-55be1056-c084-4fed-9343-5a973769e1dd.png)

Overall Accuracy: 91.26% 

Deeper Analysis: 

