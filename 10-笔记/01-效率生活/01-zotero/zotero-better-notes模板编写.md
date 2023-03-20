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


## 笔记模板 

```javaScript
<!-- author:cople -->
<h1>${topItem.getField("title")}</h1>
<p> comment:: <p>
<h2 style="color: #1B5E20; background-color:#F1F8E9;">💡 Meta Data</h2> 
<table>    
 <tr>         
	<th style="background-color:#dbeedd;">              
	     <p style="text-align:i right">Title </p>          <!-- 标题 -->
	</th>         
	<td style="background-color:#dbeedd;">          
	  ${topItem.getField('title')}         
	</td>      
 </tr> 
 <tr>
        <th style="background-color:#f3faf4;">             
	   <p style="text-align: right">Journal </p>        <!-- 期刊  -->
       </th>         
       <td style="background-color:#f3faf4;">             
	  ${topItem.getField('publicationTitle')}   
       </td>    
 </tr>     
 <tr>
        <th style="background-color:#f3faf4;">
            <!-- 作者 -->
            <p style="text-align: right">Authors </p>
        </th>
        <td style="background-color:#f3faf4;">
            ${topItem.getCreators().map((v)=>"[[" + v.firstName+" "+v.lastName + "]]").join("; ")}
        </td>
 </tr>
 <tr>
        <th style="background-color:#dbeedd;">
            <!-- 出版日期 -->
            <p style="text-align: right">Pub. date </p>
        </th>
        <td style="background-color:#dbeedd;">
            ${topItem.getField('date')}
        </td>
 </tr>   
 <tr>
        <th style="background-color:#f3faf4;">
            <p style="text-align: right">DOI </p>
        </th>
        <td style="background-color:#f3faf4;">
            <a href= "https://doi.org/${topItem.getField('DOI')}">${topItem.getField('DOI')}</a>
        </td>
 </tr>
 <tr>
        <th style="background-color:#dbeedd;">
            <!-- 分区 -->
            <p style="text-align: right">JCR </p>
        </th>
        <td style="background-color:#dbeedd;">
            ${topItem.getField('callNumber')}
        </td>
 </tr>
 <tr>
        <th style="background-color:#dbeedd;">
             <!-- 影响因子 -->
            <p style="text-align: right">IF </p>
        </th>
        <td style="background-color:#dbeedd;">
            ${topItem.getField('libraryCatalog')}
        </td>
 </tr>
 </table>
</span></h1>\n <h2 style="color:  #E65100; background-color:  #FFF8E1;">📜 研究背景 & 目的 & 意义 & 基础</h2> <hr/>
<h3>  <span><span style="color:  #1565C0">背景：</span></span></h3>
<p></p>
<h3>  <span style="color: #1565C0">目的：</span></h3>
<p></p>
<h3>  <span style="color: #1565C0">意义：</span></h3>
<p></p>
<h3>  <span style="color: #1565C0">基础：</span></h3>
<p></p>
</span></h1>\n <h2 style="color:#2E7D32; background-color:    #F1F8E9;">&#x1F4CA 研究内容</h2> <hr/>
<p></p>
</span></h1>\n <h2 style="color:#4A148C; background-color:    #F5F5F5;">🚩 研究结论</h2> <hr/>
<p></p>
</span></h1>\n <h2 style="color: #006064; background-color:   #E0F7FA;">📌 创新 & 疑问</h2> <hr/>
<h3>  <span style="color: #1565C0">创新：</span></h3>
<p></p>
<h3>  <span style="color: #1565C0">疑问：</span></h3>
<p></p>
</span></h1>\n <h2 style="color:#1565C0; background-color:   #E1F5FE;">🔬 研究展望</h2> <hr/>
```

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

@${(noteItem.parentItem ? noteItem.parentItem.getField('citationKey'):  (noteItem.getNoteTitle ? noteItem.getNoteTitle().replace(/[/\\?%*:|"<> ]/g, "-") + "-" : ""))}.md
```

>`noteItem.parentItem`获取note的父条目，如果存在父条目则返回父条目，没有为null。
>`(condition ? code : else_code)`是条件语句，可以参见[java三元描述符](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)
>
>`noteItem.getNoteTitle()`获取笔记的title
>