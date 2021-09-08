# What is

对于 `SSIS` 项目中的敏感数据，如数据库密钥、人为设定为敏感信息的变量等，`SSDT` 提供了数据加密的功能，而该功能是必选的，当然，一共提供了五种加密的等级来进行选择  

- DontSaveSensitive
- EncryptAllWithPassword
- EncryptAllWithUserKey
- EncryptSensitiveWithPassword
- EncryptSensitiveWithUserKey  

关于这些不同等级的详细信息可以参考 [Reference 1](#reference)。  
设定了数据加密可以保证项目中的敏感数据不会泄露，但是同时也会带来一定的不便，例如开发项目的账号与生产环境执行任务的账号并非同一个，这时如果我们设定了将数据进行加密，在其他环境运行任务时会导致无法解密敏感信息导致失败。

# How To

为了解决由于数据加密导致的无法在其他环境中解密信息的问题，我们可以采用使用配置管理器 `Configuration Manager` 来保存如数据库链接信息等敏感数据，但是这种方法的缺点也很明显，敏感信息被明文保存在配置文件中，造成安全隐患。  
具体实现方法请参考 [Using Configuration Manager to isolate env](Using%20Configuration%20Manager%20to%20isolate%20env.md) 及 [Connectiong Manager using Connection String](Connectiong%20Manager%20using%20Connection%20String.md)

---
# Reference  
1. [Access Control for Sensitive Data in Packages](https://docs.microsoft.com/en-us/sql/integration-services/security/access-control-for-sensitive-data-in-packages?view=sql-server-ver15)
