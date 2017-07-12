---
layout: post
title:  "log4net指南"
date:   2017-07-12 09:49:01 +0800
categories: .NET
---

# Log4Net
记录在使用log4net过程中遇到的问题

## 配置
#### 使用`BasicConfigurator.Configure() `方法
```C#
using Com.Foo;
using log4net;
using log4net.Config;

public class MyApp 
{
    private static readonly ILog log = LogManager.GetLogger(typeof(MyApp));

    static void Main(string[] args) 
    {
        BasicConfigurator.Configure();
        log.Info("Entering application.");
        log.Info("Exiting application.");
    }
}
```
这种方式是最简单方式，不需要任何配置文件，但是这种方式的配置是硬编码的。
#### 使用应用程序配置文件

```C#
using Com.Foo;
using log4net;
using log4net.Config;

public class MyApp 
{
    private static readonly ILog log = LogManager.GetLogger(typeof(MyApp));

    static void Main(string[] args) 
    {
        XmlConfigurator.Configure();
        log.Info("Entering application.");
        log.Info("Exiting application.");
    }
}
```

这种方式需要在应用程序配置文件(app.config/web.config)中添加log4net配置。


1. 首先，为了在配置文件中嵌入新的节点，要先在configSections节点下定义，并指定`log4net.Config.Log4NetConfigurationSectionHandler`将被用来解析该 节点，类型名必须为完全限定名，逗号后面是程序集名。
2. 添加`log4net`节点，并进行自定义的配置。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="log4net" type="log4net.Config.Log4NetConfigurationSectionHandler, log4net" />
    </configSections>
    <log4net>
        <appender name="ConsoleAppender" type="log4net.Appender.ConsoleAppender" >
            <layout type="log4net.Layout.PatternLayout">
                <conversionPattern value="%date [%thread] %-5level %logger [%ndc] - %message%newline" />
            </layout>
        </appender>
        <root>
            <level value="INFO" />
            <appender-ref ref="ConsoleAppender" />
        </root>
    </log4net>
</configuration>
```

#### 使用自定义配置文件

XmlConfigurator 可以直接读取xml文件并使用该文件配置log4net，XmlConfigurator接受System.IO.FileInfo对象的方法可以用来指定自定义文件。

```C#
using Com.Foo;
using log4net;
using log4net.Config;

public class MyApp 
{
    private static readonly ILog log = LogManager.GetLogger(typeof(MyApp));

    static void Main(string[] args) 
    {
        XmlConfigurator.ConfigureAndWatch(new FileInfo("log4net.config"));
        log.Info("Entering application.");
        log.Info("Exiting application.");
    }
}
```
需要新建一个log4net.config文件，并且将该文件设置成`始终复制到输出目录`

```xml
<?xml version="1.0" encoding="utf-8" ?>
<log4net>
    <appender name="ConsoleAppender" type="log4net.Appender.ConsoleAppender" >
        <layout type="log4net.Layout.PatternLayout">
            <conversionPattern value="%date [%thread] %-5level %logger [%ndc] - %message%newline" />
        </layout>
    </appender>
    <root>
        <level value="INFO" />
        <appender-ref ref="ConsoleAppender" />
    </root>
</log4net>
```
