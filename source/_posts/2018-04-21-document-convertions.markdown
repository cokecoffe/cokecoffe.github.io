---
layout: "post"
title: "Document Convertions"
date: "2018-04-21 14:14"
categories: AppTeam
---

## 注释形式

1. [单行注释](#singleline)
2. [多行注释](#multiline)
3. [方法注释](#function)
4. [方法集注释](#block)
5. [类注释](#class)

<!-- more -->

<b id="singleline"></b>
### 单行注释

使用`//`注释方法内某个属性或者某个代码块
```
int button;//按钮

//循环
for（int i=0; i<4; i++){

}
```
<b id="multiline"></b>
### 多行注释

注释文字较多的时候适合使用`/*注释内容*/`多行注释
```
/*
这里是较多的注释文字
*/
for（int i=0; i<4; i++){

}
```
<b id="function"></b>
### 方法注释

用于对方法进行说明，使用`/**注释内容**/`
```
/**
 方法说明
 @param 参数名 参数说明
 @return 返回值说明
 */
```
**使用方法**:
Xcode快捷键:`cmd+alt+/`
Studio快捷键:函数上方输入 `/**` 然后回车

<b id="block"></b>
### 方法集注释（iOS）

用于对方法进行分类
```
#param mark - <#注释内容>
```
<b id="class"></b>
### 类注释

在.h 文件 @interface 上面添加当前类的 提示注释
1. 方便查看当前类的作用（如图）；
2. 在各个类中使用当前类的时候都可以通过 option+点击 来查看提示注释（如图）；
3. 方便以后做更多的提示注释（如图）；
```
/// 商品订单优惠cell
@interface SGProductOrderDiscountCell : UITableViewCell
```
