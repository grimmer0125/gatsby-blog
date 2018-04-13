---
title: Remaster Ubuntu by Tradtional Way
date: '2009-11-03T10:52:00.006+08:00'
tags:
- Ubuntu
layout: post
---

簡短的紀錄一下，大致上都是照以下這教學

[https://help.ubuntu.com/community/LiveCDCustomization"](https://help.ubuntu.com/community/LiveCDCustomization)

不過因為預設的apt-get相關設定有時會抓不到套件，所以在要進入`chroot`前

Copy resolv.conf and sources.list from the host system
```
# cp /etc/resolv.conf jaunty/remaster/etc/
```

Preserve original sources.list
```
# cp jaunty/remaster/etc/apt/soures.list jaunty/remaster/etc/apt/soures.list.backup
# cp /etc/apt/sources.list /jaunty/remaster/etc/apt/
```

exit後，replace the sources.list with the original sources.list
```
# cp jaunty/remaster/etc/apt/sources.list.backup jaunty/remaster/etc/apt/sources.list
```
