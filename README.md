# Wheat-Detection
An object-detection challenge from Kaggle launched on May-2020. 
The raw data is provided from the Kaggle challange - Global Wheat-head Detection :  
https://www.kaggle.com/c/global-wheat-detection/data  
and consist two parts:
(1) a dataset of the wheat-head images (3434 files)
(2) a csv file specifying all bounding boxes coordinates, specified in COCO format (x,y,width,height))

The original data was combined with augmneted data created using the Albumentation library (The augmented image generator is available in an additional notebook) aand transferred to VOC-PASCAL format (Xmin, Ymin, Xmax, Ymax)
The following object-detection models were considered:
- Faster RCNN - Region based convolutional neural net
- YOLO - "You Only Look Once"  

I used an RCNN model from the torchvision library which was pretrained using resnet50. In the RCNN models initial RoIs (regions of interest) are passed through CNN to define 4-parameters rectangles. YOLO on the other hand trains each image as a grid to produce a vector that defines the existance of an object, the rectancle coordinates and the labels.
Although YOLO is in many cases considered as a more efficient model the FasterRCNN was evaluated first. YOLO was originally written in c++ by DarkWeb in 2015, it is currently not compatible to the Pytorch framework but was modified to work with TensorFlow. The YOLO model will be hopefully estimated as well for this project in the near future.

Evaluation was carried out according to the competition rules. The score of each bbox prediction is based on the IoU metric (intersection of union) and the number of true- detections is a function of the threshold - the minimal IoU score that is considered as a right detection. 
