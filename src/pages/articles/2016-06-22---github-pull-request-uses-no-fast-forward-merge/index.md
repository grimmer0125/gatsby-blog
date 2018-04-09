---
title: "GitHub Pull Request Uses No Fast Forward Merge"
date: "2016-06-22"
layout: post
tags:
  - Git
---
It means it always uses  
```git merge –no-ff```  
So if you want to use fast-forward way, the steps of the solution is

1. create a pull request first     
2. don't click "Merge pull request" button, please merge these two branch locally, and then push to remote.
3. The status on this pull request on github will become merged!!
