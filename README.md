## Hand Gesture Recognition
This is a project that helps to create an Object detection model from scratch. The Images are captured, Labelled and then used to train a Single Shot detection Model.

<p align="center">
<img src="/Example.gif"></img>
</p>



### What is a Single Shot Detection Model?
<p align="center">
<img src="/ssd_architecture.jpg"></img>
</p>

Object Detection falls in the realm of Computer Vision and is related to image processing that deals with the detection of instances in single images or videos. This used to be a very difficult process but with the advent of faster compute capabilities came data science and deep neural network. Some of the variants of neural networks used to train object detection models are R-CNN, Faster-CNN, Single Shot Detectors (SSD) and You only look once (YOLO).

Typically Object detection models are divided into two main  types. Single stage (shot) detection models such as YOLO and SSD and multi stage detection models such as R-CNN.  The major difference between the two is that in the two-stage object detection models, the region of interest is first determined and the detection is then performed only on the region of interest. This implies that the multi-stage object detection models are slower but more accurate and the single shot detectors are faster but less accurate compared to the multi stage ones. 


## The DataSet
The uploaded notebook (Image_collection.ipynb) was used to create images using my laptops camera (shows the poor quality of images). The purpose of this project is not to create the most accurate model but to create the most accurate model with very little resources/compute power at hand. The images were trained for 4 classes. i.e thumbsup, thummbsdown, thankyou and livelong. with a total of 16 images per class I used LabelImg to labell the images using box labelling's top left to bottom right technique. The data set was split such that every class had 12 images in the train dataset and 4 images in the test/eval dataset.




## Training
+ First I created a labelMap which is a simple dictionary containing the label names and their respective numbers.
+ All of the XML files containing bounding boxes for each image was then converted to tfrecords using the script available online. Some changes were made to the script for a couple of reasons. Firstly the tensors were converted from a range of zero to one instead of being their pixel representations because the mobile net v2 model used was trained using such values. Secondly, (though a minor change but neverthless important) the xmin, xmax, ymin, ymax values in the tfrecords script where created using a bottom right to top left labelling technique and had to be changed to represent the technique I used.
+ The config file of the mobile net had to be changed to represent 4 classes, a batch size of 4, tfrecords, labelmap, and trianing epochs of 5000

## Evaluation
+ Once the model was trained and all the evaluation metrics were stored I used tensorboard to evaluate, change the parameters are retrain once the desired results were acheived.
+ Evaulation metrics were stored after every 100 epochs. Gamma correction was used to account for different lighting in the images.

# Results
### Classification Loss
<p align="center">
<img src="/Metrics/classification_loss.JPG"></img>
</p>

### Localization Loss
<p align="center">
<img src="/Metrics/localization_loss.JPG"></img>
</p>

### Regulartizatio Loss
<p align="center">
<img src="/Metrics/regularization_loss.JPG"></img>
</p>

### Total Loss
<p align="center">
<img src="/Metrics/total_loss.JPG"></img>
</p>

### Learnign rate
<p align="center">
<img src="/Metrics/learning_rate.JPG"></img>
</p>
