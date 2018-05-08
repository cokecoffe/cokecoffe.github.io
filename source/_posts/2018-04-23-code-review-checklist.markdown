---
layout: "post"
title: "Code Review CheckList"
date: "2018-04-23 16:09"
categories: AppTeam
---

# Code Review CheckList

本规范作为Code Review的依据

<!-- more -->

### 架构/设计/常规

1. 文件
```
文件存放是否根据对应文件夹归类
```

2. 头文件引用
```
是否有重复、无用的引用
```

3. 单一职责
```
一个类、一个方法只能做一件事，适当做抽离，提高复用性
```

4. 注释
```
是否有必要的注释，注释格式是否规范
```

5. 命名
```
类、方法 命名是否符合规范
```

6. 代码格式
```
代码是否进行过格式化，有否多余空格等
```

7. 无用代码
```
是否提交了测试代码、无用的注释
```

### 编码风格

[《Objective-C code style》](https://cokecoffe.github.io/2018/04/20/2018-04-20-Objective-C%20Style/)

[《Android-Java Code Style》](https://cokecoffe.github.io/2018/04/21/2018-4-21-android-java-code-style/)
