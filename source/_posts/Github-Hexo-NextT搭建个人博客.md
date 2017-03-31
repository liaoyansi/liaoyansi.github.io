---
title: Github+Hexo+NextT搭建个人博客
date: 2017-03-30 22:53:56
categories: 
- Hexo
tags: 
- Hexo
---
##  准备：配置开发环境
下载安装以下工具
- [Node.js](https://nodejs.org/en/download/)
- [git](https://git-scm.com/downloads)
- 安装git后将git的bin目录添加到环境变量path中
---
## 注册配置Github
### 新建一个git账号 
- [git网址](https://github.com/)

### 创建一个新仓库

  - **页面右上角 New repository**
  ![179110166410551.png](http://upload-images.jianshu.io/upload_images/3780097-7f158ffc8062f9dd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- **创建yourname.github.io，打勾表示名称可用**
 ![17130423106109148.png](http://upload-images.jianshu.io/upload_images/3780097-30f80535d658ff98.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> yourname为你的github用户名

### 配置SSH-Key
  - **安装git后**
  - **接着鼠标右键-点击Git Bash Here打开Git Bash    弹出以下窗口**
  ![1732010983113115.png](http://upload-images.jianshu.io/upload_images/3780097-0a9bd4900af49983.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  - **输入如下命令： **
```  
  $ git config --global user.name "Your Name"
  $ git config --global user.email "email@example.com"
  $ ssh-keygen -t rsa -C email@example.com  // 生成ssh
```
    >user.name 你的git用户名
    >user.email 你的git注册的邮箱

- **之后直接回车，不用填写东西。然后就在c盘->用户->登录用户名文件夹下生成一个目录.ssh ，里面有两个文件：id_rsa , id_rsa.pub**
![16261013101150106.png](http://upload-images.jianshu.io/upload_images/3780097-f8dc339ee28b6ad1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###  登陆github，进入刚刚新建的仓库，
  - **点击settings -> Deploy keys  －> add deploy key**
   ![170010238998110.png](http://upload-images.jianshu.io/upload_images/3780097-38929c222583d174.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- **打开之前生成的 id_rsa_pub 文件**
  - 复制文件中的内容粘贴到key中，
  - 选中 allow write access
  - 最后点击add key
  ![17900101109101109.png](http://upload-images.jianshu.io/upload_images/3780097-2cf3ad4de5bee243.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 测试是否成功  
- **在Git Bash中输入以下命令**
``` 
$ ssh -T git@github.com 
```

- 提示：
```
 Hi whitescholars/whitescholars.github.io! You've successfully authenticated, but GitHub does not provide shell access.
```
    证明校验成功。
---
## Hexo
**关于Hexo**
- 快速，简单而高效的静态博客框架

### 安装Hexo
- 在电脑的任意一个盘（位置自选）建一个文件夹，比如说的我的文件取名为blog.打开此文件夹，按住电脑的shift键，右击鼠标，选择在此处打开命令窗口(或者打开电脑的dos窗口，直接切换目录到blog文件夹)  
在命令窗口中输入：
``` 
$ npm install -g hexo-cli  //安装hexo
```

### 初始化Hexo
 ```
 $ hexo init
 ```

### 接着输入以下命令
```
  $ hexo g # 生成
  $ hexo s # 启动服务
```
![1729051110196111.png](http://upload-images.jianshu.io/upload_images/3780097-17f5d8421c0cf734.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 输入[http://localhost:4000](http://localhost:4000/) 即可查看网站。
![17290507311848.png](http://upload-images.jianshu.io/upload_images/3780097-ba677a35edf97070.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

---
## 安装Next主题
NexT 主旨在于简洁优雅且易于使用，所以首先要尽量确保NexT的简洁易用性。
这是一个扩展主题，由一个台湾学生[iissnan](https://github.com/iissnan)开发。主题秉承精于心，简于形的理念。

### 下载Next主题
```
$ cd your-hexo-site
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```
### 启用Next主题
- **打开_config.yml文件**
![1707011810913599.png](http://upload-images.jianshu.io/upload_images/3780097-27b4e8d35d53d7b3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- **设置 theme: next**
```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next
```

- **设置language: zh-Hans**
```
language: zh-Hans
```

- **配置 deploy**
```
 # Deployment
    ## Docs: https://hexo.io/docs/deployment.html
 deploy:
    type: git
    repository: git@github.com:yourname/yourname.github.io.git
    branch: master  
```
    repository为对应仓库的地址。注意仓库地址有两种形式。一种是https，一种是SSH。此处应该使用SSH形式的地址。

- **最后输入以下命令**
```  
    $ hexo clean # 清理
    $ hexo g  # 生成文件
    $ hexo d  # 部署文件
```

- **hexo d的时候可能会出现**
```
ERROR Deployer not found: git
```
    遇到这种情况，运行以下命令
```
$ npm install hexo-deployer-git --save
```

- **安装好后继续运行 **
```
$ hexo d 
```

- **到此安装完成，打开自己的博客看看吧**


![17860608738771.png](http://upload-images.jianshu.io/upload_images/3780097-8325982b866c682f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 附：
[Next官网](http://theme-next.iissnan.com/)
[主题作者iissnan的博客](https://github.com/iissnan)
[hexo官网](https://hexo.io/zh-cn/index.html)

过程中参考了：
[白衣秀才](http://www.cnblogs.com/penglei-it/p/Hexo.html)