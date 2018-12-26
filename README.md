# Ishmael Rogers
# Infinitely Deep Robotics Group 
# www.idrg.io
# Follow Me Project
[image1]: ./images/CNN.jpg
[image2]: ./images/fcn.png 
[image3]: ./images/skipp_connect.png
[image4]: .images/100_batch.png

Convolutional Networks
---
A CNN contains many layers that each capture differents feartures at different levels of object's hiearchy. At the lowest level (the first layer) in the hierarchy, the CNN classifies small parts of the image based on simple shapes i.e horizontal/vertical lines and blobs of colors. The layers that follow tend to be higher in the hierarchy and are used to classify more complex ideas like shapes (combinations of lines), and eventually full objects like flowers.

![alt text][image1]


A Fully Convolutional Network (FCN) is similiar to a CNN except the last fully connected layer (i.e the classification layer) is substituted by a 1x1 convolution layer with a large "receptive field". With this structure the goal is to capture the full scope of the scene and determine two things 

1. What are the different objects in the scene 
2. Where are they located in the scene. 


The structure of FCN is divided into two parts:

1. The convolution i.e the encoderpart which will extract features from the image 
2. The Transposed convolution, deconvolution or decoder part which will upscale the output of the encoder (or reverse the convolution) so that it is in the original size of the image.

![alt text][image2]


A 1x1 convolution simply maps an input pixel with all it's channels to an output. We use it here to reduce the number of depth channels.


The last Fully Connected (FC) layer of the CNN is converted to a 1x1 convolutional layer. The new convolution layer is designed to be big enough so that it will allow the localization effect to be scaled up to our original input image size. From there, activate the pixels that indicate objects as well as their approximate locations within the scene. 

Advantage
---
Replacing the fully-connected layers with convolutional layers allows the model to handle images of any size into the trained network.

Disadvantage
---
Information is lost each time we encoding (or down-sample); 

NOTE: The smaller picture is kept (the local context) and the bigger picture (the global context) is lost.

Using max-pooling reduces the size of the input and allows the neural network to focus on only the most important elements. This accomplished by only retaining the maximum value for each filtered area, while removing the remaining values.

Activations from previous layers (aka skip connections) are sumed/interpolated together with the up-sampled outputs when decoding from the previous layer. See diagram below.

![alt text][image3]

Bilinear Upsampling
---
2 factor bilinear upsampling is used in the decoder blocks to recover the lost resolution then combines it with the previous encoder layers outputs to get the original image size.  

Batch normalization 
---
By normalizing the inputs to the network, the input layers to the network also become normalize. 

NOTE: "batch" normalization refers to the process of using mean and variance to normalize each layer's input at every batch level. 

Advantage
--- 
1. Networks train faster
2. Higher learning rates
3. Simplifies the creation of deeper networks
4. Provides a bit of regularization.

Summary
---

1. Encoder blocks: take inputs from previous layers, and compresses it down. Thus losing some of the resolution (i.e the bigger picture).

2. 1x1 Convolution block: Reduces the depth and captures the global context of the scene.

3. Decoder blocks: Receieves inputs from previous layers, decompress it using up-sampling and adds inputs from the previous encoder blocks through skip connections thus recovering some of the lost information.

4. Softmax activation: Normal convolution layer takes outputs from last decoder block activates the output pixels to indicate the class and location of objects, thus semantic segmentation. 


# Hyper-parameters 


Epoch
---
An epoch refers to the number of times the entire training dataset gets propagated through a given network.

NOTE: One epoch is a single forward and backward pass of the whole dataset. 

This method is used to increase the accuracy of the model without needing aditional data. 

Learning Rate
---
This parameter controls the size of the weights and biases. Based on excersies in the course my goal is to try the brute force method using the following values: 

1. 0.01
2. 0.001
3. 0.0001

Batch Size
---

The batch size chosen was 100 because testing at 40 and 65 produced error message. 

![alt text][image4]


Workers
---


Validation 
---


Steps
---
Refers to the number of batches of training images that are passed through the network in 1 epoch.

How to determine steps per epoch 
---
Using dataset 1 and AWS

% n = number of images
n = 4131

% bs = batch size
bs = 100

% spe = steps per epoch 

spe = n /bs = # 41.31 


Can the model track other objects?
---

To track different objects, change the mask data and re-train the network on a new target (cars, flowers, insects, etc.).


