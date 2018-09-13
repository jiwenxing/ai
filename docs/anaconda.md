
# 使用 anaconda 管理 python 开发环境
---

## 烦人的 python 环境问题

一个 python 环境中需要有一个解释器负责解释运行 python 脚本， 另外还有一个包集合（site-packages 文件夹）。

针对解释器，我们知道 python 的版本大概分为 2.x 和 3.x， 而这两个版本之间互相不兼容，由于这个历史原因给开发带来的困扰我相信很多童鞋都经历过；而包集合中包含了自带的包和第三方包, 第三方包一般通过 pip 或者 easy_install 来下载，当本地只有一个 python 环境，那所有程序用到的各种包都只能放到同一个环境中从而导致环境混乱，这样也给开发带来了很多不便。

以下问题你是不是也遇到了呢！

- 到底该装 Python2 呢还是 Python3 ？
- 为什么安装 Python 时总是出错？
- 怎么安装工具包呢？
- 为什么提示说在安装这个工具前必须先安装一堆其他不明所以的工具？

## 为什么用 Anaconda

**Anaconda** 完美的解决了上面这个问题，它通过管理工具包、开发环境、Python版本，大大简化了你的工作流程，不仅可以方便地安装、更新、卸载工具包，而且安装时能自动安装相应的依赖包，同时还能使用不同的虚拟环境隔离不同要求的项目。

Anaconda 其实就是一个开源的 Python 发行版本，只不过其包含了（提前集成了）conda、Python等一堆常用的安装好的工具包。

## 什么是 conda

conda 是开源包（packages）和虚拟环境（environment）的管理系统，也就是说 Anaconda 是通过 conda 实现的虚拟环境管理。

- packages 管理    
可以使用 conda 来安装、更新 、卸载工具包 ，并且它更关注于数据科学相关的工具包。在安装 anaconda 时就预先集成了像 Numpy、Scipy、 pandas、Scikit-learn 这些在数据分析中常用的包。另外值得一提的是，conda 并不仅仅管理 Python 的工具包，它也能安装非 python 的包。比如在新版的 Anaconda 中就可以安装R语言的集成开发环境 Rstudio。

- 虚拟环境管理    
在conda中可以建立多个虚拟环境，用于隔离不同项目所需的不同版本的工具包，以防止版本上的冲突。对纠结于 Python 版本的同学们，我们也可以建立 Python2 和 Python3 两个环境，来分别运行不同版本的 Python 代码。

## 安装 Anaconda

从 [Anaconda 官网](https://www.anaconda.com/download/#macos) 下载64位 macOS 版本按照提示安装，安装结束后在 `~/.zshrc` 中追加环境变量如下，注意我是直接安装到了磁盘根目录，因此路径直接是`/anaconda3/bin`。

> export PATH=$HOME/bin:/usr/local/bin:$PATH:/usr/local/sbin:/anaconda3/bin

修改保存完后，在 terminal 执行 `source ~/.zshrc` 使设置立即生效，然后便可以在 terminal 中执行各种操作如下：


```bash
$ conda --version // 查看当前版本
$ conda upgrade --all // 升级所有依赖
$ conda list // 列出当前环境的所有包

// 创建自己的开发环境
$ conda create -n learn python=3 // 创建一个叫 learn 的虚拟环境
$ conda env list  // 列出conda管理的所有环境
$ source activate learn // 切换到刚刚创建的虚拟环境

// 常用命令
$ conda install requests // 安装requests包
$ conda remove requests // 卸载requets包
$ conda install numpy=1.10 // 限定版本安装
$ conda remove -n learn --all // 删除learn环境及下属所有包
$ conda update requests // 更新requests包
$ conda  search search_term // 模糊查询包
$ conda env export > environment.yaml // 导出当前环境的包信息
$ conda env create -f environment.yaml // 用配置文件创建新的虚拟环境

```

如果还需要一个 python2.x 版本的环境，则直接执行 `$ conda create -n learn-py2 python=2.7` 这时会创建一个名称为 learn-py2 的虚拟环境，并指定 python 版本。这时这个环境只有一些自带的官方包，是一个比较干净的环境，我们可以按照需要自行安装第三方包。

导入导出环境，可以将包信息存入yaml文件中，当需要重新创建一个相同的虚拟环境时很方便，类似于 docker。


## 总结

Anaconda 的虚拟环境隔离功能可以和 eclipse 的 workspace 类比，我们使用 eclipse 开发 Java 项目时，有的系统要求 JDK6，有的要求 JDK8，我们可以通过创建不同 workspace 去分别设置编译环境来实现开发环境切换。而它的包管理功能则类似于集成了 Maven 能力。

当然 anaconda 除了虚拟环境和包管理功能之外还在于其丰富数据分析包，这里主要介绍了用 anaconda 管理自己的开发环境, 后面会对其它功能另行介绍。
