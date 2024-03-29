A virtual machine (VM) is an emulation of a computer system.
An emulator is hardware or software that enables one computer system (called the host) to behave like another computer system (called the guest).
Video game enthusiasts use emulators to play 1980s arcade games using the original 1980s programming code, which is interpreted by a current-era system.

Emulation focuses on recreating an original computer environment, which can be time-consuming and difficult to achieve, but valuable because of its ability to maintain a closer connection to the authenticity of the digital object. Potentially additional features original hardware didn't have.

This is especially useful when the original system is difficult to obtain, this should not only apply to out of date systems, but also be upwardly mobile to future unknown systems.

In many cases, the goal of emulation in new media art is to preserve a digital medium so that it can be saved indefinitely and reproduced without error, so that there is no reliance on hardware that ages and becomes obsolete. The paradox is that the emulation and the emulator have to be made to work on future computers.

Emulation techniques are commonly used during the design and development of new systems. It eases the development process by providing the ability to detect, recreate and repair flaws in the design even before the system is actually built. This also allows the software development to take place before the hardware is ready, thus helping to validate design decisions.

## CHIP-8, mid-1970s

CHIP-8 是一个很简单的芯片，有 16 个 8 位寄存器和 35 个指令，可以使用 4K 内存。

- 4KB Memory
- 16 8-bit data registers, address register is 16 bits
- 2 timers, for delay and sound, both count down at 60 hertz
- monochrome 64×32 pixels Display
- beeping sound when sound timer is nonzero
- input keyboard has 16 keys
- 35 16-bit opcodes, support math and logic operations, control flow, graphics and sound

## Super Chip (or SCHIP), 1991

- 128x64 resolution
- higher speed in extended mode
- instructions to scroll the screen down, left, and right
- backward compatible with CHIP-8

## Mega Chip (or MCHIP), 2007

- 256x192 resolution
- Indexed coloring (255 colors max + transparency)
- Digitised sound (mono 8bit)
- 24-bit addessing, 32MB max
- Fixed high-speed speed
- Custom sprite sizes
- backward compatible with Super Chip

## XO-CHIP, 2014

- save an inclusive range of registers to memory
- load an inclusive range of registers from memory
- select zero or more drawing planes by bitmask
- scroll the contents of the display up by 0-15 pixels
- 16-byte "audio pattern buffer"

[Chip-8/SuperChip/MegaChip emulator and docs](https://github.com/gcsmith/gchip)
[A Chip8 assembler and IDE](https://github.com/JohnEarnest/Octo)

## Little Computer 3 (LC-3)

The LC-3 was developed by Yale N. Patt at the University of Texas at Austin and Sanjay J. Patel at the University of Illinois at Urbana–Champaign, specified in their textbook Introduction to Computing Systems: From Bits and Gates to C and Beyond, 2/e.

- eight 16-bit registers
- 16-bit addressable memory
- fifteen 16-bit instructions with 4-bit opcodes
- I/O devices operate on ASCII characters
- no native PUSH and POP instructions
- no native support for floating-point numbers

http://www.rodrigoaraujo.me/posts/lets-build-an-lc-3-virtual-machine/

## Motorola 68000

- 32-bit processor, 8 MHz
- 16-bit data bus
- 16-bit arithmetic logic unit
- 8 32-bit general purpose data registers
- 7 32-bit general purpose address registers plus two stack registers
- A 16-bit status register for condition codes and privileged flags like the Supervisor mode enable flag and the interrupt priority level
- big endian byte order

It is used on many early computers including the early Macintosh series, the early Sun Microsystems workstations, the Amiga, the Atari ST, and the Sega Genesis/Mega Drive.
68000 is still a supported architecture in the latest version of gcc.

## AVR 单片机

AVR is the microcontroller designed by Atmel, now owned by Microchip. It is very popular with both hobbyists and professionals but has seen a massive uptake in education due to the Arduino products and ecosystem.
AVRs are available with 8-pins to 100-pins, although anything 64-pin or over is surface mount only.
采用了 RISC 精简指令集，内嵌高质量的 Flash 程序存储器，擦写方便，支持 ISP 和 IAP，便于产品的调试、开发、生产、更新。

Type 1 Hypervisors (Paravirtualization): Hypervisor sits on bare metal hardware and each OS sits on the hypervisor. e.g. VMware ESXi, Oracle VM Server, Microsoft Hyper-V.

Type 2 Hypervisors (Emulation): Hypervisor sits on top of the host OS. e.g. Oracle VirtualBox, Parallels, VMware Workstation.
