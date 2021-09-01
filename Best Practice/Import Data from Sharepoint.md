# Before you go

尽管 Microsoft Sharepoint 支持用户创建和协作 Word, Excel, Powerpoint 等文档，但是原生的 SSDT 组件 OData 仅支持 Sharepoint 中的 List 类型的数据。
>有一些第三方的软件可以支持从 Sharepoint 获取 Excel 等数据，比如 [Cdata](https://www.cdata.com/drivers/sharepoint/)， 我并没有使用过，本文基于 SSDT 官方的组件。

# What is
>[Microsoft Lists](https://www.microsoft.com/en-us/microsoft-365/microsoft-lists) is an app that helps you track information and organize work.

`Microsoft List` 是微软推出的用于协同工作的工具，本质上是平面文件，具有某些 Excel 的特性，使用方式与 Excel 相类似。

# How to
1. 创建一个新的 List 。  
在 [Microsoft Lists](https://www.microsoft.com/en-us/microsoft-365/microsoft-lists) 按指引登录并创建一个新的 List。 
![NewList](/images/NewList.png)

2. `(Optional)` 配置 List，删除不需要的默认属性。  
新建的 List 会默认将第一个列 `Title` 设为必填列，可以在设置页面中更改列的属性等。  
![ListSetting](/images/ListSetting.png)
![SettingDetail](/images/SettingDetail.png)

3. 配置 SSIS 的数据源。  
使用 SSIS 中的 `OData Source` 组件来连接 List  
![SSISToolBoxOdata](/images/SSISToobBoxOdata.png)   
配置 OData 数据源,点击 `New` 创建新的连接。  
![](/images/ODataOverview.png)  
在连接配置页面填入 Sharepoint 地址与用户认证信息。  
![](/images/ODataConnection.png)  
配置完成以后返回前一个页面，在 Collection 中选择自己创建的 List 即可。
> Sharepoint 地址获取方法如下  
将创建的 List 地址的后半部分修改为 `_vti_bin/listdata.svc`。  
例如，如果 List 地址为  
`https://mydomian.sharepoint.com/personal/username/Lists/SSIS_Tutorial/AllItems.aspx`
则对应的连接地址为  
`https://mydomian.sharepoint.com/personal/username/_vti_bin/listdata.svc`

>如果在配置连接时报错如下图  
![](/images/NoSDK.png)  
原因是电脑尚未安装 Sharepoint 的组件，可到 [SharePoint Server 2013 Client Components SDK](https://www.microsoft.com/en-pk/download/details.aspx?id=35585) 下载并安装即可。  

4. 配置 Data Flow 并执行
>如果在 Design 模式下可以正常预览数据，但是在 Debug 时遇到了如下错误  
`OData Source [2]] Error: Cannot acquire a managed connection from the run-time connection manager.`  
`[SSIS.Pipeline] Error: OData Source failed validation and returned error code 0xC020801F.`  
是由于网络连接的原因，需要开启 TLS 1.2 来访问网页，方法如下，参考 [References ][References 4]<a href = "https://docs.microsoft.com/en-us/archive/blogs/dataaccesstechnologies/tls-issue-with-ssis-package-while-accessing-odata-source-like-dynamics-ax-online" title = "TLS Issue with SSIS package while accessing OData Source like Dynamics AX Online">4</a> [ref](https://github.com/Albych/SSIS-Tutorial/blob/main/Best%20Practice/Import%20Data%20from%20Sharepoint.md/#references):  
>1. 确保运行 SSIS 的电脑上已经安装了 .NET 4.6 或更新版本的 .NET Framework Runtime，可以从微软官网下载并安装。
>2. 修改注册表，强制使用 TLS 1.2 进行访问。

5. 至此，结束。


---
### References
1. [Mircosoft SharePoint Foundation REST Interface](https://docs.microsoft.com/en-us/previous-versions/office/developer/sharepoint-2010/ff521587)
2. [Reading SharePoint Lists with Integration Services 2017](https://www.mssqltips.com/sqlservertip/1733/reading-sharepoint-lists-with-integration-services-2017/)
3. [How to configure OData SSIS Connection for SharePoint Online](https://www.sqlshack.com/how-to-configure-odata-ssis-connection-for-sharepoint-online/)  
4. [TLS Issue with SSIS package while accessing OData Source like Dynamics AX Online](https://docs.microsoft.com/en-us/archive/blogs/dataaccesstechnologies/tls-issue-with-ssis-package-while-accessing-odata-source-like-dynamics-ax-online)

[References 4]:<https://docs.microsoft.com/en-us/archive/blogs/dataaccesstechnologies/tls-issue-with-ssis-package-while-accessing-odata-source-like-dynamics-ax-online> "TLS Issue with SSIS package while accessing OData Source like Dynamics AX Online"
