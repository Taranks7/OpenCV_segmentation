# OpenCV_segmentation #

## unzip data.zip ##

**Install dependencies** |
------------- | 
opencv-python  |
pytorch  |
torchvision |
torchgeometry |



Semantic  image  segmentation  of  cardiovascular  MR  (CMR)images.   CMR  imaging  is  the  gold  standard  for  assessing  cardiac  chamber  volume  and  mass  formany cardiovascular diseases.  For decades,  clinicians have been relying on manual segmentationapproaches to derive quantitative measures such as left ventricle volume, mass and ejection fraction.However, manual expert segmentation is tedious, time-consuming and prone to subjective errors.It becomes impractical when dealing with large-scale datasets. This automated developed methodology uses Convolutional Neural Network (CNN), segmenting a CMR image into four regions:  the background, the left ventricle (LV), the rightventricle (RV) and the myocardium (Myo). 

## Dataset ##
First, we introduce the dataset used for this task.  The dataset can be downloaded fromthe  ACDC1challenge  but  we  have  modified  it  for  the  sake  of  simplicity.   The  dataset  after  ourmodifications contains a totoal of 200 CMR images in a PNG format.  We split the data into 50%for  training,  10%  for  validation  and  40%  for  testing.   For  the  training  set,  there  are  100  CMR mages and 100 respective ground truth mask images. In this project, the provided dataset was augmented to produce a larger dataset. 

## Network architecture ## 
There are many state-of-the-art CNN architectures for semantic imagesegmentation.  Popular choices are FCN2, DeepLab3, SegNet4, etc.  However, these networks maynot be directly applicable to this task due to the limitation of computational power you have. Regardless  of  which  network  you  use,  inthis task the input tensor to the network must be of size (B, 1, H, W) and the outputtensor from the network must be of size (B, 4, H, W). Here B denotes batch size, Hand W stand for image height and width, respectively. In this project we implemented the U-Net architecture 

## Metric ##
Dice  similarity  coefficient5or simplyDicewill be used to measure segmentation perfor-mance with respect to ground truth.  Dice between two binary masksXandYis defined as theintersection ratio between both the overlap area and the average area of the two masks. 

## Loss function ##
To obtain precise segmentation results, it is important you implement an effectiveloss function.  Here we use the cross-entropy loss. 
