---
layout: single
title:  "Asp.net Bundle 指南"
date:   2017-07-12 09:49:01 +0800
categories: .NET
---

## 资源

* [Learn About ASP.NET MVC](https://www.asp.net/mvc)

## Bundle

1. 安装 *Microsoft.AspNet.Web.Optimization* package包
1. 新建*App_Start\BundleConfig.cs*类


  ```c#
  using System.Web.Optimization;
  
  namespace Excellentcourse.App_Start
  {
      public class BundleConfig
      {
          public static void RegisterBundles(BundleCollection bundles)
          {
              bundles.Add(new StyleBundle("~/Content/css").Include(
                  "~/Content/themes/icon.css",
                  "~/Content/themes/color.css",
                  "~/Content/themes/default/easyui.css",
                  "~/Content/Custom.css"
                  ));
              bundles.Add(new ScriptBundle("~/Scripts/js").Include(
                  "~/Scripts/jquery.min.js",
                  "~/Scripts/jquery.easyui.min.js",
                  "~/ckeditor/ckeditor.js"
                  ));
          }
      }
  }
  ```
  
1. 在Global.asax下的Application_Start()中注册Bundle

  ```c#
      public class MvcApplication : System.Web.HttpApplication
      {
          protected void Application_Start()
          {
              AreaRegistration.RegisterAllAreas();

              BundleConfig.RegisterBundles(BundleTable.Bundles);
              WebApiConfig.Register(GlobalConfiguration.Configuration);
              FilterConfig.RegisterGlobalFilters(GlobalFilters.Filters);
              RouteConfig.RegisterRoutes(RouteTable.Routes);
          }
      }
  ```

1. 在服务端页面上加入以下脚本


  ```html
  <head>
      <meta charset="utf-8" />
      <title>@ViewBag.Title</title>
      @Styles.Render("~/Content/css")
      @Scripts.Render("~/Scripts/js")
  </head>
  ```
  
参考: [Bundling and Minification](https://www.asp.net/mvc/overview/performance/bundling-and-minification)

