---
layout: "post"
title: "iOS Project Directory"
date: "2018-04-21 14:00"
---

## 通用项目-目录结构
```
|____AppDelegate(程序入口)
  |____Base(全局基类:ViewController、API基类等，模块内部基类定义在Session里)
  |____Manager(全局管理模块:用户、网络监听、全局设置、地理位置等)
  |____Vendors(第三方服务商SDK)
  |____Library(封装后的第三方库)
  |____Macro(全局宏定义、常量定义)
  |____Resource(全局图片、声音、配置项等。PS:各模块资源分布在Sessions)
  |____Sessions(功能模块)
  | |____Session
  | | |____API(网络请求)
  | | |____Model(数据模型定义)
  | | |____Service(数据请求、处理、加工)
  | | |____Controller
  | | |____View(Cell\自定义View)
  | | |____Resource(该模块涉及的图片资源等)
```
