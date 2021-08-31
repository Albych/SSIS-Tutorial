# Before you go

尽管 Microsoft Sharepoint 支持用户创建和协作 Word, Excel, Powerpoint 等文档，但是原生的 SSDT 组件 OData 仅支持 Sharepoint 中的 List 类型的数据。
>有一些第三方的软件可以支持从 Sharepoint 获取 Excel 等数据，比如 [Cdata](https://www.cdata.com/drivers/sharepoint/)， 我并没有使用过，本文基于 SSDT 官方的组件。

# What is
>[Microsoft Lists](https://www.microsoft.com/en-us/microsoft-365/microsoft-lists) is an app that helps you track information and organize work.

`Microsoft List` 是微软推出的用于协同工作的工具，本质上是平面文件，具有某些 Excel 的特性，使用方式与 Excel 相类似。

# How to
1. 创建一个新的 List 。  
在 [Microsoft Lists](https://www.microsoft.com/en-us/microsoft-365/microsoft-lists) 按指引登录并创建一个新的 List。  
![NewList](images\New List.png)  



---
### References:  
1. [Mircosoft SharePoint Foundation REST Interface](https://docs.microsoft.com/en-us/previous-versions/office/developer/sharepoint-2010/ff521587)
2. [Reading SharePoint Lists with Integration Services 2017](https://www.mssqltips.com/sqlservertip/1733/reading-sharepoint-lists-with-integration-services-2017/)
3. [How to configure OData SSIS Connection for SharePoint Online](https://www.sqlshack.com/how-to-configure-odata-ssis-connection-for-sharepoint-online/)
4. [TLS Issue with SSIS package while accessing OData Source like Dynamics AX Online](https://docs.microsoft.com/en-us/archive/blogs/dataaccesstechnologies/tls-issue-with-ssis-package-while-accessing-odata-source-like-dynamics-ax-online)
