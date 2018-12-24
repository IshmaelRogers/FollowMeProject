# Ishmael Rogers
# Infinitely Deep Robotics Group 
# www.idrg.io
# Follow Me Project
[image1]: ./images/CNN.png
[image2]: ./images/fcn.png 

This

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


A 1x1 convolution simply maps an input pixel with all it's channels to an output pixel, not looking at anything around itself. It is often used to reduce the number of depth channels, since it is often very slow to multiply volumes with extremely large depths.

When we convert our last fully connected (FC) layer of the CNN to a 1x1 convolutional layer we choose our new conv layer to be big enough so that it will enable us to have this localization effect scaled up to our original input image size then activate pixels to indicate objects and their approximate locations in the scene as shown in above figure. replacement of fully-connected layers with convolutional layers presents an added advantage that during inference (testing your model), you can feed images of any size into your trained network.

One problem with this approach is that we lose some information every time we do convolution (encoding or down-sampling); we keep the smaller picture (the local context) and lose the bigger picture (the global context) for example if we are using max-pooling to reduce the size of the input, and allow the neural network to focus on only the most important elements. Max pooling does this by only retaining the maximum value for each filtered area, and removing the remaining values.





explains each layer of the network architecture and the role that it plays in the overall network. The student can

demonstrate the benefits and/or drawbacks of different network architectures pertaining to this project and can 

justify the current network with factual data. Any choice of 
configurable parameters should also be explained in the network architecture.

The student shall also provide a graph, table, diagram, illustration or figure for the overall network to serve as a reference for the reviewer.


# Section 2 

he student explains their neural network parameters including the values selected and how these values were obtained (i.e. how was hyper tuning performed? Brute force, etc.) Hyper parameters include, but are not limited to:

Epoch
Learning Rate
Batch Size


All configurable parameters should be explicitly stated and justified.


# Section 3 

The student demonstrates a clear understanding of 1 by 1 convolutions and where/when/how it should be used.

The student demonstrates a clear understanding of a fully connected layer and where/when/how it should be used.




# Section 4



The student is able to identify the use of various reasons for encoding / decoding images, when it should be used, why it is useful, and any problems that may arise.




# Section 5

The student is able to clearly articulate whether this model and data would work well for following another object (dog, cat, car, etc.) instead of a human and if not, what changes would be required.






# Section 6




# Section 7 
