---
title: zotero-better-notes模板编写
date: 2023-03-14 13:21:12
excerpt: 为啥要做？做完后有何收获感想体会？
tags: 效率 
rating: ⭐
status: complete 
destination: 10-01-01
share: false
obsidianUIMode: source
---

zotero的API是可以通过JavaScript调用的，更多关于[[JavaScript语法介绍]]


## 导出模板设置

### 导出的header 
```javascript
${await new Promise(async (r) => {
  let header = {};
  header.alias = noteItem.parentItem? noteItem.parentItem.getField("title") : "";
  header.rating = "⭐";
  header.share = false;
  header.tags = [];
  header.zoteroTags = noteItem.parentItem? noteItem.parentItem.getTags().map((_t) => _t.tag):[];
  header.collections = (
    await Zotero.Collections.getCollectionsContainingItems([
      (noteItem.parentItem || noteItem).id,
    ])
  ).map((c) => c.name);
  r(JSON.stringify(header));
})}
```




### 导出的文件名，`[[citationKey]]` 的风格

`[[citationKey]]`的文件名可以保证，直接从zotero使用bibtex的快速Copy的时候**引用及是双向链接**。

![](https://tf-picture-bed-1259792641.cos.ap-beijing.myqcloud.com/20230314132455.png)

```js

${(noteItem.parentItem ? noteItem.parentItem.getField('citationKey'):  (noteItem.getNoteTitle ? noteItem.getNoteTitle().replace(/[/\\?%*:|"<> ]/g, "-")  : ""))}.md

```

>`noteItem.parentItem`获取note的父条目，如果存在父条目则返回父条目，没有为null。
>`(condition ? code : else_code)`是条件语句，可以参见[java三元描述符](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)
>
>`noteItem.getNoteTitle()`获取笔记的title
>