# mkdir - 新建文件夹

与 win 下的 mkdir 同理，在这里详细讲 Linux 下的 mkdir

命令格式：`$ mkdir [OPTION]... DIRECTORY...`

仅仅是新建一个文件夹的话，mkdir + 你想要的名字 就可以了

如果你要同时建立多个文件夹，就多写几个，用空格间隔

再如果，你的文件夹名字是带了空格的，用双引号就好了，例如：

```shell
$ mkdir "Hello World"
```

mkdir 提供了许多的选项，下面逐一介绍

## -m, --mode=MODE

像 chmod 一样设置文件夹权限，而不是 a=rwx 这个格式

```shell
$ mkdir -m 600 hello
$ mkdir --mode=600 hello    # 两个命令等价
```

```
$ mkdir hello
$ chmod 600 hello
```

意思是，上面两个命令，等价

## -p, --parents

如果要创建的文件夹已存在，不显示错误。会创建父目录在需要的时候

后面一句话是什么意思呢？假定你要往新建的文件夹里再新建一个文件夹，通常情况下，你需要执行两次 mkdir。而加上 `-p` 选项后，你可以直接创建

假定我们要在当前目录下新建一个叫做 epi 的文件夹，并且在 epi 里再新建一个叫做 epi2 的文件夹，在以往是这么做的

```shell
$ mkdir epi
$ mkdir epi/epi2
```

甚至是

```shell
$ mkdir epi
$ cd epi
$ mkdir epi2
```

现在只需要

```shell
$ mkdir -p epi/epi2
```

## -v, --verbose

为每一个创建成功的文件夹打印一条消息

## --help

打印帮助信息

## --version

显示当前 mkdir 的版本
