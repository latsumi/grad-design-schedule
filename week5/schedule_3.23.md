### 今日目标

看完os2021课程实验指导书中的lab1和lab2

### 今日流水账

下午大致了解了下实验顺序，确定可以作为参考。

晚上九点开始看

### lab1 RV64裸机应用

makefile语法 变量定义有几种赋值符号。使用 `$(varname)` 来调用

可参考的 [内存结构布局](https://rcore-os.github.io/rCore-Tutorial-Book-v3/chapter1/4understand-prog.html#id8) 介绍，包括每段的名称和功能

entry文件 设置好 os 运行的堆栈，然后调用main函数

main文件 首先初始化 `.bss` 段，然后输出内存布局的信息

`sbi.c` 中，使用嵌入式汇编，调用 ecall 指令向 M 态，也就是向 rustsbi 发出了服务请求。

printf 的实现见 `printf.c`

### lab2 批处理系统

内存很小，执行第二个任务的时候要把第一个任务从内存丢掉

用 `cmake` 来构建用户程序。user文件夹下好多文件，这个哪些是能直接拿来用的？

user/src目录下是是我们要运行的用户程序

kernel/kernelld.py文件保证用户程序链接时的指令对齐。修改了 `/user/target/kernel_app.ld` 这个文件写的内存布局
中间根据需要执行的用户程序在数据段添加了几行，具体见[这里](https://github.com/DeathWish5/ucore-Tutorial-Book/blob/main/lab2/guide.md#%E7%94%A8%E6%88%B7%E7%A8%8B%E5%BA%8F%E7%9A%84%E8%BD%BD%E5%85%A5)。

执行前需要将用户程序加载到规定的物理内存位置。所以规定了用户的链接脚本，并在内核完成程序的 "搬运"。分别是 `user/lib/arch/riscv/user.ld` 和 `kernel/batch.c`

`trap.c` 特权级切换
trap.c 的 usertrapret() 和 trampoline.S 中的 userret 函数展示了从S态返回/进入U态的过程，也就是当中断处理完毕后返回用户态的过程。（先放着用到了再看）

用户中断处理 先不管，等出错了再考虑

### 今日总结

大致看完了指导书前两个lab。明天先修改之前的文件，看能不能跑通printf。写之前先记得改gitignore文件。争取白天完成。



