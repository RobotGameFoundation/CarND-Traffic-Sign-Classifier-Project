
# **Traffic Sign Recognition**

  
**Build a Traffic Sign Recognition Project**

  

The goals / steps of this project are the following:

* Load the data set (see below for links to the project data set)

* Explore, summarize and visualize the data set

* Design, train and test a model architecture

* Use the model to make predictions on new images

* Analyze the softmax probabilities of the new images

* Summarize the results with a written report

  
  

[//]: #  (Image References)

  

[image1]: ./examples/visualization.png  "Visualization"



[image2]: ./new_images/image1.jpg  "Traffic Sign 1"

[image3]: ./new_images/image2.jpg  "Traffic Sign 2"

[image4]: ./new_images/image3.jpg  "Traffic Sign 3"

[image5]: ./new_images/image4.jpg  "Traffic Sign 4"

[image6]: ./new_images/image5.jpg  "Traffic Sign 5"

[image7]: ./new_images/image6.jpg  "Traffic Sign 6"  

## Rubric Points

### Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/481/view) individually and describe how I addressed each point in my implementation.

  

---

### Writeup / README

  

#### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one. You can submit your writeup as markdown or pdf. You can use this template as a guide for writing the report. The submission includes the project code.

  

You're reading it! and here is a link to my [project code](https://github.com/udacity/CarND-Traffic-Sign-Classifier-Project/blob/master/Traffic_Sign_Classifier.ipynb)

  

### Data Set Summary & Exploration

  

#### 1. Provide a basic summary of the data set. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

  

I used the pandas library to calculate summary statistics of the traffic

signs data set:

  

* The size of training set is 34799

* The size of the validation set is 4410

* The size of test set is 12630

* The shape of a traffic sign image is (32,32,3)

* The number of unique classes/labels in the data set is 43

  

#### 2. Include an exploratory visualization of the dataset.

  

Here is an exploratory visualization of the data set. It is a bar chart showing how many examples of each label.

  

![alt text][image1]

  

### Design and Test a Model Architecture

  

#### 1. Describe how you preprocessed the image data. What techniques were chosen and why did you choose these techniques? Consider including images showing the output of each preprocessing technique. Pre-processing refers to techniques such as converting to grayscale, normalization, etc. (OPTIONAL: As described in the "Stand Out Suggestions" part of the rubric, if you generated additional data for training, describe why you decided to generate additional data, how you generated the data, and provide example images of the additional data. Then describe the characteristics of the augmented training set like number of images in the set, number of images for each class, etc.)

  



 As a first step, I normalized the image data because it reduce the noise and make the data more statistically normal.
Then, I shuffle the data to reduce the variance of the image data.



  



  
  

#### 2. Describe what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.

  

My final model consisted of the following layers:

  


| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x3 RGB image   							| 
| Convolution 5x5     	| 1x1 stride, valid padding, outputs 28x28x6 	|
| RELU					|												|
| Avg pooling	      	| 2x2 stride,  outputs 14x14x6  				|
| Convolution 5x5	    |  1x1 stride, valid padding, outputs 10x10x16 	|
| RELU					|												|
| Avg pooling	      	| 2x2 stride,  outputs 5x5x16  				|
| Fully connected		| inputs 400, outputs 120        									|
| RELU	
|Dropout				|		
| Fully connected		| inputs 120, outputs 84        									|
| RELU
|Dropout				|		
| Fully connected		| inputs 84, outputs 43        									|
| Softmax				|
  
  

#### 3. Describe how you trained your model. The discussion can include the type of optimizer, the batch size, number of epochs and any hyperparameters such as learning rate.

  

To train the model, I used an LeNet neural net architecture. I use the AdamOptimizer to optimize. I add  dropout layer after the relu activation layer of the 2  full connected layer.
The batch size was 128 and number of epochs equaled 30. Initial learning rate was set on 0.001.

  

#### 4. Describe the approach taken for finding a solution and getting the validation set accuracy to be at least 0.93. Include in the discussion the results on the training, validation and test sets and where in the code these were calculated. Your approach may have been an iterative process, in which case, outline the steps you took to get to the final solution and why you chose those steps. Perhaps your solution involved an already well known implementation or architecture. In this case, discuss why you think the architecture is suitable for the current problem.

  

My final model results were:

* training set accuracy of   0.999

* validation set accuracy of  0.958

* test set accuracy of  0.940

  





  


  

### Test a Model on New Images

  

#### 1. Choose six German traffic signs found on the web and provide them in the report. For each image, discuss what quality or qualities might be difficult to classify.

  

Here are six German traffic signs that I found on the web:

  

![alt text][image2] ![alt text][image3] ![alt text][image4]

![alt text][image5] ![alt text][image6] ![alt text][image7]

  

The last image might be difficult to classify because after the resize it is hard to identify the image even of human eyes.

  

#### 2. Discuss the model's predictions on these new traffic signs and compare the results to predicting on the test set. At a minimum, discuss what the predictions were, the accuracy on these new predictions, and compare the accuracy to the accuracy on the test set (OPTIONAL: Discuss the results in more detail as described in the "Stand Out Suggestions" part of the rubric).

  

Here are the results of the prediction:

  

| Image | Prediction |

|:---------------------:|:---------------------------------------------:|

| Speed Limit 60 | End of all speed and passing limits |

| Stop | Stop  |

| No passing | No vehicles |

| Children Crossing | Speed Limit 80 |

| Speed Limit 30  |  Speed Limit 30  |

| Bicycle Crossing | Bicycle Crossing |

  
  

The model was able to correctly guess 3 of the 6  traffic signs, which gives an accuracy of 50 .

  

#### 3. Describe how certain the model is when predicting on each of the five new images by looking at the softmax probabilities for each prediction. Provide the top 5 softmax probabilities for each image along with the sign type of each probability. (OPTIONAL: as described in the "Stand Out Suggestions" part of the rubric, visualizations can also be provided such as bar charts)

  

The code for making predictions on my final model is located in the 13th cell of the Ipython notebook.

  


  

### (Optional) Visualizing the Neural Network (See Step 4 of the Ipython notebook for more details)

#### 1. Discuss the visual output of your trained network's feature maps. What characteristics did the neural network use to make classifications?