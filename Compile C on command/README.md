# 在命令行下编译 C 语言 (Win 特指)

有同学说，我电脑配置极低，VS 通常启动较慢，怎么通过命令行编译 C 程序？

以前也确实遇到过这个情况，一台处理器为 U 的内存只有 2G 的电脑结果跑了一个 Win 8，这个环境下跑 VS 肯定是不方便了，连 Dev 也很慢。
所以，如果学了一点命令行基础的，用命令行无疑是最合适的。动不动就看到一些个人服务器就一核处理器和 512M 的内存，带个 Minimal 的系统都不吃力。
接下来就是要介绍怎么在命令行下编译和运行程序，这里使用的是 MinGW 的 gcc

## 前置条件

阅读本文前，我假定你已经有一定的命令行功底，懂得 Win 环境下最基本的命令行操作

## 什么是 gcc

gcc，全称 GNU Compiler Collection，就是一套编译工具链。我们把一个或多个代码文件交给 gcc 后，它负责调用 cc1 程序生成经过预处理的 .i 文件，之后 cc1 拿着这些 .i 生成 .s 的汇编文件，之后 gcc 拿着这些汇编文件交给 as 程序让它生成 .o 的二进制代码文件，最后 collect2 程序把这些二进制代码文件链接到一起，生成一个可执行文件

## 下载 gcc (x64)

到[这里](https://nuwen.net/mingw.html)下载 MinGW，页面的 Download 处有一个 mingw-[version]-without-git，下载它

如果你是 32 位系统，往后看

完成后，双击运行，解压到你想要的位置

## 添加环境变量

在命令行那篇文章里提到过，要想在命令行下运行一个文件，就得去到它所在的那个路径。但是如果我们每次都要去到 gcc 所在的文件夹，再写上一长串的路径去编译文件，岂不是很麻烦？为此，我们要把 gcc 的路径添加到环境变量里去

### 复制 gcc 所在的路径

在你解压的目录下，有一个叫做 `MinGW` 的文件夹，打开它，里面有一个 `bin` 目录，打开。复制当前的路径

右键计算机 -> 属性 -> 高级系统设置 -> 环境变量 -> 系统变量 -> Path

### 如果你在 Win10

双击 Path，在新出来的窗口里点击新建，粘贴你复制下来的路径，然后点击确定，所有的窗口都是确定，没有可以点击确定的窗口点击关闭

### 如果你不是 Win10

打开 Path，在弹出来的窗口的变量值的末尾，加上一个`半角冒号`，之后粘贴你复制的路径，点击确定

## 测试是否正确

```batch
> gcc
```

输出的如果不是`不是内部或外部命令`的话，就算是安装成功了

你也可以用 `gcc --version` 来查看当前安装的 gcc 版本

```batch
> gcc --version
```

## 编辑你的代码

你可以打开记事本，编辑，之后保存为 .c 后缀的代码文件。或者使用 Sublime，Nodepad++ 等工具作为你的记事本

## 文件编码问题

如果你用的是记事本来写 .c 文件，文件里的中文输出的时候不会有问题，如果是 Sublime 和 VS Code 等的编辑器的话，由于 cmd 的字符编码默认是 GBK，而 Sublime，VS Code 默认为 UTF-8，程序输出时会造成乱码

解决方案如下

### Sublime

Ctrl + Shift + P，之后敲 `Install Package Control`，回车

等待若干秒后，会弹窗出现安装成功的提示，点击确定关闭。接着 Ctrl + Shift + P，敲 `Install Package`，过一会会出来一个列表，输入 `ConvertToUTF8`，按回车即可安装

安装完成后会出现一个 Package Control Message，就是安装成功了

接下来重启你的 Sublime，在下次写代码遇到中文的情况，菜单栏 -> File -> Set File Encoding To -> Chinese Simplified(GBK)

### VS Code

右下角的空格旁边有一个文字编码信息，单击后上方有个 通过编码保存，往下滑，有一个 Chinese(GBK)

### Nodepad++

菜单栏 -> 编码 -> 编码字符集 -> 中文 -> GB2312

## 一些编译方式

接下来的代码文件假设为 Hello.c

### 编译并链接：

```batch
> gcc Hello.c
```

生成的是 `a.exe`，默认不显示警告

### 编译并生成自定名字程序

```batch
> gcc Hello.c -o main
```

意思是生成一个叫做 `main.exe` 的程序

也可以是：

```batch
> gcc -o main Hello.c
```

### 保存编译过程中的临时文件

```batch
> gcc Hello.c --save-temps
```

### 只做预处理

```batch
> gcc -E Hello.c
```

生成 .i 的经过预处理的代码文件

### 只做编译

```batch
> gcc -S Hello.c
```

生成汇编代码

### 只做编译和汇编

```batch
> gcc -c Hello.c
```

生成机器码文件

### 打开警告信息

```batch
> gcc Hello.c -Wall
```

意思是打开大多数的警告

你可以使用下面的命令查看更多的警告选项

```batch
> gcc --help=warnings
```

### 让 gcc 优化代码

```batch
> gcc Hello.c -O2
```

意思是让 gcc 对代码做 O2 优化

你可以使用下面的命令查看更多的优化选项

```batch
> gcc --help=optimizers
```

### 每个子进程所用的时间

```batch
> gcc Hello.c -time
```

gcc 是一套工具链，在开头就讲过，`-time` 选项目的是把子进程的耗时给显示出来

### 遵循标准的编译

```batch
> gcc Hello.c -std=c99
```

意思是用 C99 的标准去编译这个文件

类似的还有 C11, C89, C90, C9x, C1x 等等等等……

## 未完待续……