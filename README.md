# Wheat-Detection
An object-detection challenge from Kaggle. The competition was launched on May-2020 and currently holds more than 1600 participants (teams and individuals).
The raw data is provided from the Kaggle challange - Global Wheat-head Detection :  
https://www.kaggle.com/c/global-wheat-detection/data    
and consists two parts:  
(1) a dataset of the wheat-heads images (3434 files)  
(2) a csv file specifying all bounding boxes coordinates, specified in COCO format (x,y,width,height))

The original data was combined with augmneted data created using the Albumentation library (The augmented image generator is available in an additional notebook) aand transferred to VOC-PASCAL format (Xmin, Ymin, Xmax, Ymax)
The following object-detection models were considered:
- Faster RCNN - Region based convolutional neural net
- YOLO - "You Only Look Once"  

In the RCNN models initial RoIs (regions of interest) are passed through CNN to define 4-parameters rectangles. YOLO on the other hand trains each image as a grid to produce a vector that defines the existance of an object, the rectancle coordinates and the labels.
Although YOLO is in many cases considered superior in terms of efficiency, I have decided to try FasterRCNN first using a pretrained RCNN model (fasterrcnn_resnet50_fpn). imported from the torchvision library. YOLO was originally coded in c++ by DarkWeb in 2015 and was further modified to work with TensorFlow framework. I intend to use YOLO for this project in the near future.

Evaluation was carried out according to the competition rules. The score of each bbox prediction is based on the IoU metric (intersection of union) and the number of true- detections is a function of the threshold - the minimal IoU score that is considered as a right detection. 
![](https://github.com/omrigo5/Portfolio-Omri-Goldberg/blob/master/Images/publish-1.png?raw=true)
