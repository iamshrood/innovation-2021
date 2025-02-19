 

 

# **易玩团项目介绍**文档

 



 ![logo](https://i.loli.net/2021/11/04/Um9ore8sxXP7dyA.png)

 

 



## `参赛选手：康帅 杨桢 杨贺 张晨博`

 

###  体验版小程序码：



 ![okS7J5YPDyv9T1RDp5UzV9dtJ8Sk](https://i.loli.net/2021/11/04/BZJHCE4Ixjsp8cG.jpg)

## 1.   作品介绍

### 1.1开发背景

随着中国互联网技术的不断地发展，手机社交已经成为我们日常生活里不可或缺的一部分。截至2020年3月，我国手机网民规模为8.97亿，我国网民使用手机上网的比例高达99.3%。在我国网民群体中，学生最多占比26.9%。网络社交对我们生活的影响越来越明显，调查结果显示，96.03% 的学生认为网络社交对其生活学习有重要影响，但随之而来的孤独感也不乏见。74.17% 的学生认为现实生活中的孤独感对生活有一定影响，13.25% 的学生认为有很大影响。我们基于此出发，通过易玩团呼吁大学生“走出去”，参加社会活动，增强实际中的沟通交往能力。

### 1.2设计架构

![技术架构图](https://i.loli.net/2021/10/25/T9pgCHY1w42Mrqa.gif)

![系统结构图](https://i.loli.net/2021/11/04/HetYhdr1ToplwJZ.png)

## 2. 实现功能

小程序设计帮助使用者利用本程序寻找有相同诉求的同学。根据使用者的需求发起易玩团或参与易玩团。与其他同学进行交流，从而线上沟通，线下社交。扩大自己的社交圈。

### 2.1前端部分

#### 1. 用户注册登录

用户可以通过微信登录快速创建账号，然后正常使用本小程序。登录时会上传用户的昵称及头像，并且初始化网易云信IM服务。

#### 2．浏览易玩团

浏览易玩团分为分类浏览以及地图浏览两种方式。

分类浏览即首页的分四大板块的浏览方式，可以通过限定学习、出行、饮食以及娱乐四种分类中的任意一种并且以卡片列表的形式来浏览易玩团。卡片内容包含易玩团的简要内容、易玩团时间、地点以及易玩团当前的参与人数。

地图浏览方式即在中心为用户位置的地图上显示周围的易玩团，用户可以直接点击地图上的头像来查看其他用户发布的易玩团。

在浏览到心仪的易玩团后，可以点击进入来查看易玩团的具体信息，包含易玩团的地点、时间、图片等信息。同时也可以在详情中直接加入易玩团。

#### 3．发布易玩团

易玩团的分类有四种：拼学习、拼出行、拼饮食以及拼娱乐。发布时会需要用户填写易玩团表单，来确定易玩团的基本内容，并通过腾讯位置服务来确定易玩团的地点，再根据相应选择的板块进行一个简要描述，如选择拼学习模块需说明学习的主要内容。用户成功发布后，便可在主页看到刚刚发布的易玩团。

#### 4．关注用户

在浏览易玩团时，你也可以直接关注发布易玩团的用户，并且还可以与其发起聊天，畅谈你们感兴趣的话题。并且还可以去个人中心在关注列表中看到你关注的其他用户，以及关注你的用户。

#### 5．历史及收藏

用户可以在个人中心的浏览历史中以卡片列表的形式看到刚刚浏览过的易玩团。也可以在个人中心的我的收藏中，看到用户自己所收藏的易玩团。

#### 6．用户聊天

得益于网易云信IM服务的支持，用户可以与其他用户在易玩团中畅谈无阻，在易玩团详情中，点击用户头像即可发起聊天，用户间可以讨论易玩团的详情以及任何感兴趣的话题。

### 2.2后端部分

#### 1.权限管理

使用SpringSecurity框架对权限进行管理，登录时将用户名密码表单方式提交到/login_p，随后根据数据库数据判断该用户具有的角色，然后查询这个角色所拥有的权限（也就是访问路径），如果该角色拥有该权限则放行，反则不然。

#### 2.用户管理

对用户可以进行修改基本信息，包括密码。并且可以为用户分配角色，使得用户具有该角色的所有权限。

#### 3.帖子管理

通过记录用户发帖地点的经度纬度，从而使得小程序端可以在地图定位，并且定位图标是由后台来完成的，使用java.awt.graphics将用户头像切割为圆形，与之前设置好的背景图案重合，完成了定位显示。并且根据经纬度可以判断当前位置与帖子的距离，超出规定范围的帖子不会显示在地图上。并且管理员拥有审核帖子，删除帖子的权限，审核不通过的帖子将不会显示在小程序端。

#### 4.前台用户管理

一个新小程序用户登录时，小程序端向后台发来js_code，后端使用js_code访问微信服务端，获取到用户的openid与token，随后将获取到的内容返回给小程序端，小程序端又可以拿着这些信息获取到用户的所有基本信息，并上传至后台端，保存入数据库中。管理员可以对用户的基本信息，关注粉丝进行查看，并且可以删除用户。

## **3.**使用场景

易玩团是一款专注于解决大学生社交难题的小程序。便利了大学生的日常生活。在学习、娱乐、出行、吃饭等方面为使用小程序的大学生用户发布诉求，提供寻找志同道合好友的服务。

### 3.1作品优势

随着拼多多的理念深入人心。我们将“拼”的概念引入社交当中。既可以缓解用户的社交孤独的情况。也可以节省用户的娱乐、出行成本。同时将地图定位引入小程序中，使得用户可以根据地图浏览其用户的易玩团并加入其中，提升了用户使用时的搜索效率。应用前景

### 3.2业务模式

本系统以免费的发帖为基础，同时可以接入附近的商家作为最初的收益来源。从长期来看，可以在应用中接入部分不影响用户体验的广告。同时可以与相关公司进行合作，如与类似“滴滴出行”等公司进行合作简化用户拼团流程。

### 3.3目标用户

以在校大学生为主，用来保证拼团的可靠性与用户身份的认证。

## **4.**功能展示

#### 4.1用户注册登录

用户在登录界面点击登录会先触发微信登录，并且会查询是否存在该用户，若存在登录成功，如果不存在，则会获取用户头像昵称等信息上传到数据库，并为用户创建网易云信账号。登录成功后会自动跳转到首页。

如果用户尝试跳过登录使用本小程序，任何请求之前都会进行登录判断，确保用户进行操作时保留登录状态，若用户未登录，则跳转到登录页面。



|      |                                                              |      |                                                              |
| ---- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
|      | ![应用程序  中度可信度描述已自动生成](https://i.loli.net/2021/10/25/LeS3VTPpyUEmMuv.gif) |      | ![图形用户界面, 文本, 应用程序  描述已自动生成](https://i.loli.net/2021/10/25/Guo6V8nZ7J4O2Cx.gif) |
|      |                                                              |      |                                                              |

 	        **图4.1.1 登录页            						图4.1.2 登录时获取用户信息**

 








#### 4.2首页浏览易玩团

首页包含全部以及拼学习、拼出行、拼美食和拼娱乐四种分类的易玩团列表，用户可以选择自己感兴趣的分类进行查看，易玩团以卡片形式显示，并包含简要信息的展示。且长列表被封装成组件，通过传入type类型值来区分列表的分类。

![img](https://i.loli.net/2021/11/04/g7hsiRFWKYUucxt.png)

###  4.3发布易玩团

易玩团的分类共拼学习、拼出行、拼美食和拼娱乐四种分类，通过点击首页右上角的发布按钮，选择要发起的易玩团分类，并填写相应的表单，即可成功发布易玩团。不同的分类拥有不同的定制化内容，如拼学习会要求填写学习的内容。表单组件部分使用uView的选择器，图标则是使用iconfont的字体图标，方便控制图标的颜色和大小。



|      |                                                              |      |                                                              |
| ---- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
|      | ![图形用户界面, 文本, 应用程序, 聊天或短信  描述已自动生成](https://i.loli.net/2021/10/25/Uk6x2J4sAt7GlKZ.gif) |      | ![图形用户界面, 文本, 应用程序  描述已自动生成](https://i.loli.net/2021/10/25/uQ9hq4CzyAnVp2D.gif) |
|      |                                                              |      |                                                              |

### 4.4易玩团详情

易玩团详情包含易玩团的标题、描述、时间、地点以及相应分类的定制化内容等，同时也可以看到易玩团的参与者。

![手机屏幕截图  描述已自动生成](https://i.loli.net/2021/10/25/FohZBweyNHWmPz8.gif)

 

 

 

 

### 4.5消息通知

消息通知页包含聊天会话及各类通知的分类查看，用户点击聊天会话时可以继续与其他用户畅谈，聊天的实现依托于网易云信IM服务的接入，以及发布订阅者模式的使用保证用户第一时间获取聊天数据回显。



| ![图形用户界面, 文本, 应用程序, 聊天或短信  描述已自动生成](https://i.loli.net/2021/10/25/tZqzXaObFDdxSQP.gif) | ![图形用户界面, 文本, 应用程序, 聊天或短信  描述已自动生成](https://i.loli.net/2021/10/25/ypGPjH3cegqvJOn.gif) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

 

###  6.地图浏览

用户可以通过地图浏览自身定位周围3.5公里范围内的易玩团，同时也可以自由查看全国各地的易玩团。当浏览到合适的易玩团时，可以点击进入详情查看。

![工程绘图  描述已自动生成](https://i.loli.net/2021/10/25/ikNDmsq8RYGLnMp.gif)

### 4.个人中心

个人中心包含用户当前的关注以及粉丝列表、我的易玩团和联系客服等功能，用户在这里可以查看自己浏览过或收藏过的易玩团，也可以查看自己发布或参与的易玩团。

![图形用户界面, 应用程序  描述已自动生成](https://i.loli.net/2021/10/25/hKkFvucx64UGEea.gif)

![图形用户界面, 文本, 应用程序, 聊天或短信  描述已自动生成](https://i.loli.net/2021/10/25/wgWJAc61tEmhvU9.gif)

