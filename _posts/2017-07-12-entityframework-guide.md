---
layout: post
title:  "EntityFramework指南"
date:   2017-07-12 09:49:01 -0600
categories: .NET
---

# EntityFramework

## 连接字符串设置

#### 在 Code First 模式下使用 app.config/web.config 文件中的连接字符串

```xml
<connectionStrings>
  <add name="DemoContext" 
       providerName="System.Data.SqlClient" 
       connectionString="Server=.;Database=MyDemo;Integrated Security=True;"/>
</connectionStrings>
```
如果连接字符串的名称与上下文的名称（带或不带命名空间限定）相同，则使用无参数构造函数时 DbContext 会找到该连接字符串。

```c#
public class DemoContext : DbContext 
{ 
    public DemoContext() 
    { 
    } 
}
```
如果连接字符串名称与上下文名称不同，则可通过将连接字符串名称传递给 DbContext 构造函数，指示 DbContext 在 
Code First 模式下使用此连接

```c#
public class MyContext : DbContext 
{ 
    public MyContext() 
        : base("DemoContext") 
    { 
    } 
}
```
参考 ：https://msdn.microsoft.com/zh-cn/data/jj592674 




## 使用Entityframework连接MySQL

### 安装

下载并安装 [MySQL for Visual Studio](https://dev.mysql.com/downloads/windows/visualstudio/) 和 [MySQL Connector/Net ](https://dev.mysql.com/downloads/connector/net/)

Note: 

1. 下载需要注册Oracle账号

1. 先安装MySQL for Visual Studio, 后安装MySQL Connector/Net。  具体请参考[MySQL for Visual Studio Documentation](https://dev.mysql.com/doc/visual-studio/en/visual-studio-install.html)

1. 安装MySQL Connector/Net会在machine.config下添加以下内容

  ```xml
    <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
        <dependentAssembly>
          <assemblyIdentity name="MySql.Data" publicKeyToken="c5687fc88969c44d" culture="neutral" />
          <bindingRedirect oldVersion="6.7.4.0" newVersion="6.9.6.0" />
        </dependentAssembly>
        <dependentAssembly>
          <assemblyIdentity name="MySql.Data.Entity" publicKeyToken="c5687fc88969c44d" culture="neutral" />
          <bindingRedirect oldVersion="6.7.4.0" newVersion="6.9.6.0" />
        </dependentAssembly>
        <dependentAssembly>
          <assemblyIdentity name="MySql.Web" publicKeyToken="c5687fc88969c44d" culture="neutral" />
          <bindingRedirect oldVersion="6.7.4.0" newVersion="6.9.6.0" />
        </dependentAssembly>
      </assemblyBinding>
    </runtime>
  ```
  
  ```xml
    <system.data>
      <DbProviderFactories>
        <add name="MySQL Data Provider" invariant="MySql.Data.MySqlClient" description=".Net Framework Data Provider for MySQL" type="MySql.Data.MySqlClient.MySqlClientFactory, MySql.Data, Version=6.9.6.0, Culture=neutral, PublicKeyToken=c5687fc88969c44d" />
      </DbProviderFactories>
    </system.data>
  ```

