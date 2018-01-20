# 当你拿到新 Mac 后

我自己昨天刚到了一台新的 MacBook Air，那就写点东西来配置 Mac 吧

## 卸载不用的 App

比如 iMovie, Pages, GarageBand 这样的

## 修改机子的名字

系统偏好设置 -> 共享 -> 电脑名称

修改好后敲回车确认

## 和 Win 一样的滚动鼠标

Mac 的默认鼠标滚动是和 Win 相反的

系统偏好设置 -> 鼠标 -> 取消打钩 **滚动方向：自然**

## 更改 root 密码

```bash
$ sudo passwd root
```

## 生成 ssh 密钥对

```bash
$ ssh-keygen
```

这个在 git clone 等操作会用到

## 安装开发工具集

```bash
$ xcode-select --install
```

带上 git, clang 等工具

## 安装包管理器 brew

这里的断句应该是：安装 包管理器

https://brew.sh/index_zh-cn.html，然后复制页面上的命令，粘贴到你的终端，执行

## 安装你需要的开发工具

```
$ brew install wget ...
```

命令根据自身需要来改

## 美化你的终端

```
$ brew install zsh zsh-completions
```

安装完成后先不要打开 zsh，接着安装 oh my zsh

https://github.com/robbyrussell/oh-my-zsh，在 oh my zsh 的开源仓库的 README 上有 via curl 的安装方式

```bash
$ sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

或者通过 wget

```bash
$ sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

接着看终端上的提示就行了

修改主题：

```bash
$ vim .zshrc
```

找到 ZSH_THEME 那一行，就看你喜欢什么主题，修改就好
