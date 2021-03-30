### 今日目标

周四了，第二模块的代码能不能用上并跑通呢。

### 今日流水账

总之是在fit楼通宵了。
先对比一下ch2的文件吧

两个py文件 kernelld看过了
pack.py 干了啥？ 作用是生成link_app.S 供编译链接，将目标用户程序包含入 link_app.S中，同时记录了这些程序的地址和名称信息

musl-riscv-toolchain 的作用是什么？突然冒出来这样的一个工具链

为了加入trap文件（中断相关），添加了riscv.h这个文件

string.c 一些字符串操作相关的函数

syscall.c 提供系统调用的函数

trampoline.S 切换用户态和内核态

syscall_ids.h 应该是把所有系统调用的编号全写进去了（实际上只实现了write和exit）


user里面生成用户程序的过程跟系统有什么关系

### 今日总结