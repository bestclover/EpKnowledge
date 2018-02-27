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
```

```
$ mkdir hello
$ chmod 600 hello
```

意思是，上面两个命令，等价

## -v, --verbose

为每一个创建成功的文件夹打印一条消息

## --help

打印帮助信息

## --version

显示当前 mkdir 的版本

---

未完待续
