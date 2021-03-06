# CMR Image Segmentation: Project Overview #
- Developed an automated process, using convolutional neural networks (CNN), to segment (cardiovascular magnetic resonance) CMR images.
- Implement and trained the deep learning based model through augmenting provided training dataset.
- Model had an accuracy score of approximately 0.83 at labelling CMR images into the following classes:   the background region (black), the left ventricle (LV) region(white), the myocardium (Myo) region (white gray) and the right ventricle (RV) region (dark gray). 

![opencv_seg](https://user-images.githubusercontent.com/74196907/102830431-345aca80-43e1-11eb-807f-711e7d297f04.png)


## Code and resources used ## 
**Python version:** 3.7  
**Packages:** opencv-python, pytorch, torchvision, torchgeometry 

## How to use ##
- **unzip data.zip**
- jupyter notebook openCV_project.ipynb is used to train and evaluate the segmentation model

## Background ## 
Semantic  image  segmentation  of  cardiovascular magnetic resonance (CMR) images.   CMR  imaging  is  the  gold  standard  for  assessing  cardiac  chamber  volume  and  mass  for many cardiovascular diseases.  For decades,  clinicians have been relying on manual segmentation approaches to derive quantitative measures such as left ventricle volume, mass and ejection fraction.However, manual expert segmentation is tedious, time-consuming and prone to subjective errors.It becomes impractical when dealing with large-scale datasets. This automated developed methodology uses Convolutional Neural Network (CNN), segmenting a CMR image into four regions:  the background, the left ventricle (LV), the right ventricle (RV) and the myocardium (Myo). This labelling can be seen in the rightmost tile in the figure below. 

### Dataset ###
First, we introduce the dataset used for this task.  The dataset can be downloaded from the  ACDC1 challenge  but  we  have  modified  it  for  the  sake  of  simplicity.   The  dataset  after  our modifications contains a total of 200 CMR images in a PNG format.  We split the data into 50% for  training,  10%  for  validation  and  40%  for  testing.   For  the  training  set,  there  are  100  CMR mages and 100 respective ground truth mask images. In this project, the provided dataset was augmented to produce a larger dataset. 

### Network architecture ### 
There are many state-of-the-art CNN architectures for semantic image segmentation.  Popular choices are FCN2, DeepLab3, SegNet4, etc.  However, these networks may not be directly applicable to this task due to the limitation of computational power you have. Regardless  of  which  network  you  use,  in this task the input tensor to the network must be of size (B, 1, H, W) and the output tensor from the network must be of size (B, 4, H, W). Here B denotes batch size, H and W stand for image height and width, respectively. In this project we implemented the U-Net architecture 

### Metric ###
Dice  similarity  coefficient5 or simply Dice will be used to measure segmentation perfor-mance with respect to ground truth.  Dice between two binary masks X and Y is defined as the intersection ratio between both the overlap area and the average area of the two masks. 

### Loss function ###
To obtain precise segmentation results, it is important you implement an effective loss function.  Here we use the cross-entropy loss. 
