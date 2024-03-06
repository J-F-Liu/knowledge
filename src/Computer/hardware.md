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

# 单片机

I2C - Inter-Integrated Circuit

- low speed two wire serial protocol
- master slave relationship
- sending data to and from the SDA connection, with the speed controlled via the SCL pin
- discoverable by `i2cdetect` command
- LCD / OLED screens, temperature sensors and analog to digital converters

SPI - Serial Peripheral Interface

- master slave relationship
- shift registers, sensors and even an SD card

UART - Universal Asynchronous Receiver / Transmitter

- provide a console / terminal login for headless setup

工业机器人
库卡 KUKA，AABB 精度和重复性好

目前几个主流的手机玻璃维氏硬度参数如下：

小米龙晶（860 HV0.025）、华为昆仑 2 代（830 HV0.025）、苹果超晶瓷（814 HV0.025）、康宁大猩猩玻璃 Victus2（670 HV0.025）。

ps.HV 表示维氏硬度，前面的数值为硬度值，后面则为试验力，如果试验力保持时间不是通常的 10-15 秒，还需在试验力值后标注保持时间。
