# appium下IOS11.3真机环境搭建
mac系统下的appium环境搭建（python）   
简介：appium是app自动化测试主流工具之一，此次介绍的为mac系统下的搭建过程。   
工具：MacOSX、VPN、IOS真机、pycharm   
准备好了以上工具就开始吧！
### xcode   
自行苹果商店搜索吧，请提前准备好最新系统，我这里是用的9.3的xcode
### python3.6
现在是18年4月20号，我安装的是3.6.5，直接去python官网下载安装即可
### appium
appium安装有两种，第一种是命令行版本（针对python脚本的），这里安装的其实是server端，client端要在python里面安装；第二种是桌面版的（直接下载安装包安装即可），桌面版是集成了server和client，所以不需要额外安装了，我这里推荐两种都安装   
**命令行安装：npm install -g appium**
### pycharm
个人学习的话社区版就可以了，专业版要破解，有想破解的童鞋请自己google，不过还是请尊重版权，购买支持正版吧。   
pycharm下可以使用虚拟环境，我这里不推荐使用，我因为安装了python3.6.5版本，所以我就使用的是当前版本，当然mac系统自带2.7.10版本，有想使用的还是可以使用。   
**环境配置路径**：File->Default setting->Project interpreter->add->Existing environment   
在里面填写下列路径：/Library/Frameworks/Python.framework/Versions/3.6/bin/python3.6    
用**系统自带python**的童鞋填：/usr/bin/python2.7   
做好这些以后就要安装一些库了，这里直接使用pycharm来安装，点击+号按钮后输入appium-python-client 选择正确的库安装即可，命令行也可以：pip3 install Appium-Python-Client   
![image](https://github.com/GongK/APPIUM/blob/master/%E6%B7%BB%E5%8A%A0%E5%BA%93.png)   

---

## 命令行安装的东西
- brew安装   

<html>
终端输入：usr/bin/ruby -e "$(curl -fsSL  https://raw.githubusercontent.com/Homebrew/install/master/install)"  
</html>

 
验证：**brew -v**
- Carthage   
终端输入：**brew installCarthage**
- libimobiledevice   
终端输入：**brew install libimobiledevice** --HEAD   

- nodejs
下载安装包安装，[下载地址](https://nodejs.org/en/download/)
- ios-deploy    
终端输入：**npm install -g ios-deploy**   
- xcpretty   
终端输入：**gem install xcpretty**   
- 安装appium-doctor来验证appium环境   
 终端输入：npm install appium-doctor 安装后     
输入appium-doctor --ios 来验证ios环境是否完成，出现以下信息表示完成   
![image](https://github.com/GongK/APPIUM/blob/master/appium-doctor.png)

