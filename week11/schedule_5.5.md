### 今日目标

论文，论文，还是论文。今日第二章

### 可能会用到的知识点

本部分模拟硬件内存十分有限的场景

kernelld.py文件保证用户程序链接时的指令对齐，kernel_app.ld写了内存布局（？等下要对比下两个ld文件）
user.ld 和 batch.c 完成了用户程序的搬运。

trap.c 的 usertrapret() 和 trampoline.S 中的 userret 函数 需要着重解释。
trampoline.S 切换用户态和内核态

musl可能跟用户程序有关？

用户程序栈按4k对齐

user.ld 搬运用户程序到指定位置0x80400000

中断帧trapframe的定义


### 可能可以参考的文献

riscv中文手册

### 今日总结

完成了第二章，但是进度比预计的慢，后面还是要尽量多留点时间，不然时间真的不够了。