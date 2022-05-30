## Binarization

大津法阈值法是由日本学者大津于 1979 年提出的，是一种自适应的阈值确定的方法，又叫大津法, 简称 OTSU。
Otsu 利用最大类间方差法原理计算阈值将原图像分成前景，背景两个部分。

## Image Convolution

Image convolution can be used for many tasks.

Filters with weights distributed according to Gaussian distribution are called Gaussian filters. It can even be proved that Gaussian filter is the only filter that doesn't add any additional information to the image. And they're probably the most used filters in image processing and image recognition.

Gaussian filters have infinite support, but discrete filters use finite kernels. For the same sigma, we can build filters of different sizes. As a general rule of thumb, we usually set Gaussian filter half-width to about three sigma. So the total size of Gaussian filter equals to six sigma.

Applying Gaussian filter can reduce noise in image, but it also blurs the image. The larger the intensity of noise, a larger filter kernel should be used to remove the noise. But the larger the filter, the stronger is the blur. So it's a compromise between smoothing of the image and reducing the additive noise.

To reduce image blur and make edges more pronounced we can apply blurring and subtract blurred image from original image. We can combine all operations into single convolution and approximate it with negative Laplacian of Gaussian.

Sharpening produce visually pleasing results usually. So it's oftenly used in consumer cameras to improve the quality of images. And you can only turn it off if you tried to capture the raw images with no post-processing.

## Image Segmentation

### Level Set Method 弹性水平线法

In image segmentation, the level set method (LSM) re-formulates the parametric active contour into a non-parametric energy minimization problem.
The active contour is embedded as the zero level set of a higher dimensional function, which moves according to the active contour evolution equation and drives its zero level set to the edges of the desired objects.

Signed distance functions (SDFs) or binary functions can be used as the level set function (LSF).

The use of distance function is necessary to estimate accurately geometric features s.a. the curvature or the contour normal, which can be essential for some applications s.a. the surface reconstruction problem from scattered points.

Binary function cannot provide the distance information, but allows fast and convex optimization techniques with graph cut methods or convex relaxation methods.

Level set method pros:

- flexible to adapt to different problems in computer vision and fluid dynamics
- deal with changes of topology (contour breaking and merging) without any extra functions
- guarantee of the existence of solutions in the class of viscosity partial differential equations (PDEs)
- include suitable edge-, region- and shape-based terms in LSF to adapt to different tasks

Important papers:

- 2011 An Efficient Algorithm for Level Set Method Preserving Distance Function
- 2018 Adaptive Eigenspace Segmentation
- 2020 A survey of level set method for image segmentation with intensity inhomogeneity

- 2001 Active contours without edges
- 2007 Fast Global Minimization of the Active Contour/Snake Model
