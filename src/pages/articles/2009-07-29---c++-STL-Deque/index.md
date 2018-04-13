---
title: c++ STL中的Deque使用
date: '2009-07-29T14:08:00.001+08:00'
tags:
- c++
layout: post

---

基本上，deque是個雙向佇列，所以可自由的從最前面或最後面加入元素。當要清空deque時，若使用

```
deque.clear();
```

則bulid debug mode下的project會過不了，在release mode下會過但執行時有時會跳出例外。最後我找到的soultion則是使用

```
deque.erase(deque.begin(), deque.end());
```

這樣就OK了。
