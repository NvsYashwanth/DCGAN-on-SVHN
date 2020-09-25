# DCGAN-on-SVHN
Implementation of DCGAN on the Street View House Numbers (SVHN) dataset.

THIS README WILL WALK YOU THROUGH THE PROJECT. PLEASE READ IT ONCE TO GET AN IDEA OF THE PROJECT WORKFLOW.

## Street View House Number (SVHN) dataset
* You'll be training DCGAN on the Street View House Numbers (SVHN) dataset. These are color images of house numbers collected from Google street view. SVHN images are in color and much more variable than MNIST.
* [Data can be downloaded from here](http://ufldl.stanford.edu/housenumbers/)

## Pre-processing and data loading
* We just need to convert the data into a tensor and prepare our data loaders.

## Visualizing our training data
* We will now generate a batch of data and visualize the same. Please note that the np.transpose function translates the image dimension by the order specified. For example, an RGB image of shape 3x32x32 gets transposed to 32x32x3 upon calling the following function:
```np.transpose(img,(1,2,0))```
* Our batch size is 128, so instead of plotting all 128 images of a batch, we only plot 20 in this case.

<p align='center'>
  <img src="">
</p>

## Scaling images
* It is important to scale the images as the Tanh function has values in the range -1 to 1, so we need to rescale our training images to a range of -1 to 1. (Right now, they are in a range from 0-1.)

## Helper functions — Convolutional & Transpose Convolutional
* To make things easier and simply our code, we will define helper functions for defining our Discriminator & Generator networks.
* The reason for these helper functions? Answer — DRY! 😅

## Discriminator Architecture
* We shall now define our discriminator network. The discriminator as we know is responsible for classifying the images as real or fake. Thus this is a typical classifier network.

## Generator Architecture
* The generator network is responsible for generating fake images that could fool the discriminator network into being classified as real. Over time the generator becomes pretty good in fooling the discriminator.

## Parameter initialization
* We will initialize the weights and biases of our network by sampling random values from a normal distribution. This results in better results. We define a function for the same that takes a layer as an input.
* For weights, I used 0 mean and 0.02 standard deviation.
* For bias, I used 0.
```Now this should be in place replacement so the _(underscore) after the function does the same.```

## Loss functions and optimizer
* We shall make use of Adam optimizer with a learning rate of 0.002. This is as per the original research paper on DCGANs. [You can check it out here](https://arxiv.org/abs/1511.06434).

* We used BCEwithLogitsLoss(), which combines a sigmoid activation function (we want the discriminator to output a value 0–1 indicating whether an image is real or fake) and binary cross-entropy loss.

<p align='center'>
  <img src="">
</p>

## Training phase & Loss curves
* We will define a function for training our model. The parameters would be the Discriminator, Generator, epoch number.

<p align='center'>
  <img src="">
</p>

## Sample generation
* It is important that we rescale the values back to the pixel range(0–255).
* And finally, we have our generated faces below. 👀

<p align='center'>
  <img src="">
</p>

***I HAVE INCLUDED THE .pkl FILE. SO YOU CAN GENERATE THE IMAGES TO SEE HOW IT PERFORMS.****

## Conclusion
* We have seen how to generate street view house numbers with DCGAN implementation on the SVHN dataset. The images generated can be further improved by tuning the hyperparameters. One could also opt for deeper layers than the one here. Doing so would however result in an increased number of parameters which again would take a lot of time to train. Now open your Jupyter Notebook and implement the same. In the next article, I shall walk you through the image-to-image translation with CycleGANs. Cheers!
