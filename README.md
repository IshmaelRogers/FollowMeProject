# Ishmael Rogers
# Infinitely Deep Robotics Group 
# www.idrg.io
# Follow Me Project
[image1]: ./images/CNN.png
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
By a factor of 2 is used in the decoder blocks to recover resolution then combines it with the previous encoders layers outputs to get the required up-size. 

Batch normalization 
---
By normalizing the inputs to the network, the input layers to the network become normalize. 

NOTE: "batch" normalization refers to the process of using mean and variance of the to normalize each layer's input. 

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


Learning Rate
---


Batch Size
---

The batch size chosen was 100 because testing at 40 and 65 produced error message. 

![alt text][image4]


Workers
---


Validation 
---





# Section 3 

The student demonstrates a clear understanding of 1 by 1 convolutions and where/when/how it should be used.

The student demonstrates a clear understanding of a fully connected layer and where/when/how it should be used.




# Section 4



The student is able to identify the use of various reasons for encoding / decoding images, when it should be used, why it is useful, and any problems that may arise.




# Section 5

The student is able to clearly articulate whether this model and data would work well for following another object (dog, cat, car, etc.) instead of a human and if not, what changes would be required.






# Section 6




# Section 7 
