# Image-Forgery-Detection
Image Manipulation Detection using ELA and Deep Learning

Dataset - We have used the widely popular CASIA dataset. It contains 7243
original images and 3594 manipulated images. This gives us a good
amount of data to train our model. We also test our model with a smaller
subset of the above mentioned dataset.

Initial Preparation - Error Level Analysis - As the first step, we perform Error Level Analysis(ELA) on all the images in
the dataset. This starts with resaving all the images and then taking the
absolute difference between the individual pixel values of the original image
and the resaved image. This gives us the ELA image of that particular image.
Since the difference in pixel values is very less, we then enhance the image to
highlight the differences and increase the quality of ELA image. We do this by
first normalizing the pixel value according to the extremes, and then scaling it
to 255, which gives us a clear view of the ELA image.which is the standard for
any RGB image. Finally, we enhance the brightness of the image, which gives
us a clear view of the ELA image.

Data preparation - For this step, we first normalize the data in order to make it feedable to the
CNN architecture. Then we split the dataset into training and testing sets. We
use 90% of the data to train the model, and 10% of the images are used to
test the model.

Convolutional Neural Network - The first layer of our CNN is the Convolutional layer where each image is
subjected to 32 kernels/filters, where each filter is of dimension 5x5. It takes
the 128x128x3 input , where the dimensions represent a standard RGB
image. In this layer. Rectified Linear Unit(ReLU) is used as the activating
function.
The second layer is also a Convolutional Layer, which takes inputs from the
first layer. The second layer also subjects the input to 32 kernels, each kernel
being 5x5 in dimensions. Again ReLU is used as an activating function. The
output to this layer is of dimensions 120x120x3.
The third layer in our CNN architecture is a Max Pooling layer, where we use
2x2 kernels to get the max values and reduce the dimensionality and size of
images. This reduces the number of parameters, and helps in preventing
overfitting. The output from this layer is 60x60x32.
We further prevent overfitting by a dropout of 25% parameters.
Then we add two dense fully connected layers, each with its own dropout of
25%. First layer has ReLU as activation functions while the last output layer
uses Softmax function as its activation function.
We used Categorical_Crossentropy to calculate the loss(loss function), and
RMS is used as an optimizer for the Model.

