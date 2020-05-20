# Computer Vision

Computer vision is a key branch of artificial intelligence, aiming at understanding the surrounding environment from the visual information captured by cameras.

Vision is a process of seeing what is where.

Vision can be studied at three different levels: computational theory level, algorithm level and implementation level.

Each computation task is independent of specific algorithms, algorithms can be independent of the software or hardware platform on which they are implemented.

Estimate the values of unknown parameters (robot posture, camera orientation, etc.), given a number of measurements (sensory data, images, feature points, etc.). These kinds of problems are called inverse problem because they involve in estimating unknown model parameters instead of simulating the forward formation equations.

A multiple view problem is inherently a vision problem involving more than one view of the same scene.

Many of the visual problems are generally ill-posed, that is, solutions are not unique.

## Camera Model

Vision system starts its work by acquiring an image or a set of images from cameras or data storage devices.

The pinhole perspective (also called central perspective) projection model, first proposed by Brunelleschi at the beginning of the fifteenth century, is mathematically convenient and, despite its simplicity, it often provides an acceptable approximation of the imaging process.

A thin lens produces the same projection as the pinhole. A camera is modeled as a pinhole, which performs a perspective projection. The perspective projection is a nonlinear mapping.

A 2D point is denoted by $m = [x,y]^T$ in pixel image coordinates. A 3D point is denoted by $M = [X,Y,Z]^T$ in world coordinates. We use $\tilde x$ to denote the augmented vector by adding 1 as the last element: $\tilde m = [x,y,1]^T$ and $\tilde M= [X,Y,Z,1]^T$.

![](images/pinhole_camera_model.png)

### Camera matrix 相机内参矩阵，相机外参矩阵

The relationship between a 3D point M and its image projection m is given by
$$ s\tilde m = K [R\ t] \tilde M $$

where $s$ is an arbitrary scale factor, $(R, t)$, called the extrinsic parameters, is the rotation and translation which relates the world coordinate system to the camera coordinate system, and A is the camera intrinsic matrix, is given by

$$
K=\begin{bmatrix}
   f_x & 0 & c_x  \\
   0 & f_y & c_y  \\
   0 & 0 & 1
\end{bmatrix}
$$

with $(c_x,c_y)$ the coordinates of the principal point that is usually at the image center, $(f_x,f_y)$ the focal lengths in image x and y axes expressed in pixel units.

It is difficult to manufacture a perfect lens. In practice, several simple lenses are carefully assembled to make a compound lens with better properties. The two planes of front and back lens, called the principal planes, are perpendicular to the optical axis, and are separated by a distance t, called the thickness of the lens. The principal planes intersect the optical axis at two points, called the nodal points.

The thick lens produces the same perspective projection as the ideal thin lens, except for an additional offset equal to the lens thickness t along the optical axis.

影像坐标系是以二维影像为基本建立的坐标系，描述像素点在影像上的位置，分为以像素为单位的 uv 坐标系以及以物理尺寸为单位的 xy 坐标系。uv 坐标系以图像左上角为原点，u 轴和 v 轴分别平行于图像平面的两条垂直边（u 轴朝右，v 轴朝下）；xy 坐标系以相机主光轴与像平面的交点（主点）为原点，x 轴和 y 轴分别与 u 轴和 v 轴平行且方向一致。
相机坐标系从相机的视角来描述物体在三维空间中的坐标。以相机中心为原点，X 轴与 Y 轴分别与影像坐标系的 x 轴与 y 轴平行，且方向一致，根据右手坐标系规则得到 Z 方向。相机坐标系是物理尺寸单位。

## Camera Calibration

Accurate calibration is of key importance for performance most machine and computer vision tasks.

Camera calibration is a necessary step in 3D computer vision in order to extract metric information from 2D images.

Camera calibration is the process of estimating the intrinsic and extrinsic parameters of a camera.

In applications based on triangulation, such as stereo vision or structure light vision, the over all performance of the machine vision system strongly depends on the accuracy of the camera calibration.

Main factors that influence the calibration accuracy:

- the extraction of feature points in the image plane
- the geometric accuracy of the calibration target
- the lens distortion model conformity with the actual lens
- the optimization algorithms used to converge on the camera parameters
- the operational conditions of the experiments

Generally, camera calibration methods can be classified into two categories: self-calibration and object-based calibration.

Self-calibration estimates the camera’s parameters by using multi-view images without calibration targets. As such, it is the appropriate solution for on-line implementation in which accuracy is not highly demanded.

The object-based camera calibration is performed by employing an object, such as 3D object, 2D pattern or 1D pattern with known coordinates, which is commonly used in off-line calibration for highperformance applications.

### Homography matrix 单应矩阵

We assume the plane of a calibration board is on $Z = 0$ of the world coordinate system. We have

$ \tilde m = H \tilde M $ with $ H = λA [r_1\ r_2\ t]$, $m = [x,y]^T$, $\tilde M= [X,Y,1]^T$.

The 3×3 matrix $H$ is defined up to a scale factor, called homography matrix.

Let $h = [\bar h_1^T\ \bar h_2^T\ \bar h_3^T]^T$, $\bar h_i$ is the i-th row of H. Then

$$
\begin{bmatrix}
   \tilde M^T & 0^T & -x\tilde M^T \\
   0^T & \tilde M^T & -y\tilde M^T
\end{bmatrix}h=0
$$

When we are given n points, we have n above equations, which can be written in matrix equation as $Lh = 0$, where L is a 2n×9 matrix. As h is defined up to a scale factor, the solution is well known to be the right singular vector of L associated with the smallest singular value (or equivalently, the eigenvector of $L^TL$ associated with the smallest eigenvalue).

Using the knowledge that $r_1$ and $r_2$ are orthonormal, we have

$$
\begin{gathered}
h_1^TA^{-T}A^{-1}h_2 = 0 \\
h_1^TA^{-T}A^{-1}h_1 = h_2^TA^{-T}A^{-1}h_2
\end{gathered}
$$

Let

$$
B = \begin{bmatrix}
   B_{11} & B_{12} & B_{13}  \\
   B_{21} & B_{22} & B_{23}  \\
   B_{31} & B_{32} & B_{33}
\end{bmatrix} = λA^{-T}A^{-1} = λ\begin{bmatrix}
   \dfrac{1}{f_x^2} & 0 & -\dfrac{c_x}{f_x^2}  \\
   0 & \dfrac{1}{f_y^2} & -\dfrac{c_y}{f_y^2}  \\ \\
   -\dfrac{c_x}{f_x^2} & -\dfrac{c_y}{f_y^2} & (\dfrac{c_x}{f_x^2}+\dfrac{c_y}{f_y^2}+1)
\end{bmatrix}
$$

Note that B is symmetric, defined by a 6D vector
$$b = [B_{11},B_{12},B_{22},B_{13},B_{23},B_{33}]^T.$$

Let $H=[h_1\ h_2\ h_3]$, $h_i$ is the i-th column vector of H. Then

$$
h_i^TBh_j = v_{ij}^Tb
$$

with

$$
v_{ij}=[h_{i1}h_{j1},h_{i1}h_{j2}+h_{i2}h_{j1},h_{i2}h_{j2},h_{i3}h_{j1}+h_{i1}h_{j3},h_{i3}h_{j2}+h_{i2}h_{j3},h_{i3}h_{j3}]^T.
$$

Therefore, the two fundamental constraints from a given homography, can be rewritten as 2 homogeneous equations in b:

$$
\begin{bmatrix}
   v_{12}^T \\
   (v_{11}-v_{22})^T
\end{bmatrix}b=0
$$

If n images of the model plane are observed, by stacking n such equations we have

$$
Vb=0
$$

where V is a 2n×6 matrix. The solution is well known as the eigenvector of $V^TV$ associated with the smallest eigenvalue (equivalently, the right singular vector of V associated with the smallest singular value).

Once $b$ is estimated, we can compute all camera intrinsic matrix A.

$$
\begin{gathered}
f_x = \sqrt{\frac{λ}{B_{11}}} \\
f_y = \sqrt{\frac{λB_{11}}{B_{11}B_{22}-B_{12}^2}} \\
c_x = \frac{B_{13}}{B_{11}} \\
c_y = \frac{B_{12}B_{13}-B_{11}B_{23}}{B_{11}B_{22}-B_{12}^2} \\
λ = B_{33}- \frac{B_{13}^2+c_y(B_{12}B_{13}-B_{11}B_{23})}{B_{11}} \\
\end{gathered}
$$

Once A is known, the extrinsic parameters for each image is readily computed.

$$
\begin{gathered}
r_1 = λA^{-1}h_1 \\
r_2 = λA^{-1}h_2 \\
r_3 = r_1 \times r_2 \\
t = λA^{-1}h_3 \\
λ = \frac{1}{|A^{-1}h_1|} = \frac{1}{|A^{-1}h_2|}
\end{gathered}
$$

Because of noise in data, the so-computed matrix $R = [r_1\ r_2\ r_3]$ does not in general satisfy the properties of a rotation matrix. We need to estimate the best rotation matrix from a general 3×3 matrix.

## Lens distortion model

The centre-of-distortion may be displaced from the centre of the image or the principal point of the camera.

## Calibration Target

In principle, any appropriately characterized object could be used as a calibration object.

Circle targets can provide improved calibration quality due to a higher feature density. In contrast to the saddle points in checkerboards, circles are imaged as ellipses under camera perspective.

However, symmetric circle grids are not rotationally invariant, and hence not suitable for stereo calibration. In these cases, checkerboard or asymmetric circle grids can be used.
In order for the checkerboard targets to be rotation-invariant, the number of rows needs to be even and the number of columns odd, or the other way around.

Generally, the target should fill most of your camera's FOV (Field Of View) at the desired working distance. This is because cameras need to be focused on that specific distance and calibrated.
Changing the focus distance slightly affects focal length, which would throw any previous calibration off. Even aperture changes usually have a negative effect on calibration validity, which is why they should be avoided.

For accurate calibration, the camera model is best constrained if the camera sees the calibration target filling most of the image. Popularity speaking, if a small calibration plate is used, many combinations of camera parameters could explain the observed images.
As a rule of thumb, the calibration plate should have an area of at least half the available pixel area when observed frontally.
Capturing calibration information from the periphery of images is especially important for the determination of lens distortion parameters.

#### Calibration Best Practices

- Proper mounting of calibration target and camera.
- Perform calibration at the approximate working distance (WD) of your final application.
- Choose the right size calibration target.
- The target should have a high feature count. Using fine patterns is preferable.
- Collect images from different areas and tilts.
- Use good lighting. This is often overlooked, but hugely important.
- Have enough observations. Remove bad observations.
- Calibration is only as accurate as the calibration target used.

## Stereo Vision

Binocular stereo is a problem to determine the 3D shape of visible surfaces in a static scene from images taken of the same scene by two cameras.

The first step is to match the points in the two images, so that one can then determine the 3D position of each point by triangulation.

For any two views, they share the common epipolar constraint, which is the only geometrical constraint available.

A 3-D point P is projected onto both image planes, to points $p_l$ and $p_r$, which constitute a conjugate pair. Given a point $p_l$ in the left image plane, its conjugate point $p_r$ in the right image is constrained to lie on a line called the epipolar line. This is called the epipolar constraint.

The line connecting the lens centers of the two cameras, called baseline.

All the epipolar lines in one image plane pass through a common point ($e_l$ and $e_r$ respectively) called the epipole, which is the projection of the optical center of the other camera.

The epipolar plane is defined by the observed point P and the two centers of projection, $O_l$ and $O_r$; the epipoles are located at the point of intersection of the line joining the centers of projection and the two projective planes.

![](./images/epipolar_plane.png)

A very special case is when both epipoles are at infinityy, that happens when both image planes are parallel to the baseline. Epipolar lines, then, form a bundle of parallel lines in both images.

If you have a stereo camera where the relative position and orientation of two cameras is fixed, and if you computed poses of an object relative to the first camera and to the second camera, ($R_1$, $T_1$) and ($R_2$, $T_2$), respectively.

For the same object point M, its coordinates is $M_1$ and $M_2$ in each camera coordinates, we have

$$
\begin{gathered}
s_1\tilde m_1 = A_1 M_1 = A_1 [R_1\ T_1] \tilde M \\
s_2\tilde m_2 = A_2 M_2 = A_2 [R_2\ T_2] \tilde M \\
M_2 = R M_1 + T
\end{gathered}
$$

So given ($R_1$, $T_1$), if you know (R,T) the orientation and position of the second camera relative to the first camera, it is possible to compute ($R_2$, $T_2$):

$$
\begin{gathered}
R_2=R∗R_1 \\
T_2=R∗T_1+T
\end{gathered}
$$

From the coplanar constraint,

$$
\begin{gathered}
M_2 \cdot (T \times RM_1) = 0 \\
M_2^T E M_1 = 0
\end{gathered}
$$

### Essential matrix 本质矩阵

The essential matrix E is determined by the rotation $R$ and translation $T=[t_1,t_2,t_3]^T$ between the two cameras.

$$
E=T \times R=\begin{bmatrix}
   0 & -t_3 & t_2  \\
   t_3 & 0 & -t_1  \\
   -t_2 & t_1 & 0
\end{bmatrix}R
$$

Alternatively, $(R^T M_2)^T\cdot(T\times M_1)=0 \implies E = R \begin{bmatrix}
   0 & -t_3 & t_2  \\
   t_3 & 0 & -t_1  \\
   -t_2 & t_1 & 0
\end{bmatrix}.$

Then in image coordinates,

$$
\begin{gathered}
\tilde m_2^TA_2^{-T}EA_1^{-1}\tilde m_1=0 \\
F = A_2^{-T}EA_1^{-1} \\
E = A_2^TFA_1
\end{gathered}
$$

### Fundamental matrix 基础矩阵

The fundamental matrix F is a matrix determined from point correspondences between two images, it has determinant 0 with rank 2. We can compute F in a manner analogous to computing the image homography in the previous section, by providing a number of known correspondences.

To recover the epipolar geometry between two images from point matches, least-squares techniques are exploited to obtain more robust estimate.

$$\tilde m_2^TF\tilde m_1=0$$

For fixed $\tilde m_1$, $F\tilde m_1$ defines a line in the other imageplane, called the epipolar line of point $\tilde m_1$, vice versa. This implies that one point of a corresponding pair is on the epipolar line of the other point, therefore point correspondence detection reduces to search on the epipolar line.

The fundamental matrix cannot be uniquely determined if the corresponding points are exactly coplanar in the scene or exactly have a special symmetry, for example, at the vertices of a cube, This does not occur for real data with noise.

The essential matrix is the specialization of the fundamental matrix to the case of normalized image coordinates. Reversely, the fundamental matrix may be thought of as the generalization of the essential matrix in which the assumption of calibrated cameras is removed.

## Stereo Calibration

Stereo calibration determines the relative geometry (rotation and translation) between cameras. The intrinsic parameters of each camera can be determined separately as in camera calibration or jointly with the relative geometry.

Stereo calibration involves finding the rotation matrix R and translation vector T between the two cameras.

We can separately use single-camera calibration for the two cameras to obtain ($R_1$, $T_1$) and ($R_2$, $T_2$), then

$$
\begin{gathered}
R=R_2∗R_1^T \\
T=T_2 - R∗T_1
\end{gathered}
$$

A robust Levenberg-Marquardt iterative algorithm to find the (local) minimum of the reprojection error of the calibration points for both camera views, and the final solution for R and T is returned.

It was observed that correcting lens distortion while estimating internal camera parameters can lead to detrimental numerical compensations, where the apparence of an observed pattern can be explained by distortion or by change of point of view.

By using acalibration harp, photographs of this harp allow measuring the residual distortion after correction.

## Scene Reconstruction

Given two images of the same scene, we can compute the 3D position of the point determined by a corresponding pair of points if the positions, orientations, and internal parameters of the two cameras that took the images are known.

We determine from a corresponding point pair the triangle made by two lines of sight and the baseline. For the first camera, the ray is the line passing through the viewpoint and the point (x, y) on the image, determined by solving the first two equations. Similarly, the ray for the second camera is obtained by solving the last two equations up to one free parameter.

The epipolar equation is the necessary and sufficient condition that the two rays intersect, and the fundamental matrix F is determined by the projection matrices P and P'.

Ambiguous correspondence between points in the two images may lead to several different consistent interpretations of the scene.

![](images/ambiguous_correspondence.jpeg)

#### rectification of stereo pairs

Any pair of stereo images, can be transformed so that epipolar lines are parallel and horizontal in each image. This procedure is called rectification.

The rectified images can be thought of as acquired by a new stereo rig, obtained by rotating the original cameras. The important advantage of rectification is that computing stereo correspondences (Dhond and Aggarwal, 1989) is made simpler, because search is done along the horizontal lines of the rectified images.

Dense stereo matching is greatly simplified if images are rectified.

### Three‐dimensional Reconstruction from Image Sequences with the Kalman Filter

![](images/stereo_vision_uncertainty.png)

A model of uncertainty sources needs to be introduced in order to have a reasonable algorithm. Such inference problems from noisy data are called probabilistic inference.

Maximum Likelihood Estimator (MLE)
standard Kalman filter (SKF)
extended Kalman filter (EKF)
unscented Kalman filter (UKF) 无迹卡尔曼滤波器

## Visual Odometry

In most of the industrial cases, one needs to obtain measurements from a vision system that are expressed in real-world coordinates. This requires transforming pixel measures into metric values.
