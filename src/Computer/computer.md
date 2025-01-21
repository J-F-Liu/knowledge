# 电脑

电脑的本质是信息处理。
信息处理的基本单元是文件。

文件是字节的序列，序列的长度就是文件的大小。
文件系统以目录树的形式组织文件，每个文件和目录都有名称、访问权限、最近修改时间等属性。
根据目录层次，每个文件和目录都有一个由名称和路径分隔符组成的唯一的路径。

查看目录的三个基本命令：

```
pwd 显示当前工作目录
ls  列出当前目录中的文件和子目录
cd PATH 改变当前工作目录，PATH参数可以是绝对路径或相对路径
```

文件名一般由两个部分组成，以“.”分隔，“.”之后的叫做文件的扩展名，用来表示文件的类型。
常见的文件扩展名有：

```
txt 文本文件
html 网页文件
md  Markdown文件
pdf PDF文件
doc,docx Word文档
bmp,gif,jpg,png,svg 图片文件
wav,mp3,acc,ape 音频文件
avi,mp4,mkv 视频文件
zip,rar,7z 压缩文件
exe,dll 可执行文件
```

"Not having to think about it" is certainly a measure of success for a given technology.

# 计算机架构

计算机由软件和硬件两部分构成，由于编写软硬件所用的语言有本质上的不同，它们之间的交互必须依赖于指令集架构（ISA），例如大家熟知的 x86 和 ARM。简单来说，指令集规定了软硬件之间的沟通规范（语言），依照相同指令集编写的软件，可以在任何支持该指令集的硬件上工作。这大大提升了计算机软硬件之间的兼容性，降低了整体成本。

直接针对指令集，也即用编汇语言编写程序时比较低效的，发明了编译器之后，人们可以高级语言(抽象层次更高的程序语言)编译成编汇指令，而且高级语言可以被编译适配到多种指令集架构。

在 20 世纪 70 年代，包括英特尔 8080 在内的主流微处理器仍然处于 8 位时代，主要依靠编汇语言编写程序，通过添加新的指令互相竞争。摩尔定律让内存和控制储存器变得更大，这也意味着更复杂的指令集。控制储存器包含一个用微指令写成的指令集翻译器，在执行一条传统指令时，只需要将一系列微指令组合起来。

20 世纪 80 年代初，人们发现连 Unix 这样的操作系统都可以使用高级语言编写，一旦普及了高级语言，要提高编程的效率就没必要增加指令集的复杂度，反而是使用更简单的指令架构集能够提高程序的运行速度。相比使用复杂指令集的计算机（CISC），精简指令集架构(RISC)的指令通常和微指令一样简单，因此不再需要微代码解释器，而这些解释器占用的内存可以被 RISC 当成高速缓存使用。

几十年来，新的 CISC 指令集都没有出现，而 RISC 已经成为了通用处理器的最佳指令集架构。

受到开源软件的启发，想要创造处理器领域的 Linux 系统，整个行业需要开放式的指令集架构，如果有很多人开始使用相同的开源指令集架构开发处理器，那么这种竞争就会进一步推动创新。最有名的开源例子是 RISC-V，由加州大学伯克利分校开发。它是一个支持 32 位和 64 位的模块化指令集，开发者可以根据需求选择扩展包，增加或删减增强功能。在 RISC-V 基金会的维护下，整个社区正在不断改进架构。

软件创新可以启发架构发展；提升软硬件接口会带来创新机会；市场最终会解决架构之争。

可编程的核心就是布尔运算及其相应的流程控制（Control Flow）。

In a computer, the processor can read and write information from and to random access memory (RAM). RAM gives the processor much more space to organise the intermediate results of computations. Temporary placeholders for information are called variables and are stored in memory. In a computer, it is a trivial operation to form a variable that holds a numerical value. And it is also simple to make data structures – variables in memory that contain links that can be followed to get to other variables. One of the simplest data structures is a list – a sequence of variables that can be read item by item. For example, one could store a list of players’ names on a sports team and then read each name one by one. A more complicated data structure is a tree. In a family tree for instance, links from children to parents can be followed to read out a line of ancestry. One of the most complex and general data structures is a graph, like the London Underground network.

## SIMD Instruction Sets on x86 CPUs

1997 Pentium MMX
2000 SSE2
2011 AVX, 256 bits registers
2016 AVX2, new instructions
AVX512, 512 bits registers

## 显示器

- VSync (vertical synchronization)
  GPU only changes the image data it’s sending in the so-called vertical blanking interval (vblank), which is the time between the bottom right and top left pixel.
  Applications synchronize their rendering to the display where possible - they only render one frame for every time the display updates.

- Variable Refresh Rate (VRR) or Adaptive Sync
  its two implementations are FreeSync (from AMD) and GSync (from NVidia).
  With VSync it’s always the GPU which has to adjust to the display, but with Adaptive Sync the roles are partly reversed: the GPU can tell the display to make vblank longer.
  Whenever an application is slower than the displays maximum refresh rate the display will wait for the next frame before it updates the pixels and thus you don’t see any stutter, without introducing tearing. Additionally it has very low latency in that state because every frame is displayed right when the game is finished rendering it.

## 文件系统

A file system is a clearly-defined method that the computer's operating system uses to store, catalog, and retrieve files. Files are central to everything we use a computer for: all applications, images, movies, and documents are files, and they all need to be stored somewhere.

File systems need to keep track of not only the bits that make up the file itself and where they are logically placed on the hard drive, but also store information about the file. The most important thing it has to store is the file's name. Also, the file system has to know how to organize files in a hierarchy. This hierarchy is usually called a directory. The last thing the file system has to worry about is metadata. Examples of metadata are file's modification date, attributes, such as hidden or read-only, file permissions.

One of the biggest advances in file systems has been the addition of journaling, which keeps a log of changes that the computer is about to make to each file. This means that if the computer crashes or the power goes out halfway through the file operation, it will be able to check the log and either finish or abandon the operation quickly without corrupting the file. This makes restarting the computer much faster, as the operating system doesn't have to scan the entire file system to find out if anything is out of sync.

Gary Kildall invented CP/M file system in 1973. It stored files in a completely flat hierarchy with no directories. File names were limited to eight characters plus a three-character "extension" that determined the file's type.

In MS-DOS 2.0, FAT-12 has nested directories, labeled with the backslash \ as the separator.

FAT-16 2GB maximum disk size
FAT-32 8TB (terabyte) limit, file name up to 255 characters

Year 1984, Macintosh File System, or MFS, and had a limit of 20MB and 4,096 files. File names could be 63 characters long.

MFS was replaced in 1985 by a system with proper hierarchical directories, called the Hierarchal File System, or HFS. File names were now limited to 31 characters, which was just short enough to be annoying.

The Unix File System (UFS), also known as the Berkeley Fast File System, file name is case-sensitive. Supports block suballocation where partially-filled blocks from several files could be stored in a single block.

ext2 was "inspired" by the UFS design, and used in Linux operating system.

ReiserFS added not only journaling, but attempted to improve on many other aspects of ext2. B-Tree indexing and advanced block suballocation routines sped up the file system significantly, particularly when dealing with small files on the order of 1KB.

XFS has been optimized for speed and reliability, winning many speed comparison tests. It uses extents and has many advanced features such as being optimized for multithreading—multiple threads can operate on the same file system simultaneously. In 2000 SGI released the XFS source code under the GNU Public license.

NTFS was an all-out, balls-to-the-wall implementation of all the best ideas in file systems that Cutler's team could think of. NTFS stores all of its metadata information in separate files, hidden from the regular operations of the OS by having filenames that start with the \$ character. The only thing anyone could really find to complain about NTFS was that its design was a proprietary secret owned by Microsoft.

Macintosh OS X 10.0, released in 2001. For the first release of OS X, the user was asked to choose between UFS and HFS+ when installing the OS on a new hard drive partition. For compatibility reasons, however, HFS+ was chosen as the default. UFS support was finally dropped in Leopard, the latest version of OS X.

Sun's ZFS - Zettabyte File System, announced in 2004, ZFS builds on top of virtual storage pools called zpools, so all connected drives appear to be part of a single gigantic partition. ZFS automatically take snapshots of every single change made to a file, saving only the differences, so no data can ever be lost.

TFS was created out of the need for a modern file system for Redox OS, as a replacement for ZFS, which proved to be slow to implement because of its monolithic design. TFS is inspired by the ideas behind ZFS, but at the same time it aims to be modular and easier to implement.

FAT still haunts us to this day, as most flash drives are formatted with FAT32. Because as one of the oldest file systems available, it is also the most understood and easiest to implement.

## 鼠标

1999 年 4 月，微软发布第一代光学鼠标，通过光学影像的位移来定位，促成了鼠标的升级换代。此前人们使用的都是机械鼠标，里面是一个橡胶球，通过滚动带动三个滚轮来定位，它的最大缺点就是定位不精确，而且需要经常清洗，防止污垢影响精确度。早期的光学鼠标不能在玻璃和光滑表面使用。

2009 年 8 月，罗技公司推出了会发射出两束激光的鼠标，这能使得它可以在玻璃上使用。

## 固态硬盘，solid state drives，缩写 SSD

速度快，轻巧，没有运动的部件，耐磁场和震动，容量价格比随时间在攀升。

SSD 基于 NAND 闪存构建，NAND 是非与门，闪存在断电后仍能保持数据。NAND 闪存在写入数据单元时需要先擦除原有的内容，擦除和写入都通过施加电压来实现，这会造成 NAND 中绝缘的部分产生磨损。因此 SSD 是有写入次数限制的。

SSD 使用的 NAND 单元有 4 种类型：

1. SLC (Single Level Cell) — 1 比特每单元
2. MLC (Multi-Level Cell) — 2 比特每单元
3. TLC (Triple Level Cell) — 3 比特每单元
4. QLC (Quad Level Cell) — 4 比特每单元

每个单元存储的比特数越大，受擦写引起的磨损的影响也越大，可写入次数就越小。所以 QLC 用于写入次数少，而读取频繁的场景。制造商也会相应地把 SSD 标记为写入型、读取型和混合型。

SSD 接近用坏时的可能的信号有：

- 出现硬盘坏块，读写文件用时很长且没有成功
- 无法读写文件，系统发现坏区后拒绝读取或写入
- 系统提示文件系统需要修理，且不是非正常关机造成的
- 开机启动过程中死机或崩溃，尽快把数据备份出来
- 硬盘变成只读状态，不能写入数据，好在数据没丢

SATA Ⅲ 标准，理论最高速度为 6Gbps。大部分基于 SATA 接口的固态硬盘的读取性能正常会在 500MB/S 以上。
M.2 接口本质为 PCIe 插槽，支持 NVMe 协议，走 PCIe 通道的 M.2 接口会比不走 PCIe 的 M.2 接口快。
浦科特（PLEXTOR）M9PeG 256G M.2 NVMe 固态硬盘读取速度可达 3200MB/s，写入速度 也达到 2000MB/s。

NVMe 是一种建立在 M.2 接口上的传输协议规范，采用是 PCI-E 传输通道，是专门针对闪存存储产品针对的传输协议，它并不是传输接口。

PCIe3.0 满速盘，读写一般在3000~3600MB/s；
PCIe4.0 基本上在5100~7200MB/s之间
PCIe5.0 顺序读取速度高达13545MB/s，顺序写入速度8305.14MB/s；4K随机读取速度76.54MB/s，写入速度123.91MB/s

## 显示器分辨率

720p: 1280 x 720, 称为 HD（中文译为"高清"）
1080p: 1920 x 1080, 称为 FULL HD（中文称为全高清）
1440p: 2560 x 1440, 称为 QHD 或 Quad HD，即 4 倍的 HD
2160p: 3840 x 2160, 称为 4K
4320p: 7680 x 4320, 称为 8K

OSD 菜单：OSD 是 on-screen display 的简称，即屏幕菜单式调节方式。

## USB - Universal Serial Bus

1996 USB 1.0 was released, transfer rate is 1.5Mbps
1998 USB 1.1 12Mbps, Full Speed (全速)
2000 USB 2.0 480 mbps, High Speed (高速)
2010 USB 3.0 5.0 Gbps (500 MB/s), Super Speed (超速), two-way data transfer mode
2013 USB 3.1 Gen1 5Gbps, Gen2 10 Gbps
2014 USB Type-C connector
2017 USB 3.2 Gen1 5Gbps, Gen2 10 Gbps，Gen2x2 20 Gbps
2020 USB 4.0 40Gbs, Power supply will reach 100W, only operate over the Type-C connector, allows tunneling of DisplayPort and PCI Express, support PCIE devices — such as external graphics cards, external displays
USB4 v2.0 80Gbps
2021 USB-C 2.1 support 240W of power

## WiFi

1999 802.11b 2.4GHz 11Mbps
1999 802.11a 5GHz 54Mbps
2003 802.11g 2.4GHz 54Mbps
2009 WiFi 4 (802.11n) 2.4GHz 288Mbps，5GHz 600Mbps，双频双天线，MIMO
2014 WiFi 5 (802.11ac) 5GHz 433 to 6933 Mbps，20MHz 频道，阵列天线
2019 WiFi 6 (802.11ax)，2.4/5 GHz，160MHz 频道, 600 to 9608 Mbps
2020 WiFi 6E (802.11ax), 6GHz, 600 to 9608 Mbps，1024-QAM 信号调制，MU-MIMO
2022 Wi-Fi 7 (802.11be)，2.4GHz、5GHz 和 6GHz，30Gbps，4096-QAM 信号调制，CMU-MIMO

工作频率越高，传输的能量就越大，所以在同一时间传送的数据也越多，上网速度越快。但同时，工作频率越高，穿透性越差，通讯距离短，抗干扰能力更好。

2G 基站覆盖半径约为 5-10 公里
3G 基站覆盖半径约为 2-5 公里
4G 基站覆盖半径约为 1-3 公里
5G 基站覆盖半径约为 100-300 米

# 视频格式

1988 年 MPEG(Moving Picture Experts Group)活动图像专家组成立。

1992 年底，MPEG-1 正式被批准成为国际标准。MPEG-1 音频分三代，其中最著名的第三代协议被称为 MPEG-1 Layer 3，简称 MP3。MPEG－1 曾经是 VCD 的主要压缩标准，针对 SIF 标准分辨率(对于 NTSC 制为 352X240；对于 PAL 制为 352X288)的图像进行压缩，传输速率为 1.5Mbits/sec，每秒播放 30 帧，具有 CD(指激光唱盘)音质，质量级别基本与 VHS 相当。

1994 年，MPEG-2 制定，NTSC 制式下的分辨率可达 720X486，传输率在 3-10Mbits/sec 间，已能适用于 HDTV。H.262 在技术内容上和 MPEG-2 视频标准一致。

1999 年初 MPEG4 正式成为国际标准。与 MPEG1 和 MPEG2 相比，MPEG4 更加注重多媒体系统的交互性和灵活性。分辨率可从 320×240 到 1280×1024，压缩率高且成像清晰。一般来说，一小时的影像可以被压缩为 350M 左右的数据，而一部高清晰度的 DVD 电影,可以压缩成两张甚至一张 650M CD 光碟来存储。

2003 年 3 月 由 ITU-T 视频编码专家组（VCEG）和 ISO/IEC 动态图像专家组（MPEG）联合组成的联合视频组（JVT，Joint Video Team）正式发布 H.264，又称 MPEG-4 AVC、MPEG-4 Part 10。在同等图像质量下，采用 H.264 技术压缩后的数据量只有 MPEG2 的 1/8，MPEG4 的 1/3。

2013 年 2 月 国际电联(ITU)就正式批准通过了 HEVC/H.265 标准。H.265 仅需原先的一半带宽即可播放相同质量的视频。H.265 标准也同时支持 4K（4096×2160）和 8K（8192×4320）超高清视频。H.264 可以低于 1Mbps 的速度实现标清数字图像传送；H.265 则可以实现利用 1~2Mbps 的传输速度传送 720P（分辨率 1280\*720）普通高清音视频传送。

2013 年 6 月 Google 正式推出 VP9 编码标准，实际效率与 HEVC/H.265 接近。但是行业中绝大多数企业不愿意让这么重要的国际标准被一个独立的公司（谷歌）所控制。

2015 年 9 月 Alliance for Open Media（AOM）的组织成立。采用会员制度，创始成员包括：亚马逊、ARM、思科、Facebook、谷歌、IBM、英特尔、微软等。

2017 年 3 月 AOM 发布全新的视频编码标准——AV1，无需专利费，且没有被垄断风险。AV1 的代码主要来自于谷歌的 VP10，是一个免费、开源的视频编解码器。AV1 的目标是在 VP9/HEVC 上基础上提高约 30%的编码效率。

2018 年 1 月 苹果加入了 AOM。

## 视频编码

HEVC (High-Efficiency Video Codec)，也就是 H.265，支持 8K，支持 HDR，支持广色域，支持最高 16bit 的色彩深度，最高 YUV444 的色彩抽样。

2015 年，苹果的 iPhone6s 在 A9 芯片内首次实现了 HEVC 硬解能力，同年，Intel 在第六代 Skylake 的 HD500 系列核显上，NVIDIA 在 GTX900 系列独显上，也先后支持了 HEVC 硬解。

在 2017 年发布的 iOS11, macOS 10.13 上，苹果继续完成了其 VideoToolbox 编解码框架对 HEVC 编解码能力的支持，微软也发布了 HEVC Video Extension 作为 Windows PC 环境 HEVC 解码的能力对标。从此 HEVC 成为苹果，安卓默认视频格式，成为绝大多数单反 / 无人机 / 摄像设备的主推格式。

2022 年，字节跳动工程师和 Intel 工程师合作，为 Chrome 浏览器加上 HEVC 支持，调用系统的硬解能力，发布在 Chrome 107。

H.265 being 50% more efficient than the prevailing H.264.

AV1 (AOMedia Video 1)，2018 年发布，

AV1 beats HEVC by a significant 28% in terms of encoding and decoding efficiency.
AV1 can save up to 30% file size than HEVC for the same image quality.
AV1 can sustain high-quality output from low to high data rates when it comes to UHD 4K formats, both codecs are equally as good.

AV1 is royalty-free while HEVC is royalty bearing.

Compared to HEVC, AV1 is still relatively new hence it suffers limited hardware support.
HEVC is supported by GPU/CPU from AMD, Nvidia, Intel, Apple, Qualcomm, etc. The support for AV1 decoding is already here but the AV1 encoding is by far supported by Nvidia and Intel only.

AV1 requires more powerful hardware to decode, and it takes much longer time to decode than HEVC.
A hardware accelerated encoder can run HEVC 5x faster than AV1.

AV1 codec is mainly used by Mozilla Firefox and Google Chrome browsers.

## 摄像头接口协议

UVC 全称为 USB Video Class，即：USB 视频类，是一种为 USB 视频捕获设备定义的协议标准。
符合 UVC 规格的硬件设备在不需要安装任何的驱动程序下即可在主机中正常使用。使用 UVC 技术的包括摄像头、数码相机、类比影像转换器、电视棒及静态影像相机等设备。

实现 UVC 协议需要两种接口：一种为 VC Interface(视频控制接口)，VS Interface(视频流接口)。
其中 VC 接口用于对 UVC 设备进行配置操控，而 VS 接口则用于负责传输视频数据流，两者相互配合完成 UVC 设备功能。

V4L2 是 Video for linux2 的简称,为 linux 中关于视频设备的内核驱动。
在 Linux 中，视频设备是设备文件，可以像访问普通文件一样对其进行读写，摄像头在/dev/video0 下。

## CNC machine - 数控机床 Computer Numerical Control

UART - 通用异步收发器 Universal Asynchronous Reciever / Transmitter
一种通用串行数据总线，用于异步通信。该总线双向通信，可以实现全双工传输和接收。在嵌入式设计中，UART 用来与 PC 的 USB 2.0 接口进行通信，包括与监控调试器和其它器件，数据传输速率可达 12 Mbps。

MMIO - Memory-mapped Input and Output
FIFO - First-In, First-Out

## 独立磁盘冗余阵列（RAID，redundant array of independent disks）

把相同的数据存储在多个硬盘的不同的地方，改良性能，增加容错能力。

- RAID0 又称为 Stripe 或 Striping，把连续的数据分散到多个磁盘上存取。
  磁盘空间使用率：100%，故成本最低。
  读性能：N × 单块磁盘的读性能
  写性能：N × 单块磁盘的写性能
  冗余：无，任何一块磁盘损坏都将导致数据不可用。

- RAID1 是将一个两块硬盘所构成 RAID 磁盘阵列，其容量仅等于一块硬盘的容量，因为另一块只是当作数据“镜像”。
  磁盘空间使用率：50%，故成本最高。
  读性能：只能在一个磁盘上读取，取决于磁盘中较快的那块盘
  写性能：两块磁盘都要写入，虽然是并行写入，但因为要比对，故性能单块磁盘慢。
  冗余：只要系统中任何一对镜像盘中有一块磁盘可以使用，甚至可以在一半数量的硬盘出现问题时系统都可以正常运行。

- RAID5 奇偶校验信息和相对应的数据分别存储于不同的磁盘上，其中任意 N-1 块磁盘上都存储完整的数据，是目前运用较多的一种解决方案。
  磁盘空间利用率：(N-1)/N，即只浪费一块磁盘用于奇偶校验。阵列中所有磁盘容量必须一样大。
  读性能：(N-1) × 单块磁盘的读性能，接近 RAID0 的读性能。
  写性能：比单块磁盘的写性能稍慢，多了一个奇偶校验信息。
  冗余：一个磁盘发生损坏后，不会影响数据的完整性，从而保证了数据安全。当损坏的磁盘被替换后，RAID 还会自动利用剩下奇偶校验信息去重建此磁盘上的数据，来保持 RAID5 的高可靠性。

## 网络

56K Modem： 56Kbps
ISDN 上网：带宽到了 144K
ADSL：带宽达到了 512K，最高做到了下载速率 8Mbps。
2010 年以后，光纤上网出现了，取代了 ADSL。

光纤的速率可以做得很高，最早是 10Mbps，后来是 100M（百兆）、1000M（千兆）、直到现在的 10000M（万兆）。

万兆网络的更大意义，或许在于跟 USB 3.0 接入的本地设备相比，它接入的网络设备的通信速率，两者是一样的。这意味着，互联网与本地设备，在万兆网络下，可以视为位于相同的 "数据总线" 上。
