### 今日目标

完成ch6 将已有的表全部完成 完成引言

### 可能用到的知识点

#### 大学生能力大赛

1. 彭部分，ucore移植到K210开发板

可能没啥参考的，先扫一遍吧
为什么移植riscv：开源，没有历史包袱。比如x86 控制权从rom来到bootloader时候，涉及到实模式，保护模式。复杂概念，分页之外的分段，全集描述符表，段选择子

如何快速上手已有项目：添加小功能，编写新的测试用例

在模拟器上调试的思路：优先使用printf。如果用不了用gdb。

何时用不了：
* 比如发生栈溢出错误，覆盖了页表，调用printf会破坏现场。处理方法是用反汇编文件定位错误范围，用gdb打断点，单步追踪，检查栈内存页内容
* 上下文切换，修改寄存器的时候。调用printf会破坏现场

调试经验：合理使用宏来控制整体的调试输出，而不是散落各地的printf
小经验：用测试用例来驱动代码的编写，

2. 张部分 新实验，rustsbi等等

ucore实验 第四五个实验才能真正运行用户程序 1-4都只是os的一部分
重要的是能提供操作系统的功能。

#### 进程间通信

管道pipe 只能用于父子进程之间？

本质是内核缓冲区 以先进先出方式存取。

文件描述符是怎么回事，申请文件返回的是文件指针？

### 可能可以参考的文献


### 今日总结

