# Purpose

本文介绍如何使用配置管理器 `Configuration Manager` 来参数化连接器，文中以文件连接器为例，而数据库的连接器也是同样的道理。

# How To

首先在解决方案浏览器 `Solution Explorer` 中右键单击连接管理器 `Connection Manager` 文件夹，并选择新建连接管理器 `New Connection Manager`  
![新建连接器](/images/NewConn1.png)  
选择文件类型，并点击添加，设置文件路径即可。  
![新建连接器](/images/NewConn2.png)  
本次创建的是项目的连接管理器 `Project Connction`，即当前项目内的所有包 (`Package`) 都默认包含该连接器，与之相对的是包连接管理器 `Package Connection`，即针对特定的包创建的管理器，项目的连接管理器和包的连接管理器可以互相转换。  
打开任意一个包，右键单击下方连接管理器窗口中新创建的连接器，并选择参数化 `Parameterize...`
![新建连接器](/images/NewConn3.png)  
选择属性 (`Property`) 为连接字符串 (`ConnectionString`)，并使用我们之前已经创建好的名为 `G_Data_Folder` 的参数。  
![新建连接器](/images/NewConn4.png)  
配置完成之后，我们就可以在连接管理器窗口中看到该连接名称前多了 *`fx`* 符号，表示该连接器是由参数控制的。  
![新建连接器](/images/NewConn5.png)  
