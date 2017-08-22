017.03.03最新的CocoaPods安装教程

自己装过很多次CocoaPod,中间遇到过各种烦人的问题,也促使自己在不断的摸索中学习到了很多,总结一下,供大家学习研究,以下过程经本人新机测试,一路畅通无任何错误\(请严格按照下述方法来做\),中间有网络不好的可能会下载中断出错,只要从新执行一下命令就行了.

CocoaPods简介:

CocoaPods是一个用Ruby写的、负责管理iOS项目中第三方开源库的工具，CocoaPods能让我们集中的、统一管理第三方开源库，为我们节省设置和更新第三方开源库的时间。

CocoaPods安装:

下面就正式开始安装CocoaPods，命令中间可能有空格看不出来，建议直接复制粘贴执行；

因为Mac电脑自带Ruby环境，我们就只需打开终端开始动手。然而又因为默认情况下我们mac系统自带的Ruby环境版本比较低（大概是2.0.0版本的），但是现在安装CocoaPods需要2.2.2版本及以上的，所以我们不管三七二十一先直接先升级ruby。

打开终端：&gt;\_

1、查看当前Ruby版本（一般都是2.0.0）

```
ruby -v
```

2、升级Ruby环境，首先需要安装rvm（第一步要下载一些东西等两分钟左右）

```
curl -L get.rvm.io | bash -s stable 

source ~/.bashrc

source ~/.bash_profile
```

3、查看rvm版本（结果是1.27.0就对了）

```
rvm -v
```

4、列出ruby可安装的版本信息

```
rvm list known
```

5、安装一个ruby版本（这里我选择的是2.4.0版本，当然你也可以选择其他的）

```
rvm install 2.4.0
```

6、设置为默认版本

rvm use 2.4.0 --default

7、更换源（由于国内被墙，我们需要来修改更换源，把源切换至ruby-china；网上大多数是使用的[https://ruby.taobao.org的，这里不再建议使用的了，这是因为taobao](https://ruby.taobao.org%E7%9A%84%EF%BC%8C%E8%BF%99%E9%87%8C%E4%B8%8D%E5%86%8D%E5%BB%BA%E8%AE%AE%E4%BD%BF%E7%94%A8%E7%9A%84%E4%BA%86%EF%BC%8C%E8%BF%99%E6%98%AF%E5%9B%A0%E4%B8%BAtaobao) Gems 源已停止维护，现由 ruby-china 提供镜像服务）

```
sudo gem update --system

gem sources --remove https://rubygems.org/

gem sources -a https://gems.ruby-china.org/
```

8、为了验证你的Ruby镜像是并且仅是ruby-china，执行以下命令查看

gem sources -l

如果是以下结果说明正确，如果有其他的请自行百度解决

_**CURRENT SOURCES**_

[https://gems.ruby-china.org/](https://gems.ruby-china.org/)

9、这时候才正式开始安装CocoaPods

```
sudo gem install -n /usr/local/bin cocoapods
```

10、如果安装了多个Xcode使用下面的命令选择（一般需要选择最近的Xcode版本）

```
sudo xcode-select -switch /Applications/Xcode.app/Contents/Developer
```

11、安装本地库

```
pod setup
```

12、执行以上命令后会输出一句话：Setting up CocoaPods master repo，然后就是漫长的等待，并不是卡死了而是在下载文件（下载完成后大概800多兆）本人是在晚上安装的，网速稍好些，所以几分钟就好了，人品不好网络差的可能会等很久很久很久）

如果一直安装不成功请参考网友的总结:www.jianshu.com/p/426001721ed9

要查看文件下载进度的可以在打开一个终端窗口，输入以下命令回车执行

```
cd ~/.cocoapods

du -sh *
```

执行du -sh \*之后会显示已下载的文件大小，可以多次执行来监看下载进度，如果之前还有文件大小，后来变成0了，可能是网络问题，需要结束命令并从新执行pod setup

13、下载安装完成之后可执行下列命令检查是否可用（第一次使用可能要等一会）

```
pod search AFNetworking
```

14、CocoaPods的具体使用

新建一个Xcode工程，使用终端cd到工程目录下

创建Podfile文件：

```
pod init
```

之后就可以在项目目录里看到一个Podfile文件

打开Podfile文件：

```
open Podfile
```

添加：

pod 'AFNetworking'

保存后退出

开始下载：

```
pod install
```

我这里第一次都会出错，只要在此执行就好了，可能是网络或者其他的原因。

到此为止大功告成。

