---
title: 'Let Objective-C use C++ code'
date: "2011-11-08"
layout: post
tags:
- Objective-C
- C++
category: "Objective-C"
description: ""
draft: false
---

Rules:

1. `.m` 文件可以混合`C`和`Objective-C`程式碼
2. `.mm`  文件可以混合`C`, `C++` & `Objective-C` 程式碼
3. `.c` & `.cpp`  不能混合有 `Objective-C` 程式碼

所以方法有三種:

1. 使用`.mm`
2. 從`Objective-C`使用`C`，再透過`C`來使用`C++`就能達到目的。
3. 把編譯器的Compile Sources As選項改为`Objective C++`。預設是According to file type
