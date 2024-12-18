### 芯片

28 纳米是完全符合摩尔定律（晶体管密度不断增长，成本下降）的最后一个工艺节点，即在 28 纳米之后，虽然产业能继续把晶体管做得更小、却无法更便宜。28nm 是当下芯片制造中最具性价比的工艺节点。

PGA，全称为 Pin Grid Array，即插针网格阵列。一般 PGA 插针的间隔为 1/10 英寸或 2.54 毫米。PGA 的针脚容易断裂、且间隔较大。
早期的 Intel Pentium 处理器采用的是 PGA 封装（Pentium 2 之前），后来的 Pentium 4 处理器则采用了基于 PGA 技术发展来的 FC-PGA（反转芯片 PGA）封装，但依旧属于 PGA 范畴。
在 PGA 接口上，其插座为零插拔力插座，即 ZIF（Zero insertion force）。它通过一个杠杆让用户拉起或推开插座，这个时候，插座内的弹簧式触点就会分开，然后将 PGA 接口的处理器对准放下，再将拉杆拉回到原位卡主。当插座 “归位” 后，接触点会闭合并且 “抓紧” 处理器的针脚，以此固定。

LGA，全称为 Land Grid Array，即平面网格数组封装，针脚位于插座上而非集成电路上。
LGA 封装的芯片能被连接到印刷电路板（PCB）上或直接焊接至电路板上。与传统针脚在集成电路上的封装方式相比，可减少针脚损坏的问题并可增加脚位。
早在 1996 年，MIPS R10000 和 HP PA-8000 处理器就已经使用 LGA 封装，但 Intel 从 2004 年的 Pentium 4 （Prescott） 处理器才开始使用。所有 Pentium D 和 Core 2 Duo 乃至今天的所有 Intel 台式机处理器都使用 LGA 封装。
AMD 之前只在服务器及高性能领域才使用 LGA 封装（如 Socket G34，LGA 1944），直到现在全新一代的 Ryzen 7000 系列才转换到 LGA（AM5）。
LGA 接口通过紧固顶盖的方式固定，少了弹簧式触点。

BGA，全称为 Ball Grid Array，球栅阵列封装。
从电气特性、安全性来看，BGA 方式其实是非常好的选择 —— 但是它不具备便利的可更换特性。
绝大部分的 intel 移动 CPU 都使用了这种封装方式。
APPLE 的处理器产品，目前无一例外都采用 BGA 方式，这样可以充分保证足够的电气特性，同时也兼具稳定性，故障几率相比也是最低的。

FPGA（Field Programmable Gate Array，现场可编程门阵列），是一种半定制芯片。用户可以根据自身的需求进行重复编程。FPGA 的优点是既解决了定制电路的不足，又克服了原有可编程器件门电路数有限的缺点，对芯片硬件层可以灵活编译，功耗小于 CPU、GPU；缺点是硬件编程语言较难，开发门槛较高，芯片成本、价格较高。FPGA 比 GPU、CPU 更快是因为其具有定制化的结构。

ASIC（Application Specific Integrated Circuit 特定用途集成电路）根据产品的需求进行特定设计和制造的集成电路，其定制程度相比于 GPU 和 FPGA 更高。ASIC 算力水平一般高于 GPU、FPGA，但初始投入大，专业性强缩减了其通用性，算法一旦改变，计算能力会大幅下降，需要重新定制。

### 固态电容

全固态主板是全部采用固态电容的主板。

固态电容全名为固态铝质电解电容，是除了钽电容外最高端的电容，它采用高导电性分子材料，而普通的电解电容采用的是电解液。只要有内阻，电容就会发热，里面的热空气会膨胀、上升，并让外壳涨开，只是固态电容的稳定性和膨胀幅度要小很多，因此大部分固态电容不需要防爆纹。

电容的主要作用就是将一些电流的尖峰和杂波进一步过滤，以此保证各部分供电的稳定性。电容的作用就跟水库差不多，它在水流量大的时候会放水，在水流量小的时候又会蓄水，以此来保证水库里蓄水量的平衡。

CPU 的供电电路通常是由电容、电感线圈、场效应管 (MOSFET 管 ) 这三大部分所组成。电容是保证主板和显卡质量的关键，同时也可以说是衡量板卡做工的重点。电容在主板和显卡中的作用主要来保证电压和电流的稳定（起到滤波的作用）。

固态电容的优点
一、杜绝爆浆现象。
二、固态电容在等效串联阻抗表现上相比传统电解电容有更优异的表现。

固态电容的低频响应不如电解电容，如果用于涉及到音效的部分会得不到最佳的音质效果。

### 风扇

尺寸越大，转速越高，风量越大。同样的风量，转速越高，噪音越大。

cfm (cubic foot per minute) 是常用英制流量单位，立方英尺每分钟。
国内一般用 m³/h 风量单位，立方米 / 每小时。
二者换算为：1cfm≈1.7m³/h。

## 电源

快速充电模式 fast charging mode
一个由供电设备、线缆和充电设备组成的充电系统，从初始充电状态开始，至充电 30 分钟，通过提高供电设备的输出电压或输出电流，实现进入电池的平均电流大于等于 3A 或总充电量大于等于电池额定容量的 60% 的充电方式。

根据 UFCS 快充规范内容显示，该标准采用连续调节模式，输出电压分为 5V、10V、20V、30V 四个可编程的档位（类似 USB PD3.0 PPS 调压），其中 5V 档位的可编程电压范围是 3.4V-5.5V、10V 档位的可编程电压范围是 5.5V-12V、20V 档位的可编程电压范围是 12V-21V、30V 电压的可编程电压范围是 21V-36V。

## PLC（可编程逻辑控制器）

PLC 是一种嵌入式系统，它由一组可编程的逻辑电路组成，能够对输入数据进行处理、分析、控制和输出控制信号。PLC 具有很高的灵活性、可靠性和可编程性，可以实现各种复杂的控制功能。

FPC 是 Flexible Printed Circuit 的简称，即柔性印刷电路板，也被称为软性电路板或挠性电路板。
FPC 可以在窄小和有限的空间中弯曲、折叠，从而嵌入大量精密元件，形成可弯曲的挠性电路。
FPC 广泛应用于手机、笔记本电脑、PDA、数码相机、LCM 等产品中，因其配线密度高、重量轻、厚度薄等特性而备受青睐。

# 单片机

Serial is an umbrella word for all that is "Time Division Multiplexed", to use an expensive term. It means that the data is sent spread over time, most often one single bit after another. All the protocols you're naming are serial protocols.

UART - Universal Asynchronous Receiver / Transmitter

- provide a console / terminal login for headless setup

UART is one of the most used serial protocols, and is very simple. Most controllers have a hardware UART on board. It uses a single data line for transmitting and one for receiving data. Most often 8-bit data is transferred, as follows: 1 start bit (low level), 8 data bits and 1 stop bit (high level). The low level start bit and high level stop bit mean that there's always a high to low transition to start the communication. That's what describes UART. No voltage level, so you can have it at 3.3 V or 5 V, whichever your microcontroller uses. Note that the microcontrollers which want to communicate via UART have to agree on the transmission speed, the bit-rate, as they only have the start bits falling edge to synchronize. That's called asynchronous communication.

For long distance communication (That doesn't have to be hundreds of meters) the 5 V UART is not very reliable, that's why it's converted to a higher voltage, typically +12 V for a "0" and -12 V for a "1". The data format remains the same. Then you have RS-232 (which you actually should call EIA-232, but nobody does.)

The timing dependency is one of the big drawbacks of UART, and the solution is USART, for Universal Synchronous/Asynchronous Receiver Transmitter. This can do UART, but also a synchronous protocol. In synchronous there's not only data, but also a clock transmitted. With each bit a clock pulse tells the receiver it should latch that bit. Synchronous protocols either need a higher bandwidth, like in the case of Manchester encoding, or an extra wire for the clock, like SPI and I2C.

SPI - Serial Peripheral Interface

- master slave relationship
- shift registers, sensors and even an SD card

SPI (Serial Peripheral Interface) is another very simple serial protocol. A master sends a clock signal, and upon each clock pulse it shifts one bit out to the slave, and one bit in, coming from the slave. Signal names are therefore SCK for clock, MOSI for Master Out Slave In, and MISO for Master In Slave Out. By using SS (Slave Select) signals the master can control more than one slave on the bus. There are two ways to connect multiple slave devices to one master, one is mentioned above i.e. using slave select, and other is daisy chaining, it uses fewer hardware pins (select lines), but software gets complicated.

To improve better performance, CAN protocol has been designed. In this Arbitration concept is used in which two devices are ready to communicate, then depending on their priority the transmission or reception takes place. CAN is widely used in many industries.

I2C - Inter-Integrated Circuit

- low speed two wire serial protocol
- master slave relationship
- sending data to and from the SDA connection, with the speed controlled via the SCL pin
- discoverable by `i2cdetect` command
- LCD / OLED screens, temperature sensors and analog to digital converters

I2C (Inter-Integrated Circuit, pronounced "I squared C") is also a synchronous protocol, and it's the first we see which has some "intelligence" in it; the other ones dumbly shifted bits in and out, and that was that. I2C uses only 2 wires, one for the clock (SCL) and one for the data (SDA). That means that master and slave send data over the same wire, again controlled by the master who creates the clock signal. I2C doesn't use separate Slave Selects to select a particular device, but has addressing. The first byte sent by the master holds a 7 bit address (so that you can use 127 devices on the bus) and a read/write bit, indicating whether the next byte(s) will also come from the master or should come from the slave. After each byte, the receiver must send a "0" to acknowledge the reception of the byte, which the master latches with a 9th clock pulse. If the master wants to write a byte, the same process repeats: the master puts bit after bit on the bus and each time gives a clock pulse to signal that the data is ready to be read. If the master wants to receive data it only generates the clock pulses. The slave has to take care that the next bit is ready when the clock pulse is given. This protocol is patented by NXP (formerly Phillips), to save licensing cost, Atmel using the word TWI (2-wire interface) which exactly same as I2C, so any AVR device will not have I2C but it will have TWI.

Two or more signals on the same wire may cause conflicts, and you would have a problem if one device sends a "1" while the other sends a "0". Therefore the bus is wired-OR'd: two resistors pull the bus to a high level, and the devices only send low levels. If they want to send a high level they simply release the bus.

TTL (Transistor Transistor Logic) is not a protocol. It's an older technology for digital logic, but the name is often used to refer to the 5 V supply voltage, often incorrectly referring to what should be called UART.

工业机器人
库卡 KUKA，AABB 精度和重复性好

目前几个主流的手机玻璃维氏硬度参数如下：

小米龙晶（860 HV0.025）、华为昆仑 2 代（830 HV0.025）、苹果超晶瓷（814 HV0.025）、康宁大猩猩玻璃 Victus2（670 HV0.025）。

ps.HV 表示维氏硬度，前面的数值为硬度值，后面则为试验力，如果试验力保持时间不是通常的 10-15 秒，还需在试验力值后标注保持时间。

# 工控机通信
RS-232 是美国电子工业协会 EIA（Electronic Industry Association）联合贝尔系统公司、调制解调器厂家及计算机终端生产厂家于 1970 年共同制定的一种串行物理接口标准。
RS 是英文 “推荐标准” 的缩写，232 为标识号。RS-232 是关于串行通讯的一个机械和电气接口标准。最初使用DB25接口，由IBM改为DB-9插头。
RS232是全双工传输，单端驱动，只能驱动一个接收器，传输速率一般不超过20Kbps，传输距离不超过 15 米。
需三条接口线，即"发送数据TXD"、"接收数据RXD"和"信号地GND"。
RS232 采用负逻辑电平，定义 + 5V 到 + 12V 为低电平，-12V 到 - 5V 为高电平。易损坏接口电路的芯片。

RS485是半双工传输，差分驱动，可以驱动多个接收器，有更好的抗干扰能力，传输速率可以达到 100Kbps 或更高，传输距离可以达到数百米甚至千米以上。
一般只需二根信号线，所以RS485 接口均采用屏蔽双绞线传输。两线压差为 -(2~6) V 表示 0，两线压差为 +(2~6) V 表示 1。
RS-422 的电气性能与RS-485完全一样，使用差分信号。RS-422 有4 根信号线：两根发送（Y、Z）、两根接收（A、B）。可以同时收和发（全双工）。

UART（Universal Asynchronous Receiver/Transmitter，通用异步收发器）
UART 最初是在 1980 年代由 Motorola 开发的，并被广泛用于微控制器、嵌入式系统和计算机之间的通信。
UART 有 4 个 pin（VCC、GND、RX、TX），用的是 TTL 电平，低电平为 0（0V），高电平为 1（3.3V 或以上），可以直接使用 CPU 使用的电平，直接与芯片的引脚相连。
RX 用于接收，TX 用于发送。每个设备的 RX 引脚都连接到另一个设备的 TX 引脚。
接设备的时候，一般只接 GND、RXD、TXD。不会接 Vcc 或者 + 3.3V 的电源线，避免与目标设备上的供电冲突。

若加入一个合适的电平转换器，如 SP3232E、SP3485，UART 也能用于 RS-232、RS-485 通信。
在异步通信中，发送端和接收端不需要同时处于激活状态，而是通过起始位和停止位来标识数据帧的开始和结束。
UART 通信把一个字节的数据拆分成若干 bit 位，然后一个 bit 一个 bit 的发送。发送完一个字节后会产生一个空闲状态，轮询式发送就是等待这个空闲状态并发送下一个字节。
UART 接收也是如此，UART 接收器收完一个字节并收到停止位信号时，就会向单片机的 UART 数据寄存器保存刚收到的数据，并产生一个收到标志位，轮询该标志位就可以接收到该字节数据。
UART 芯片16C550 等，传输速率达到115.2Kbps。
使用 Cat5e电缆时，传输距离可达 100 米。使用 Cat6电缆时，传输距离可延长至 125 米。质量较差的电缆可能只能支持 50 米的传输距离。如果需要更长的传输距离，可以考虑使用电平转换器来延长至 500 米。

 USB 是一种多点、高速的连接方式，采用集线器能实现更多的连接。USB 接口的基本部分是串行接口引擎 SIE，SIE 从 USB 收发器中接收数据位，转化为有效字节传送给 SIE 接口；反之，SIE 接口也可以接收字节转化为串行位送到总线。
 USB 采用差分传输方式，且具有检错和纠错功能，保证了数据的正确传输。USB 支持三种总线速度，低速 1.5Mbps、全速 12Mbps 和高速 480Mbps。
 USB 电缆具有传送电源的功能，支持节约能源模式，耗电低。USB 总线可以提供电压 + 5v、最大电流 2A 的电源，供低功耗的设备作电源使用，不需要额外的电源。

 ## 连接线

 ribbon cable 带状线缆
 flat ribbon cable 扁平带状线缆

 ## 树莓派相机参数表

|                                    | **年份** | **像素** | **芯片型号**          | **芯片尺寸**                       | **分辨率**       | **像素尺寸**          | **镜头**    | **水平视场角** |
|------------------------------------|-----------|-----------|-------------------|-------------------------------------|------------------------|-------------------|------------|-----------|
| Raspberry Pi Camera Module         | 2013     | 5MP        | Omnivision OV5647 | 3.76 × 2.74 mm                      | 2592×1944              | 1.4 µm × 1.4 µm   | 定焦        | 53.5      |
| Raspberry Pi Camera Module 2       | 2018     | 8MP        | Sony IMX219       | 3.68 × 2.76 mm (4.6 mm diagonal)    | 3280×2464              | 1.12 µm × 1.12 µm | 定焦        | 62.2      |
| Raspberry Pi High Quality Camera   | 2020     | 12.3MP     | Sony IMX477       | 6.287mm × 4.712 mm (7.9mm diagonal) | 4032×3040              | 1.55 μm × 1.55 μm | C口，CS，M12 |           |
| Raspberry Pi Camera Module 3       | 2023     | 11.9MP     | Sony IMX708       | 6.45 × 3.63mm (7.4mm diagonal)      | 4608×2592              | 1.4μm × 1.4μm     | 自动变焦      | 66       |
| Raspberry Pi Global Shutter Camera | 2023     | 1.58MP     | Sony IMX296       | 6.3mm diagonal                      | 1456×1088              | 3.45μm × 3.45μm   | C口，CS     |           |
| Raspberry Pi AI Camera             | 2024     | 12.3 MP    | Sony IMX500       | 1/2.3” (7.857mm) 6.287mm × 4.712 mm | 4056×3040 10-bit 10fps | 1.55 μm × 1.55 μm | 定焦        | 66        |


## 开发板配置
芯片
    MCU
    时钟源
存储
    RAM
    ROM
    Flash
    SD卡
接口
    GPIO
    UART
    I2C
    SPI
    PWM
    USB
    CAN
调试接口
    JTAG
    SWD
网络
    Eithernet
    WiFi
    BLE
    Zigbee
模块
    ADC
    DAC
显示
    LED
    LCD
声音
    蜂鸣器
    扬声器
    麦克风
传感器
    温度
    湿度
    加速度计
    陀螺仪
    光照传感器
    震动传感器
    压力传感器
    红外传感器
    超声波传感器
电源
电池
显示屏