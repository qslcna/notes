---
layout: post
title : 正则表达式
categories: 正则
---

## 资源

* [Online regex tester and debugger: PHP, PCRE, Python, Golang and JavaScript](https://regex101.com/)
* [正则表达式（RegEx）——快速参考](https://ahkcn.github.io/docs/misc/RegEx-QuickRef.htm)

## 分组

* 捕获型分组 `(pattern)`
* 非捕获型分组 `(?:pattern)`
  * 预查
    * 正向肯定预查 `(?=pattern)`
    * 正向否定预查 `(?!pattern)`
    * 反向肯定预查 `(?<=pattern)`
    * 反向否定预查 `(?<!pattern)`

### 不包含某字符串

* [regex - Regular expression to match a line that doesn't contain a word? - Stack Overflow](https://stackoverflow.com/q/406230/5954068)


### 在grep中使用预查

* [Regex lookahead for 'not followed by' in grep().](https://stackoverflow.com/q/9197814/5954068) 

### 参考

* [正则表达式 – 元字符  &#124; 菜鸟教程](http://www.runoob.com/regexp/regexp-metachar.html)
* [JavaScript 正则表达式的分组匹配 - KID.WuMeng - SegmentFault 思否](https://segmentfault.com/a/1190000004429477)

## 贪婪和非贪婪

`*` `+`限定符都是贪婪的，因为它们会尽可能多的匹配文字，只有在它们的后面加上一个?就可以实现非贪婪或最小匹配。

例如，您可能搜索 HTML 文档，以查找括在 H1 标记内的章节标题。该文本在您的文档中如下：

` <H1>Chapter 1 - 介绍正则表达式</H1>`

贪婪：下面的表达式匹配从开始小于符号 `<` 到关闭 H1 标记的大于符号 `>` 之间的所有内容。

```
/<.*>/
```
非贪婪：如果您只需要匹配开始和结束 H1 标签，下面的非贪婪表达式只匹配 `<H1>`。


```
/<.*?>/
```
如果只想匹配开始的 H1 标签，表达式则是：

```
/<\w+?>/
```
通过在 `*` `+` 或 `?` 限定符之后放置 `?`，该表达式从"贪心"表达式转换为"非贪心"表达式或者最小匹配。
