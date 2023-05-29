# 立体视觉

目前 3D 视觉成像技术主要分 3 种：
1、双目立体成像(Stereo Vision)
2、时间光 TOF（Time of flight）
3、结构光 3D 成像(Structured light 3D imaging)

TOF 典型的应用是微软 Kinect 2 的深度相机。3D 结构光最为人熟知的应用案例是 iPhone X 的面部设别。

![工作原理](https://www.jiajusmart.com/data/attachment/forum/201908/02/150729t64k63aul3ootttq.jpg)

![方案对比](https://img.ithome.com/newsuploadfiles/2019/2/20190217_071045_660.jpg@s_2,w_690,h_388)

结构光方案最为成熟，已经大规模应用于工业 3D 视觉领域。由于投射的经过编码的图像或散斑光点，在室外容易被强自然光淹没，所以结构光方案在室外并不好用。当物体距离相机较远时，物体上投射到的图像或光点越大，精度也越差；它也容易受光滑平面的反光影响，比如投射到镜子上。

双目立体成像方案抗环境光干扰强，分辨率高，但是技术较新不够成熟。

iPhone X 使用的 3D 结构光（或称单目结构光）需搭配高成本的点阵红外线投射器，联发科推出的双目结构光模块使用一般随机纹理（Random Texture）红外线投射器及一般双镜头组装制程，可大幅简化校准流程，提升良率与可量产性，更具成本优势。

单目结构光容易受光照影响，在户外使用时，红外线点阵投射器发出的编码光斑容易被太阳光淹没，造成识别率降低。而双目结构光则有较高的抗环境干扰能力，在各种光线和气候环境下都有很好的使用者体验。

TOF 基本原理是通过连续发射光脉冲（一般为不可见光）到被观测物体上，然后用传感器接收从物体返回的光，通过探测光脉冲的飞行（往返）时间来得到目标物距离。

TOF 法根据调制方法的不同，一般可以分为两种：脉冲调制（Pulsed Modulation）和连续波调制（Continuous Wave Modulation）。

TOF 深度相机对时间测量的精度要求较高，在近距离测量领域，尤其是 1m 范围内，TOF 深度相机的精度与其他深度相机相比还具有较大的差距，这限制它在近距离高精度领域的应用。在测量距离要求比较远的场合（如无人驾驶），TOF 深度相机的测量精度不会随着测量距离的增大而降低，其测量误差在整个测量范围内基本上是固定的，具有非常明显的优势。

ToF 技术的深度相机分辨率目前还偏低，一般也就 320\*240 的水准，功耗上也比较大。

结构光三维视觉是基于光学三角测量原理。光源将一定模式的结构光透射于物体表面，在表面上形成由被测物体表面形状所调制的光条三维图像。该三维图像由处于另一位置的摄像机探测，从而获得光条二维畸变图像。光条的畸变程度取决于光学投射器与摄像机之间的相对位置和物体表面形状轮廓（高度）。当光源与摄像机之间的相对位置一定时，由畸变的二维光条图像坐标便可重现物体表面三维形状轮廓。

根据光源所投射的光束模式的不同，结构光模式又可分为点结构光模式、线结构光模式、多线结构光模式、面结构光模式、相位法等

当采用面结构光时，将二维的结构光图案投射到物体表面上，这样不需要进行扫描就可以实现三维轮廓测量，测量速度很快，光面结构光中最常用的方法是投影光栅条纹到物体表面。当投影的结构光图案比较复杂时，为了确定物体表面点与其图像像素点之间的对应关系，需要对投射的图案进行编码，因而这类方法又称为编码结构光测量法。图案编码分为空域编码和时域编码。空域编码方法只需要一次投射就可获得物体深度图，适合于动态测量，但是目前分辨率和处理速度还无法满足实时三维测量要求，而且对译码要求很高。时域编码需要将多个不同的投射编码图案组合起来解码，这样比较容易实现解码。主要的编码方法有二进制编码、二维网格图案编码、随机图案编码、彩色编码、灰度编码、邻域编码、相位编码以及混合编码。

3D 结构光技术的基本原理是，通过近红外激光器，将具有一定结构特征的光线投射到被拍摄物体上，再由专门的红外摄像头进行采集。这种具备一定结构的光线，会因被摄物体的不同深度区域，而采集不同的图像相位信息，然后通过运算单元将这种结构的变化换算成深度信息，以此来获得三维结构。

Triangulation by R. Hartley and P. Sturm in Computer Vision and Image Understanding vol. 68, no. 2, 1997 presents a formal analysis of different triangulation methods

A flexible new technique for camera calibration article by Z. Zhang in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 22, no 11, 2000, is a classic paper on the problem of camera calibration

A Taxonomy and Evaluation of Dense two-Frame Stereo Correspondence Algorithms by D. Scharstein and R. Szeliski in International Journal of Computer Vision, vol. 47, 2002 is a classic reference on disparity computation methods

Multiple View Geometry in Computer Vision, Cambridge University Press, 2004, R. Hartley and A. Zisserman, is the most complete reference on projective geometry in computer vision

Stereo processing by semiglobal matching and mutual information by H. Hirschmuller in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 30, no 2, pp. 328-341, 2008 describes the approach used for computing the disparity in OpenCV

人眼睛的瞳距一般是 55-75cm, 标准的瞳距, 男性应该在 60.9mm 左右，女性应该在 58.3mm 左右。
看书时眼睛离书最好是 30-40cm。人裸眼的最大分辨率:0.1mm，2169✖1213。
人眼的明视距离为 25cm，视网膜至瞳孔的距离为 22mm 时，因此人眼可分辨明视距处的最小线距离为 0.1mm。
