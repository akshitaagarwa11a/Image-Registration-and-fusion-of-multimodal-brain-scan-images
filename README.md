# Image-Registration-and-fusion-of-multimodal-brain-scan-images

This is an adaptation of the paper written by Siddeshappa Nandish, Gopalakrishna Prabhu and Kadavigere V.Rajagopal 
named Multiresolution image registration for multimodal brain images and fusion for better neurosurgical 
planning. Image registration and fusion of the two modalities has been done by using a Deep Neural Network. 
The results of the research paper mentioned above have been used to train the model. Supervised Machine Learning 
has been used to do so. 

## Technology used
The project is made using PyTorch framework. It has been on the Colaboratory notebook of Google, a platform which 
provides free GPU services. As the training of the model requires high amount of processing, GPU was required.

## Data
The data used in this project, known as the Mendeley Data, has 3D images of MRI scan and CT scan and the fused 3D image 
in .img and .hdr format. The MRI image has 220 slices, the CT image has 206 slices and the fused image has 220 slices. 
The size of each slice is 256X256. Figure 1, 2 and 3 shows an example slice from each image.
![Figure 1](https://github.com/akshitaagarwa11a/Image-Registration-and-fusion-of-multimodal-brain-scan-images/blob/master/CT.png)
![Figure 2](https://github.com/akshitaagarwa11a/Image-Registration-and-fusion-of-multimodal-brain-scan-images/blob/master/MRI.png)
![Figure 3](https://github.com/akshitaagarwa11a/Image-Registration-and-fusion-of-multimodal-brain-scan-images/blob/master/fused.png)
## Deep Neural Network(Model description)
The model is made using Convolutional Neural Networks(CNNs). The structureof the model consists of 5 downsampling layers 
and 4 upsampling layers. Eachdownsampling layer consists of two convolutional layers with filters of size 3X3where stride is
1 and a pooling layer of stride 2. Whereas each upsampling layerconsists of bilinear interpolation with scale size of 2 
followed by two convolutionallayers with filters of size 3X3 where stride is 1. To introduce non-linearity, ReLUactivation 
function has been used. 
The concatenation of slices of CT and MRI images has been passed as the input to the model and the label of the model is the
corresponding fused slice. The size of the concatenated input image is (256X256X2) and the size of the label is 
(256X256X1).  
The model has been trained using different optimizers. The optimizer which displayed the best result is Adam optimizer. 
We used a scheduler to keep a track on the learning rate of the model. The model was trained in over 100 epochs.
