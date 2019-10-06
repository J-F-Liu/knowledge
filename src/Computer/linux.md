## Linux From Scratch

http://www.linuxfromscratch.org/

There are always many ways to accomplish a single task. It is not a matter of right and wrong, but a matter of personal taste.

With all the choices available, if you didn't like something, you were free, even encouraged, to change it.

LFS can help you learn how a Linux system works from the inside out. Building an LFS system helps demonstrate what makes Linux tick, and how things work together and depend on each other. One of the best things that this learning experience can provide is the ability to customize a Linux system to suit your own unique needs.

LFS allows you to create very compact Linux systems. When installing regular distributions, you are often forced to install a great many programs which are probably never used or understood. These programs waste resources.

Education is by far the most powerful of reasons. As you continue in your LFS experience, you will discover the power that information and knowledge truly bring.

### Pre-reading List
- http://www.tldp.org/HOWTO/Software-Building-HOWTO.html
- http://moi.vonos.net/linux/beginners-installing-from-source/

```dot
digraph packages {
  MPC -> Gcc
  MPFR -> Gcc
  Readline -> Bash
}
```
