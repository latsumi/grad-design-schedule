### 今日目标

先修改之前的文件，看能不能跑通printf。写之前先记得改gitignore文件。
晚上搞明白lab2需要哪些文件，尝试添加代码。

### 需要弄明白的问题

1. user文件夹底下这么多文件是怎么通过cmake生成的，哪些是需要自己手写的。

### 今日流水账

上午摸了，只稍微看了下

下午两点睡醒了

### ch1分支

改了gitignore
修改main文件
改build文件

为什么可以用stdarg.h文件？

总之把可能用到的赶紧复制过去吧。

printf文件中必不可少的几个函数包括 `consputc` 和 `loop` 函数，所以必须加上panic文件和console文件

makefile中关于 `CFLAGS` 的部分看不懂。这参数是干吗的，啥时候用到的(应该是makefile自有的关键字参数)
注释掉的话会报错
```
defs.h:15:6: warning: conflicting types for built-in function 'printf' [-Wbuiltin-declaration-mismatch]
```
具体每个参数什么作用先不搞懂了，没空搞这个。
PIE是生成地址无关可执行程序的技术，开启时可执行程序被加载到内存中时其加载地址存在不可预知性

### 今日总结

要修改的代码量远超自己的预计，printf文件需要一堆函数，没时间详细搞懂了。
该熬夜继续ch2了
