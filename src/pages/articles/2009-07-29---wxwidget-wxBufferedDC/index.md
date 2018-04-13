---
title: wxwidget中的wxBufferedDC使用方法
date: '2009-07-29T15:49:00.003+08:00'
layout: post
tags:
- wxWidgets

---

wxBufferedDC的目的是為了減少閃碩等畫面更新可能帶來的問題，它有幾個預設的constructer，若是要在wxBufferedDC中自己維持一個bitmap以增進速度，則方法是先new出一個bitmap object

```
wxDC* dc2 = new wxClientDC(this);
wxBufferedDC dc(dc2, *buffer);
```

然後在繪圖的function中，把此bitmap的pointer丟進wxBufferedDC的constructer，後再進行繪圖動作

```
{
  wxDC* dc2 = new wxClientDC(this);
  wxBufferedDC dc(dc2, *buffer);
  .
  .
  .
  dc.UnMask();
  delete dc2;
}
```

此function執行到最後面時會去執行wxBufferedDC的deconstructor，就會自動把bitmap的東西倒進wxClientDC中 (畫到螢幕上)，但之前new出來的dc2並不會自動delte掉，這樣程式執行時會有memory leak造成的不穩定情形，所以要在function最後面加dc.UnMask()來手動把bitmap倒進wxClientDC中，再delete掉dc2。
