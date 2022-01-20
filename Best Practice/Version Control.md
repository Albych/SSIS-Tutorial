# 概述

善用版本控制将会令项目开发事半功倍，在SSIS项目的开发中也是如此，无论是个人的项目开发对于历史修改的追溯还是团队项目开发的中的协作。  
本文将介绍 SSDT 软件集成的版本控制工具，如果想要了解完整的 Git 技术文档或使用方法，请参阅 [Reference 1](#reference)。  

# 简介
目前广泛使用的SSDT有两个版本，基于 Visual Studio 2017 和基于 Visual Studio 2019 版本的 SSDT，本教程以 VS 2017 为例。在安装 SSDT 时，版本控制的软件会默认安装。

# 操作介绍

## 界面介绍
打开本教程目录内的 SSIS 项目，此时窗口右侧默认会有团队资源管理器 (Team Explorer)  

![VS 主页中的团队资源管理器](/images/VersionControl1.png)
   
如果该窗口默认是关闭状态，可在 View (视图) - Team Explorer (团队资源管理器) 打开。  

下图是该界面的主页，如果当前未在主页，可点击图中图标1即可跳转至当前页面  

![团队资源管理器主页](/images/VersionControl2.png)  

图中图标2为连接管理，可以管理本地的受 Git 进行版本控制的项目以及项目的远程连接。相关内容将在 <a href="本地版本控制">本地版本控制</a>

## <a id="本地版本控制">本地版本控制</a>

  

# Reference
1. [Git_offical_doc](https://git-scm.com/doc)