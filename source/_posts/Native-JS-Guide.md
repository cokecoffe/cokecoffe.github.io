---
layout: "post"
title: Native_JS_Guide
date: 2018-12-24 14:48:00
categories: AppTeam
---

# 平安社区通用H5业务接入指南

使用的data参数规则如下

```
action  不可为空  方法名  调用原生函数  与  原生函数命名统一
needCallBack  不可为空  默认为0    是否需要原生回调
message  不可为空,  使用场景为显示页面错误等供原生使用
parameter  可为空  附加参数,用于复杂业务时,向原生传递参数 json结构
```

例如

```
{ 
"action":"jsNGetToken",
"needCallBack":"1",
"message":"获取Token",
"parameter":{
"state":1
}
}
```

返回结果

| 参数名称 | 必选 | 类型 | 参数描述 |
| ------ | ------ |  ------ |  ------ | 
| code | true |  int | 返回结果状态（0成功-1失败） |
| msg | true |  string | 返回结果信息 |
| data | true |  json | 返回结果体 |

例如

```
{ 
"code":0,
"msg":"成功",
"data":{ 
"img":"youlife"
}
}
```

## JS调取Native(原生)
原生端handerName为nativeListener并提供action如下

---

### jsNGetPhoto（获取图片）

**调取此方法原生端显示选择图片的弹窗**

*js端调取原生的选择图片时使用*

后期需要添加参数再协商

data结构如下

```
{ 
"action":"jsNGetPhoto",
"needCallBack":"1",
"message":"获取照片",
"parameter":{ }
}
```

返回结果

| 参数名称 | 必选 | 类型 | 参数描述 |
| ------ | ------ |  ------ |  ------ | 
| code | true |  int | 返回结果状态 |
| msg | true |  string | 返回结果信息 |
| data | true |  json | 返回结果体 |
| img | true |  string | 返回图片的base64 |

例如

```
{ 
"code":0,
"msg":"成功",
"data":{ 
"img":"youlife"
}
}
```



---

### jsNGetToken（获取token）

**调取此方法原生端会返回当前用户token**

![token-flow](/images/token-flow.png)

*js端需要原生端的授权（token）时调用*

| 参数名称 | 必选 | 参数描述 |
| ------ | ------ |  ------ | 
| business | true |  需要授权的业务 |

data结构如下

```
{ 
"action":"jsNGetToken",
"needCallBack":"1",
"message":"获取token",
"parameter":{ 
"business":"xxx业务"
}
}
```

返回结果

| 参数名称 | 必选 | 类型 | 参数描述 |
| ------ | ------ |  ------ |  ------ | 
| code | true |  int | 返回结果状态 |
| msg | true |  string | 返回结果信息 |
| data | true |  json | 返回结果体 |
| token | true |  string | 返回token |

例如

```
{ 
"code":0,
"msg":"成功",
"data":{ 
"token":"klsdjflksdjkfldsklkfj"
}
}
```



---

### jsNInvalidLogin（登录失效）
**调取此方法原生端会调取登录界面**

*js端调取后台接口token失效时调用*

data结构如下

```
{ 
"action":"jsNInvalidLogin",
"needCallBack":"1",
"message":"登录失效",
"parameter":{ }
}
```


---

### jsNShareWeb（调用分享）
**调取此方法原生端会显示分享弹窗**

*js端需要分享时调用*

| 参数名称 | 必选 | 参数描述 |
| ------ | ------ |  ------ | 
| shareUrl  |  true |  需要分享的链接 |
| shareTitle  |  true |  需要分享的标题 |
| shareContext  |  true |  需要分享的内容 |
| imgUrl  |  false |  需要分享的图片 |

data结构如下

```
{ 
"action":"jsNShareWeb",
"needCallBack":"1",
"message":"调用分享",
"parameter":{
"shareUrl":"http://www.baidu.com",
"shareContext":"shareContext",
"shareTitle":"shareTitle",
"imgUrl":"",
}
}
```

---

### jsNShowLoading（显示加载框）
**调取此方法原生端会显示加载框（调此方法必须调用jsNDismissLoading）**

*js端需要显示加载框时调用*
### jsNDismissLoading（隐藏加载框）
**调取此方法原生端会隐藏加载弹框**

*js端需要隐藏加载弹框时调用*
### jsNShowLoadFailed（加载失败）
**调取此方法原生端会显示加载失败（调此方法必须调用jsNShowContent）**

*js端需要显示加载失败时调用*
### jsNShowNoNetwork（显示无网络）
**调取此方法原生端会显示无网络（调此方法必须调用jsNShowContent）**

*js端需要显示加载失败时调用*
###jsNShowContent（显示内容页）
**调取此方法原生端会显示正常页面**

*js端调取加载失败jsNShowLoadFailed或者无网络jsNShowNoNetwork后调用*
