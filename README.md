# appium下IOS11.3真机环境搭建

[Windods下安卓自动化环境搭建](https://github.com/GongK/APPIUM/blob/master/Windows%E4%B8%8B%E5%AE%89%E5%8D%93%E8%87%AA%E5%8A%A8%E5%8C%96%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.md)
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
**命令行安装：==npm install -g appium==**
### pycharm
个人学习的话社区版就可以了，专业版要破解，有想破解的童鞋请自己google，不过还是请尊重版权，购买支持正版吧。   
pycharm下可以使用虚拟环境，我这里不推荐使用，我因为安装了python3.6.5版本，所以我就使用的是当前版本，当然mac系统自带2.7.10版本，有想使用的还是可以使用。   
**环境配置路径**：==File->Default setting->Project interpreter->add->Existing environment==   
在里面填写下列路径：==/Library/Frameworks/Python.framework/Versions/3.6/bin/python3.6==  
用**系统自带python**的童鞋填：==/usr/bin/python2.7==   
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


---
## WebDeiverAgent
- 一定要下载最新的：[WebDriverAgent](https://github.com/facebook/WebDriverAgent)，下载完成后在终端输入以下命令：

1. **cd /WebDriverAgent   （自己输自己下载存放的文件夹路径，我这里只是演示）**   
2. mkdir -p Resources/WebDriverAgent.bundle
3. **执行这个  ./Scripts/bootstrap.sh**一定要VPN连上了，运行无报错才可以   

- 用xcode打开WebDriverAgent.xcodeproj文件进行配置   
图中需要配置的地方用红色箭头标准了，bundle identifier自己一定要设置一个不同的，Team请配置自己的苹果账号，勾选上面的automatically   
![image](https://github.com/GongK/APPIUM/blob/master/xcode%E9%85%8D%E7%BD%AE1.png)   完成这一步就可以在模拟器运行了，但是要在真机上运行还需要下面的步骤。  
- **在此页面上点击bundle settings->下拉到code signing identity，将里面的Don‘t code sign选为IOS Developer，这步很重要，如果不做就会出现安装包损坏的提示**
- 在targets里面选择webdriveragentrunner，在这里配置好账号后勾选上面的automatically，在菜单栏Product->Scheme->webdriveragentrunner,在选择真机，点击Product->Test开始真机运行，手机在此期间不能锁屏，在手机设置->描述文件->信任app，确保手机wifi和电脑是连接的同一个路由器信号，成功运行的标准是在控制台打印出了**IP和8100端口**类似：192.168.1.3:8100，进行到这里就完成了80%，请继续往下看
- 我们安装好了appium的两个版本，这里面其实是自带WebDriverAgent，存放的路径分别是：
1. 命令行版本路径：/usr/local/lib/node_modules/appium/node_modules/appium-xcuitest-driver/WebDriverAgent 
2. 桌面版路径：/应用程序/Appium/Contents/Resources/app/node_modules/appium/node_modules/appium-xcuitest-driver/WebDriverAgent  
**分别进入这两个路径在终端下删除Webdriveragent文件夹，例：cd /usr/local/lib/node_modules/appium/node_modules/appium-xcuitest-driver   
**rm -rf WebDriverAgent**   
再将之前下载配置好的WebDriveragent压缩放在这个路径下解压**  
#### 启动
- 命令行版本启动，appium -U 自己手机的UUID
