---
title: UserManager
date: 2019-01-24 15:44:26
tags:
categories: AppTeam
---
# UserManager

## 前言

涉及到用户登录的App，需要维护用户信息、并且处理用户登录状态。以下方案为平安社区各App中关于用户管理的技术实现方案。

<!-- more -->

## 类关系

### 与用户状态相关的类

0.**UserManager**(用户管理类）

```
负责持久化用户信息
负责与服务端(包含第三方)通讯
负责派发登录成功、失效的通知
```

1.**LoginViewController**(登陆页面)

```
负责触发登录操作
```
2.**LogoutViewController**(注销页面)

```
负责触发注销操作
```
3.**ViewManager**(页面管理类)

```
通过接收登录、注销通知维护页面，例如恢复视图初始层级、弹出登陆页面等
```
4.**BaseViewController**(页面基类）

```
通过接收登录、注销通知完成一些页面初始化操作，例如输入框清空等。
子类重写对应方法进行特殊化处理，例如暂停、重启定时器等
```
5.**PushMessageManager**(推送管理类)

```
通过接收登陆、注销通知维护第三方推送绑定、解绑操作
```
6.**BaseRequest**(网络请求基类)

```
调用接口后接收登录状态，触发UserManager的注销操作
```
6.**Other**(其他)

```
其他跟用户状态相关的类
```

### 通讯示意图
![Class-RelationShip](/images/usermanager.png)

### UserManager实现

```
-(User*)getCurrentUser;
-(void)loginWithUserNamexxx;
-(void)logout:(BOOL)isUser;//isUser：是否是用户主动注销
```
### 注意事项
	
1.登陆失效后，UserManager清空本地用户信息和发送注销通知的顺序:
	
```
建议先清空掉本地信息再发送全局注销通知，因为各类需要实时的获取到登陆状态进行处理。至于需要处理服务端用户状态的（例如注销推送服务），则在发送通知时附带一份用户拷贝信息。
```
2.登陆成功后，UserManager持久化用户信息和发送登陆成功通知顺序同上。

3.注销分为主动（用户点击注销）和被动（调用接口），在调用usermanager的logout和发送注销通知的时候需要加以区分。





