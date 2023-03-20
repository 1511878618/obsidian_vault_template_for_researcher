---
title: 未命名
date: 2023-03-20 16:27:51
excerpt: 为啥要做？做完后有何收获感想体会？
tags: 
rating: ⭐
status: complete 
destination: 10-01-01
share: false
obsidianUIMode: source
---

由于template和shell commands初始环境变量的原因导致有的时候命令无法正常执行

## shell commands

- `echo $PATH`可以查看当前的环境变量
-
- 0.18附近的版本支持设置改插件使用的环境变量，直接添加即可
## template
目前没有发现修改环境变量的方式，似乎只能调用`/usr/bin:/bin:/usr/sbin:/sbin`

建议直接使用本地的python决对路径去调用


