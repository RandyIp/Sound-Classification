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

![image](https://user-images.githubusercontent.com/85899973/141875144-5c8adb7b-3eb8-4d51-a1d7-d53a72cfef48.png)![image](https://user-images.githubusercontent.com/85899973/141875159-6e5736c3-0b8b-4ee7-abf4-213840ddc609.png)![image](https://user-images.githubusercontent.com/85899973/141875168-a776e2f6-4cb3-4c1f-b8d2-58d8b79dafda.png)

* Conclusion:  
Overall, Gaussian Naive Bayes performed poorly. It has an overall accuracy of 65.59% which is a little better than pure random guessing. 

  * The accuracy can be further analyzed by looking at the accuracy given a true label and the accuracy give a predicted label. Given any true label, the accuracy fluctuates between 46% and 77%. This isn't very impressive as it suggests for digits like 3,5 and 7 the model is just purely guessing and even for it's best digit (spoken digit 8) it only does ok at best. 
  * A similar analysis can be done given that the model has predicted a spoken digit. Given any predicted label the accuracy fluctuates between 46% and 82%. This is also a poor result. Given that the model predicts a digit like 2,5 or 9, it is as good as a random guess. Given digits like 0,4 or 6 the model performs ok at best.
  * This particular model overpredicts 9 as the spoken digit. Within the code are tests using this model without the spoken digit 9 but since the results did not improve much, they were not added to this document. 

# Decision Tree: 
* How it works:
 
Decision Trees try to classify data points by separating each data point by their features (or equivalently the columns in this case). Generally, decision trees perform better when the features are highly correlated to the class that is being predicted. This means that decision trees generally do not perform well for image recognition such as our tests with spectrograms. Each pixel of the spectrogram is a feature in this case but each pixel also contains very little information about the classification of the overall data point. 

Even though the results are expected to be poor, the goal of this project is to benchmark each technique. This particular experiment is to verify the expected result. 

* Result: 

![image](https://user-images.githubusercontent.com/85899973/141882753-7f28d775-fd52-4242-bfe1-46926509821f.png)

Overall Accuracy: 63.76%

* Deeper Analysis: 

![image](https://user-images.githubusercontent.com/85899973/141882798-ecc13d77-f89d-4750-b4e8-23605d4f289f.png)![image](https://user-images.githubusercontent.com/85899973/141882817-3e4baa32-5f93-4021-96ef-89c9a7513170.png)![image](https://user-images.githubusercontent.com/85899973/141882837-0fd7b2ca-899c-45a2-bfe4-076152e69db3.png)

* Conclusion:
Overall, decision trees performed poorly when trying to classify spectrograms. It has an even lower overall accuracy of 63.76% which is slightly better than guessing. Furthermore, when looking at the deeper analysis, the individaul accuracies are very poor as well. 
  * The accuracy per true label fluctuates between 49.33% and 75%. While this looks similar to Naive Gaussian Bayes, it may actually be worse. Most true labels hover around a 60% accuracy which means given any true label the model is mostly just guessing. Compared to Naive Gaussian Bayes, even though it wasn't performing well with every true label, it did perform well with some. 
  * The accuracy per predicted label fluctuates between 51.03% and 71.79%. Similar to percent accuracy per true label, the percent accuracy per predicted label seems to be consistently low and most predicted labels hover around 60% accuracy. 
  * No number was overpredicted with decision trees unlike in Naive Gaussian Bayes. It looks like most digits were predicted at roughly the same frequency which is good. This is the only aspect in which decision trees seemed to work well, no individual digit dominated or was under-represented. 

# K Nearest Neighbors

* Result: 

![image](https://user-images.githubusercontent.com/85899973/141884791-e9e7e993-3d5b-44e8-b380-d9f9154a1605.png)

Overall Accuracy: 90.86%

* Deeper Analysis: 

![image](https://user-images.githubusercontent.com/85899973/141884858-a26701c9-0a47-4733-9a11-fc60cf371b84.png)![image](https://user-images.githubusercontent.com/85899973/141884871-fefb0486-5861-48e3-bcee-8e1736d4dcb7.png)![image](https://user-images.githubusercontent.com/85899973/141884881-3b83e1bf-52b8-456d-acfc-f18f8ad03785.png)

* Conclusion:
Easily the best performing technique so far with an accuracy of 90.86%. Still far from ideal but it is something that can be further worked upon. Also, the graphs from the deeper analysis don't show any glaring flaws either. 
  * The percent accuracy per true label ranges from 85.67% to 96%. The lowest accuracy is 85.67% which isn't great but isn't bad either. The true labels this model struggles the most with are 3,6,7 and 9. 
  * The percent accuracy per predicted label ranges from 83.33% to 96.99%. As before, the lowest accuracy is 83.33% which isn't great but isn't terrible either. The predicted labels with the lowest accuracies are 1,2 and 3. 
  * There is no obvious dominating or under-represented digit in prediction frequency. Each digit was predicted roughly the same number of times which is what the model should predict. 

# K Means 

* How it works: 

K Means doesn't use any labels. Instead, it tries to create clusters by minimizing distance between 

* Benchmarking: 
Since K Means is an unsupervised technique, the benchmarking will be different and albeit a bit simpler. There are no true labels in an unsupervised machine learning technique so the only way to see how well it performs is if each cluster produced looks like what would be expected. In this case, there should be 10 clusters with 300 data points in each cluster. 



# Conclusion
