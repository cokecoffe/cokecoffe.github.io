---
layout: "post"
title: "Android Java Code Style"
date: "2018-04-25 18:29"
categories: AppTeam
---

# Android-Java Code Style

这篇编码风格指南概括了谷歌和阿里的编码风格，并做了增删修改，作为平安社区Android-Java的编码规范。

## 介绍

我们制定Android-Java编码规范的原因是我们能够在团队协作中代码保持优雅和一致。即使我们有很多不同的人员来完成不同的项目。

<!-- more -->

## 参考

这里有些关于编码风格Java官方文档，如果有些东西没有提及，可以在以下文档来查找更多细节：

* [阿里巴巴开发手册 终极版1.3.0](https://files.cnblogs.com/files/han-1034683568/%E9%98%BF%E9%87%8C%E5%B7%B4%E5%B7%B4Java%E5%BC%80%E5%8F%91%E6%89%8B%E5%86%8C%E7%BB%88%E6%9E%81%E7%89%88v1.3.0.pdf)
* [ Google 开源项目风格指南](http://zh-google-styleguide.readthedocs.io/en/latest/google-cpp-styleguide/naming/)

## 目录

* [语言](#language)
* [命名约定](#name)
* [注释约定](#comments)
* [字符串连接方式](#string-connect)
* [局部变量的声明](#variables)
* [switch语句](#switch-statements)
* [注解](#annotation)
* [枚举类型](#enumerated-types)
* [异常处理](#error-handling)
* [静态成员](#static)
* [条件语句](#conditionals)

<b id="language"></b>
### 语言

应该使用US英语.

**应该:**

```
例
String myColor = "whiteColor";
```

**不应该:**
```
例
String myCoulor = "whiteColor";
```

<b id="name"></b>
### 命名约定
1. 包名全部小写，连续的单词只是简单地连接起来，不使用下划线。
```
例：
propertyservice
```
2. 类名都以UpperCamelCase风格编写。测试类的命名以它要测试的类的名称开始，以  Test结束。例如，HashTest。抽象类命名使用Abstract或Base开头。异常类命名使用Exception结尾。

3. 枚举类名带上Enum后缀，枚举成员名称需要全大写，单词间用下划线隔开。
```
例：
枚举名字为 ProcessStatusEnum 的成员名称：SUCCESS / UNKNOWN_REASON。
```
4. 方法名都以lowerCamelCase风格编写。

5. 常量名命名模式为CONS_CASE，全部字母大写，用下划线分隔单词。力求语义表达完整清楚，不要嫌名字长。

6. 非常量字段名以lowerCamelCase风格编写。

7. 参数名以lowerCamelCase风格编写。

8. 局部变量名以lowerCamelCase风格编写。

9. 类型变量名以类命名方式，后面加个大写的T.
```
例：
RequestT
```
10. Layout文件的命名方式

- Activity 的layout以module\_activity开头

- Fragment 的layout以module\_fragment开头

- Dialog 的 layout 以 module\_dialog 开头

- include 的layout以module\_include开头

- ListView 的 item以 module\_list\_item 开头

- RecyclerView 的 item 以 module\_recycle\_item 开头

- GridView 的 item以 module\_grid\_item

11. drawable资源名称以小写单词+下划线的方式命名。采用规则：模块名\_业务功能描述\_控件描述\_控件状态限定词。
```
例：
module\_login\_btn\_pressed,module\_tabs\_icon\_home\_normal
```

12. Anim资源名称以小写单词+下划线的方式命名，采用规则：模块名\_逻辑名称\_(方向)(序号)

- tween动画资源尽可能以通用的动画名称命名。
```
例：module\_fade\_in ,module\_fade\_out
```
- frame 动画资源：尽可能以模 块+功能命名+序号。
```
例：module\_loading\_grey\_0
```
13. color资源使用#AARRGGBB格式，命名规则：模块名\_逻辑名称\_颜色。
```
例：<color name="module_btn_bg_color">#33b5e5e5</color>
```
14. dimen 资源以小写单词+下划线方式命名。采用以下规则：模块名_大小。
```
例：<dimen name="dp16">16dp</dimen>
```
15. style 资源采用小写单词+下划线方式命名，写入 module_styles.xml 文件中，
采用以下规则：父 style 名称.当前 style 名称。
```
例：<style name="ParentTheme.ThisActivityTheme">
…
</style>
```
16. string资源文件或者文本用到字符需要全部写入module\_strings.xml文件中，字符串以小写单词+下划线的方式命名，采用以下规则：模块名\_逻辑名称
```
例：
moudule\_login\_tips,module\_homepage\_notice\_desc
```
17. Id 资源以小驼峰法命名，View 组件的资源 id 需要以 View 的缩写作为前缀。常用缩写表如下：

| 控件 | 缩写 |
| - | :-: |
| LinearLayout | ll|
| RelativeLayout | rl |  
| ConstraintLayout | cl |
| ListView | lv |
| ScrollView | sv |
| TextView | tv |
| Button | btn |
| ImageView | iv |
| CheckBox | cb |
| RadioButton | rb |
| EditText | et |
| RecycleView | rv |


其他控件的缩写推荐使用小写字母并用下划线进行分割，例如ProgressBar 对应的缩写为 progress_bar

<b id="comments"></b>
### 注释约定

1. 类、类属性、类方法、所有的抽象方法的注释使用Javadoc规范

```
例
/**
方法说明
@param 参数名 参数说明
@return 返回值说明
*/

```

类注释统一用以下模板：
```
/*/*
/* Descrip：
/* Author：  Created by ${USER} on ${DATE}.
/* Company： Copyright © 2018年 石家庄优思交通智能科技有限公司. All rights reserved.
*/
```
2. 单行注释

使用//注释方法内某个属性或者某个代码块
```
例
//按钮
int button;
//循环
for（int i=0; i<4; i++){
}
```
3. 多行注释

注释文字较多的时候适合使用/\*注释内容\*/多行注释
```
例
/*
这里是较多的注释文字
*/
for（int i=0; i<4; i++){
}
```
4. 所有枚举类型字段必须要有注释，说明每个数据项的用途。

5. 代码修改时，注释也要进行相应的修改，尤其是参数、返回值、异常、核心逻辑等的修改。

6. 及时删除不必要的注释和代码。

<b id="string-connect"></b>
### 字符串连接方式

循环体内，字符串的连接方式，使用StringBuilder的append方法进行扩展。
```
例
public String explicit(String[] fields){     
StringBuffer result = new StringBuffer();     
for(int i = 0; i < fields.length; i++){
result.append(fields[i]);
return result.toString();
}  
}
```

<b id="variables"></b>
### 局部变量的声明

不要在一个代码块的开头把局部变量一次性都声明了，而是在第一次需要使用它时才生命。局部变量在生命时最好就进行初始化，或者声明后尽快进行初始化。

<b id="switch-statements"></b>
### switch语句

每个switch语句都包含一个default语句，即使它什么代码也不包括。
```
例
switch(input){
case0:
prepareOneOrTwo
break;
default:
break;    
}
```
在一个switch块内，每个语句组要么通过break, continue, return或抛出异常来终止，要么通过⼀条注释来说明程序将继续执行到下一个语句组，任何能表达这个意思的注释都是OK的(典型的是用// fall through)。这个特殊的注释并不需要在最后一个语句组(一般是default)中出现。
```
例
switch(input){
case0:     
case1:
prepareOneOrTwo
// fall through
break;
default:
break;    
}
```

<b id="annotation"></b>
### 注解

注解紧跟在文档块后面，应用于类、方法和构造函数，一个注解独占一行。
```
例
@FormUrlEncoded
@POST("/v2/movie/top250")
Observable<BaseResponse> getTopMovie(@FieldMap Map<String, Object> map);
```
<b id="enumerated-types"></b>
### 枚举类型

值只可能在一个范围的时候用枚举定义。

<b id="error-handling"></b>
### 异常处理

捕获的异常不能忽视。典型的响应方式是打印日志，如果自身处理不了，则抛给上层。如果它确实是不需要在catch块中做任何响应，需要做注释加以说明。

<b id="static"></b>
### 静态成员

静态成员：使用类进行调用

使用类名调用静态的类成，而不是具体某个对象或表达式。
```
例
Foo aFoo = ...;
Foo.aStaticMethod()
```
<b id="conditionals"></b>
### 条件语句

条件语句主体为了防止出错应该使用大括号包围，即使条件语句主体能够不用大括号编写(如，只用一行代码)
```
例
if (!error) {
return success;
}
```
