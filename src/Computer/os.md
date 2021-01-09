## The UNIX Time-Sharing System

It is hoped, however, the users of UNIX will find that the most important characteristics of the system are its simplicity, elegance, and ease of use.

### The File System

From the point of view of the user, there are three kinds of files: ordinary disk files, directories, and special files.

A file contains whatever information the user places on it, no particular structuring is expected by the system. The structure of files is controlled by the programs which use them, not by the system.

Directories provide the mapping between the names of files and the files themselves, and thus induce a structure on the file system as a whole. The directory structure is constrained to have the form of a rooted tree.

When the name of a file is specified to the system, it may be in the form of a path name, which is a sequence of directory names separated by slashes / and ending in a file name.

If the sequence begins with a slash, the search begins in the root directory. A path name not starting with / causes the system to begin the search in the user’s current directory.

The directory entry for a file consists merely of its name and a pointer to the information actually describing the file. The same nondirectory file may appear in several directories under possibly different names. This feature is called linking; a directory entry for a file is sometimes called a link. A file is made to disappear along with the last link to it.

Each directory always has at least two entries. The name in each directory refers to the directory itself. Thus a program may read the current directory under the name . without knowing its complete path name. The name .. by convention refers to the parent of the directory in which it appears, that is, to the directory in which it was created.

In particular, in the root directories of all file systems, removable or not, the name .. refers to the directory itself instead of to its parent.

Special files are associated with I/O devices. Special files are read and written just like ordinary disk files, but requests to read or write result in activation of the associated device. An entry for each special file resides in directory /dev. File and device names have the same syntax and meaning, so that a program expecting a file name as a parameter can be passed a device name; additionally, special files are subject to the same protection mechanism as regular files.
在当时是一个讨巧的设计，现在则可抛弃。不同 IO 设备有不同的功能和接口，不能被简单的数据读写所涵盖。不同厂家同一类型的设备应当遵循统一的接口协议，节省实现成本，方便更换。文件和设备在概念上是分离的，不能混淆。设备可以从简单到复杂支持多套接口协议，用户按需选用。

There is a mount system request which has two arguments: the name of an existing ordinary file, and the name of a direct-access special file whose associated storage volume (e.g. disk pack) should have the structure of an independent file system containing its own directory hierarchy. The effect of `mount` is to cause references to the heretofore ordinary file to refer instead to the root directory of the file system on the removable volume.
加载到的路径没必要事先存在。

Each user of the system is assigned a unique user identification number. When a file is created, it is marked with the user ID of its owner. Also given for new files is a set of seven protection bits. Six of these specify independently read, write, and execute permission for the owner of the file and for all other users.

If the seventh bit is on, the system will temporarily change the user identification of the current user to that of the creator of the file whenever the file is executed as a program. This change in user ID is effective only during the execution of the program which calls for it. The set-user-ID feature provides for privileged programs which may use files inaccessible to other users. This mechanism is used to allow users to execute the carefully written commands which call privileged system entries.

The success of UNIX lies not so much in new inventions but rather in the full exploitation of a carefully selected set of fertile ideas, and especially in showing that they can be keys to the implementation of a small yet powerful operating system.

Linux 内核是一个典型的宏内核，Linux 内核太出名了，以至于几乎所有人都认为作为一个操作系统内核就应该长得和 Linux 内核那样。Minix 是 Andrew S. Tanenbaum 所著《操作系统：设计与实现》教材的示例代码。Linus 的 Linux 内核参考了 Minix，Minix 是微内核架构的操作系统。

宏内核通过函数调用访问特定的逻辑和数据。

微内核通过 IPC(进程间通信)访问特定的逻辑和数据。

函数调用是单向的，而进程间通信可以双向的。

宏内核缺乏访问共享资源的有序仲裁机制，因此同步开销会非常大，最直接的后果就是宏内核随着处理器核心的增加而不可扩展。站在多核心可扩展性角度，多核平台，无疑微内核的设计会更好，服务进程的仲裁可以让应用在多核平台无锁运行。

因为内核协议栈性能低，构建用户态协议栈可以做到专核专用，进程上下文可以完全掌握数据包收包逻辑的全过程，更便于仲裁和协作。
在经过了 30 多年的发展后，微内核，宏内核之间的性能差距已经大大缩小了。

如果能在硬件层面把 IPC 的内存拷贝，变成内存共享，就能彻底解决微内核的性能问题。

## Address Translation

地址转换负责将虚拟地址转换成物理地址，正因为有了这层转换，好多技术才可以发展起来，比如虚拟机、容器、沙盒等。

虚拟内存，借助于地址转换，操作系统可以给应用程序一种假象，独占整个计算机内存，可以使用超过实际物理大小的内存，应用程序之间互不干扰。

进程隔离，地址转换可以用来构建沙盒（sandboxes）技术，让第三方代码在沙盒中运行，限制其对内存的访问，从而避免操作系统内核和应用程序受到病毒或者恶意代码的攻击。

进程间通信，地址转换可以将不同进程空间的地址映射到同一段物理内存，从而实现进程间通信。

共享代码段，动态加载 so 库可以在多个程序实例之间进行共享。

程序初始化，使用地址转换技术可以让应用程序只加载部分代码和数据就可以运行（后台继续加载剩余部分），若执行到未加载部分，则发生中断挂起应用程序，待操作系统内核将剩余部分加载到内存后再恢复应用程序的执行。

缓存管理，操作系统内核通过合理安排程序所在的内存位置来提高缓存效率。

内存映射文件，将文件内容映射到应用程序地址空间，这样一来，文件的内容就可以被应用程序直接访问。

#### 地址转换器需要实现的目标

内存保护，限制进程访问某些特定区域的内存，比如阻止进程访问不属于他的内存空间，阻止进程覆写其代码区域。
内存共享，允许多个进程共享某段内存区域，例如，同样的代码段或者公共库。
柔性内存布局，允许操作系统灵活的将一个进程的各个部分（代码，数据，堆，栈，内存映射文件等）放到内存的任何地方（在权限许可的情况下）。
运行时查找效率，若地址转换的耗时比执行指令本身还长，显然是不切实际的，指令提取和数据加载存储过程需要硬件的支持。
紧凑的转换表，地址转换需要的空间开销要远小于被管理的内存大小。
可移植性，不同的处理器硬件架构在协助实现地址转换的时候采用了不同的选择，操作系统内核需要适应多个处理器硬件架构。

#### 内存的两种视角

虚拟地址，进程看到的内存地址为虚拟地址，他们不对应任何物理实体，每个进程有自己的地址空间。
物理地址，内存系统看到的地址为物理地址，他们用实际的地址去查找和存储内容。
