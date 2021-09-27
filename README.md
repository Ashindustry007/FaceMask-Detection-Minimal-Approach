<h1 align="center"> 
  <b> FaceMask Detection - A Minimal Approach </b> 
</h1>

<br>

## Introduction:
With the arrival of COVID-19 the world got disturbed in every possible way one can imagine. The medical professionals were the only hope of getting out of it. The virus spread across the globe from one person to another by means of bodily fluid which a common person produces while coughing or sneezing. Hence, wearing mask(s) was made mandatory to stop the spread of virus or at least to put obstruction in the rapid spread of it. Mask acted as a physical barrier to human bodily fluid carrying virus to come out and even not to inhale any other person’s fluid carrying virus. The protocol was effective along with sanitisation and vaccination. But there exists a lot of persons who still don’t use mask. To identify them and to do it automatically we are using facemask detection model developed using deep learning.

<br>

## Methodology:

<h3> 1. Dataset </h3>

We use a combination of two dataset which consists of different types of high and low resolution photos. Basically, they consist of two types of classes, masked and not-masked. Below are the link to the two datasets used. <br>
  - https://www.kaggle.com/ashishjangra27/face-mask-12k-images-dataset <br>
  - https://www.kaggle.com/prithwirajmitra/covid-face-mask-detection-dataset

<h3> 2. Data pre-processing </h3>

Any image below 75*75 pixels were dropped. The pixels are then scaled and the image is then sheared, zoomed, rotated, and horizontally flipped. The augmented images were then ready for being trained on.

<h3> 3. Model Development </h3>

We are using transfer learning of VGG16 with weights of imagenet and then fine tuning with another hidden layer with 32 neurons before the final output layer with two neurons. The optimizer that was most compatible is Adam and the loss function is Binary Crossentropy. The callback we are using for the model is reducing learning rate on plateau monitoring the validation loss.

The model architecture looks like the one below.

<P align="center">
<img align = "center" src = "https://user-images.githubusercontent.com/44130583/134890581-acd7b984-6d8b-47f0-8cd3-726620d54716.png">
</p>


The ‘training and validation accuracy’ & ‘training and validation loss’ is stated below, 

The model was trained over 50 epochs. By the end of the training the loss and accuracy were as such. 
Training loss - 0.0208
Training accuracy - 0.9961
Validation loss - 0.0514
Validation accuracy - 0.9840
The graph has been unstable but the towards the end the rate of change of graphical values decreases and the result obtained is surely an optimal one.



Results:

The confusion matrix shows,

Correctly predicted Masked = 552
Correctly Predicted Not-masked = 466
Masked predicted as Not-masked = 26
Not-masked predicted as masked = 3

In this case we are best avoiding the false positive (not masked predicted as masked) to be as low as possible, because we should not miss out on those people who don’t wear mask and helps in spreading the virus. That being only 3 cases, we can say that the model is quite good for the real world usage.
Below is the Classification report stating the precision, recall, and f1-score of the model. So the accuracy is 97% which is a pretty good score but can be further increased. 

