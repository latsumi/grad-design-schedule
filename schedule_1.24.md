### 今日目标

学习 [bigmagic博客](https://my.oschina.net/u/4239621)的几篇关于 riscv 的文章

### 需要完成的工作


### 一日流水账

睡了一上午

13:20 - 开始学习bigmagic博客

16:00 - 17:00 开会，汇报近期完成情况

19:00 - 22:00 继续看博客

23:30- 看 `riscv64-ucore` 的文档

### bigmagic博客学习笔记

#### 读 [riscv64 裸机编程实践与分析](https://my.oschina.net/u/4239621/blog/4868601)

1. 一个工程包括两部分，链接文件和源代码

    * 源代码就是编译链接生成的二进制程序
    * 链接脚本文件则可以告诉程序的布局，比如代码段，函数的入口等等

2. 查看生成程序的布局情况
```
riscv64-unknown-elf-objdump -d filename
```
3. 有点怪，项目不是从c代码开始的，只有汇编代码和链接文件，没法直接参考（其实是可以参考的，看了别人的项目工程里是有 `.S` 文件的）

4. 可以参考的编译指令
```
riscv64-unknown-elf-gcc -march=rv64g -mabi=lp64 -static -mcmodel=medany -fvisibility=hidden -nostdlib -nostartfiles -Thello.ld -Isifive_u hello.s -o hello
```
`-march`：可以指定编译出来的架构，比如rv32或者rv64等等。

`-static`：表示静态编译。

`-mabi=lp64`：数据模型和浮点参数传递规则

`-mcmodel=medany`：没看懂，好像跟地址空间范围有关

`-fvisibility=hidden`：动态库部分需要对外显示的函数接口显示出来。

`-nostdlib`：不连接系统标准启动文件和标准库文件，只把指定的文件传递给连接器。

`-nostartfiles`：不带main函数的入口程序。

`-Thello.ld`：加载链接地址。

#### 读 [opensbi下的riscv64裸机系列编程1(串口输出)](https://my.oschina.net/u/4239621/blog/4872019)

先暂停看以前同学的ucore文档

### [`riscv64-ucore`](https://1790865014.gitbook.io/ucore-step-by-step/v/tutorial/) 文档学习笔记

#### lab 0

了解了自己之前用的是预编译( `prebuilt` )工具链，没有什么问题，不一定需要复杂的编译指令。

#### lab 0.5 最小可执行内核

* 链接器 `ld`：作用是把输入文件(往往是 .o文件)链接成输出文件(往往是elf文件)。`链接脚本` (linker script)的作用，就是描述怎样把输入文件的 `section` 映射到输出文件的section, 同时规定这些section的 `内存布局`
* `tail`是riscv伪指令，作用相当于调用函数（跳转）
* 关键字 `__attribute__`：定义函数时使用，可以设置函数属性，示例如下
```
int kern_init(void) __attribute__((noreturn));
```
本次用到的 attribute-list 为 `noreturn` ，表示函数不会返回。
* `extern` 修饰的关键字：此处只声明变量（变量名，数据类型），而定义在其他文件中（分配内存）
* 我们可以通过 `ecall` 指令(environment call)调用OpenSBI。通过寄存器传递给OpenSBI一个 `调用编号`，如果编号在 0-8 之间，则由OpenSBI进行处理。
* C语言并不能直接调用ecall, 需要通过 `内联汇编` 来实现
* `unsigned char` 的使用：赋值给int、long等类型时，不会对最高位进行扩展

### 零散的可能用到的知识

编译的时候加 `-v` 参数可以看到编译过程中的细节，比如用了哪些库和参数之类的。

[OSCHINA](https://www.oschina.net/)似乎是个很好的网站，如果有问题搜不到可以考虑去这边搜问题解答

RISC-V `特权指令`，三个模式
* Machine Mode：机器模式，简称M Mode。机器级是最高级特权，也是 RISC-V 硬件平台唯一必须的特权级。运行于机器模式（M-mode）下的代码是固有可信的
* Supervisor Mode：监督模式，简称S Mode。
* User Mode：用户模式，简称U Mode。用户模式（U-mode）和管理员模式（S-mode）被分别用于传统应用程序和操作系统

### 今日总结

今天主要的时间都用来看上述博客和riscv64-ucore的文档，赞一个文档质量，十分详细生动，而且注释非常清楚，简直奶奶级教程。但是我自己的代码工作好像还有很多要做，时间已经很晚了(25:16)所以修改了日程计划，把明天也划给第一模块。

决定了自己的os叫做qCore。通“急行”（きゅうこう），希望能顺利快快进展，早日毕业。

明天的工作应该是先把lab0.5的代码解析大致看完，看看有什么新知识点，然后就可以参照博客自己建项目了。



