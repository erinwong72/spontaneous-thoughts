# Separable convolutions
Source: [A Basic Introduction to Separable Convolutions | by Chi-Feng Wang | Towards Data Science](https://towardsdatascience.com/a-basic-introduction-to-separable-convolutions-b99ec3102728)

The key to implementing them (and the reason) is to *reduce* computational complexity.

Two types:
1. Spatial separable convolutions
2. Depthwise separable convolutions

## Spatial separable convolutions
This method deals mainly with width and height of the input, not really doing anything about the depth (number of channels). One 3x3 kernel can be separated into two 1x3 and 3x1 kernels that, when multiplied together, make up the original kernel. Convolutions can then be done to each separately, reducing the number of multiplications.

![[Pasted image 20230731204635.png|475]]

The problem is that not every kernel can be separated in this way, into two smaller kernels, so this method only works for a small portion of the kernels processed by the network.

## Depthwise separable convolutions
The concept is similar—separating into two smaller kernels and performing convolutions on those first, except this time, depth is also considered (# of channels).

Two kernels get two different types of convolutions:
1. Depthwise covolution
2. Pointwise convolution

### Depthwise convolution
The kernel used will be 1 channel deep, and will be passed over the input image as usual. n number of kernels will be used for n channels and each kernel will filter over **one** channel of the image.

After this, the outputs are stacked to get a smaller (width and height-wise) but same depth image.

![[Pasted image 20230731205429.png|500]]

### Pointwise convolution
A new set of kernels will be used (say p), this time 1x1xn where n is the number of channels, so it basically filters over every pixel, across all n channels. After, stack to get the same size as the input (from the depthwise convolution) except there will now be p channels as each kernel, after filtering, returns an image with a depth of 1.

![[Pasted image 20230731210140.png|500]]

Essentially, this separation of convolutions reduces the number of times you have to transform the image. With normal convolution, if you want 256 channels, you would create 256 kernels, thus transforming 256 times. However, with depthwise convolution, you’re really only transforming the image once, by applying one kernel to each channel. And then with pointwise convolution, you’re not really transforming the image, you’re just extending/elongating it?