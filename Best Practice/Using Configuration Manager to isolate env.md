# Why

通常，企业除了正式使用的生产环境，还会存在一个或多个测试环境，用于开发和测试新的功能，而且生产环境和测试环境通常会是不同的路径或服务器。而针对此种情形，`SSIS` 项目提供了`Configuration Manager` **配置管理器**来隔离不同环境的参数，（尽管这个管理器会偶尔抽风

# What is?

通常，生产环境和测试环境除了服务器名称或路径不同外其他均相同，例如数据转换逻辑、关联方式等，为了更加方便的管理测试和生产环境，`SSIS` 的 `Configuration Manager` 可以通过简单的切换操作来在测试和生产环境之间进行转换。

>配置管理器只是对部分参数进行了环境隔离，项目中的包是同时供测试和生产进行使用的，请注意在项目**开发**时如果需要编译**生产**环境的部署文件，需要回退到 `Stable` 版本时的状态再进行编译。

可以通过两种方式进入配置管理器中
- 右键单击解决方案，并选择配置管理器 `Configuration Manager...`  
![1st Entry to CM](/images/ConfigurationManagerEntry1.jpg)
- 在工具栏中选择配置管理器下拉菜单，并选择配置管理器  
![2nd Entry to CM](/images/ConfigurationManagerEntry2.jpg)  

**配置管理器的主界面如下图**  

![配置管理器的主界面](/images/ConfigurationManagerMain.png)  
可以在配置管理器的界面中新增或修改配置环境
>有时通过工具栏的配置管理器快速切换到另一个环境时，项目的实际配置并没有切换过去，这时需要在配置管理器中进行手工切换，问题产生的原因未知。

# How to

## 创建新的配置

在配置管理器中点击 `Active solution configuration:` 或 `Configuration` 的配置下拉框,并选择`<New...>`  
![配置管理器主界面](/images/NewCM1.png)  
在弹出窗口中输入新的配置的名称，并选择是否从已有的配置复制设置。  
如果选择从现有的配置复制设置，则新的配置中的参数与所选择的设置相同。  
这里我们选择从 `Development` 配置复制。  
![创建配置页面](/images/NewCM2.png)  
点击完成即可创建  
![配置管理器新增配置后页面](/images/NewCM3.png)  

## 配置不同环境参数

在为不同的环境创建了不同的配置之后，我们按照实际情况将配置中的参数修改成对应环境的值。  
在界面中的解决方案浏览器 `Solution Explorer` 中打开项目的参数配置 `Project.params`  
![配置管理](/images/ProjectParams1.png)   

>如果 `Solution Exporer` 为关闭的状态，可点击 `View` - `Solution Explorer`，重新打开。  

此时，页面展示的是当前选择的配置所对应的参数。  
![配置页面](/images/ProjectParams2.png)  

其中 `Project.params` 页面中左上角的三个图标分别表示新建参数，删除参数和添加参数至配置中。  
首先我们添加一个参数，设置如上图所示。  
而后我们点击第三个图标将该参数添加至配置中。  
点击添加 `Add`，并选择我们想要利用配置来管理的参数并点击确定。

![配置不同配置参数页面](/images/ProjectParams3.png)  

此时我们可以看到 `G_Data_Folder` 参数针对不同的配置都有了一个值，我们将值修改成对应正确的。  

![配置参数](/images/ProjectParams4.png)  

点击确定之后可能会弹出一个提示框，提示我们需要保存项目，关闭提示框，点击功能栏中的保存全部 `Save All`或快捷键 `Ctrl` + `Shift` + `S`，这样配置就成功修改完成。  

![提示框](/images/ProjectParams5.png)  

这时我们切换不同的配置时，项目的参数就会随着配置文件进行变化  

![测试](/images/ProjectParams6.png)  
![正式](/images/ProjectParams7.png)  

同理，我们也可以配置数据库的连接字符串，参见 [Connectiong Manager using Connection String](Connectiong%20Manager%20using%20Connection%20String.md)。