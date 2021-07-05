Image convolution can be used for many tasks.

Filters with weights distributed according to Gaussian distribution are called Gaussian filters. It can even be proved that Gaussian filter is the only filter that doesn't add any additional information to the image. And they're probably the most used filters in image processing and image recognition.

Gaussian filters have infinite support, but discrete filters use finite kernels. For the same sigma, we can build filters of different sizes. As a general rule of thumb, we usually set Gaussian filter half-width to about three sigma. So the total size of Gaussian filter equals to six sigma.

Applying Gaussian filter can reduce noise in image, but it also blurs the image. The larger the intensity of noise, a larger filter kernel should be used to remove the noise. But the larger the filter, the stronger is the blur. So it's a compromise between smoothing of the image and reducing the additive noise.

To reduce image blur and make edges more pronounced we can apply blurring and subtract blurred image from original image. We can combine all operations into single convolution and approximate it with negative Laplacian of Gaussian.

Sharpening produce visually pleasing results usually. So it's oftenly used in consumer cameras to improve the quality of images. And you can only turn it off if you tried to capture the raw images with no post-processing.
