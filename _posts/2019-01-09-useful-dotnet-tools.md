---
layout: post
title:  ".Net 实用工具"
date:   2019-01-09 21:23:01 +0800
categories: .NET
---

## 网络跟踪

编辑配置文件（`web.config`&#124;`app.config`&#124;`machine.config`），开启类级别的网络日志

```xml
<configuration>  
  <system.diagnostics> 
    <switches>  
      <add name="System.Net" value="Verbose"/>  
      <add name="System.Net.Cache" value="Verbose"/>  
      <add name="System.Net.Http" value="Verbose"/>  
      <add name="System.Net.Sockets" value="Verbose"/>  
      <add name="System.Net.WebSockets" value="Verbose"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```
### 参考
[如何：配置网络跟踪 &#124; Microsoft Docs](https://docs.microsoft.com/zh-cn/dotnet/framework/network-programming/how-to-configure-network-tracing)

## ILMerge
一个将多个程序集合并到一个程序集中。
### 参考
* [ILMerge/ilmerge-manual.md at master · dotnet/ILMerge · GitHub](https://github.com/dotnet/ILMerge/blob/master/ilmerge-manual.md)
* [c# - ILMerge Best Practices - Stack Overflow](https://stackoverflow.com/q/9376)

## 远程调试

[远程调试 &#124; Microsoft Docs - Visual Studio &#124; Microsoft Docs](https://docs.microsoft.com/zh-cn/visualstudio/debugger/remote-debugging?view=vs-2015)
