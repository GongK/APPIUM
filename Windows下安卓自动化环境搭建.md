
## Windows下安卓自动化环境搭建
- ####  node.js
1. 下载地址 [官网下载](http://nodejs.cn/download/)
2. 安装好后，在window下进入cmd输入 **node -v** 以及**npm -v**可查看到对应版本信息表示安装完成

- #### Python
[官网地址](https://www.python.org/)，版本号不管是2.x还是3.x的都可以，但是请注意是32位还是64的，默认安装路径为C盘的根目录。

Python环境变量配置：将C:\Python36\Scripts\和C:\Python36添加到path中，在cmd中输入python --version，出现版本等信息表示安装好了


- #### Appium
**安装方式下列二选一吧**
1. 因为某些原因，国内墙的存在我们安装一些东西的时候很慢，有梯子的同学可以采用以下安装方式：

   在cmd窗口输入：
```
npm install -g appium（-g表示全局安装）
```

   
2.实在没有梯子也可以用淘宝的镜像来安装，首先是镜像设置

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
安装好后输入来安装appium
```
cnpm install -g appium
```
- **Appium-Python-Client**
 
上一步安装的appium其实是appium server，现在来安装客户端
1. 通过命令行：
```
pip install Appium-Python-Client
```
安装好后可以继续输入

```
from appium import webdriver
```
控制台没有报错的话，就表示安装好了
2. Pycharm安装

一些童鞋喜欢用pycharm来下写代码，记得在Available Packages中添加这个包

- **JDK安装**

这里就不赘述JDK的安装了吧，大家应该都是很熟悉安装和环境变量的配置了

- **Android SDK**

网盘下载 [android sdk manager](http://tools.android-studio.org/index.php/sdk)安装后启动SDK manager.exe可以看到主界面

tools目录下必须勾选下载的有：Android SDK Tools、Android SDK Platform-tools、Android SDK Build-tools(选择一个即可，rc是预览版本)。

另外的android P（P是代号，带表安卓9版本）这样的都是模拟器，可以不勾选，用自己下的模拟器。如果要下载就必须勾选SDK Platform ,其余都是可选。

Extras目录里面都是可选的装备，看情况进行下载吧

- **Appium-doctor**

最后在npm里面安装appium-doctor来检测一下所需要的环境是否齐全

```
cnpm install appium-doctor -g
```
安装好后cmd控制台输入：appium-doctor即可，安装好了的都会打上绿色的√，没有就再安装吧
