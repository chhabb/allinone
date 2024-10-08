# `<!--truncate-->`

`<!--truncate-->` 是 Docusaurus 博客系统中用于截断文章内容的标记。它的作用是在博客列表页面或其他需要显示文章摘要的地方，只显示 `<!--truncate-->` 之前的内容，而 `<!--truncate-->` 之后的内容则只会在文章详情页面中显示。

### 使用场景

当你有一篇博客文章并希望在博客列表页面只展示文章的部分内容（例如一段引言或简介），而不展示整篇文章时，你可以使用 `<!--truncate-->`。它帮助读者在博客列表中快速预览文章，并通过点击标题来阅读完整内容。

### 详细说明

在 Docusaurus 中，博客文章通常以 Markdown 编写。你可以通过 `<!--truncate-->` 标记手动指定在哪里截断文章。

#### 示例：

```md
---
title: 使用 Docusaurus 搭建博客
date: 2023-09-23
tags: [Docusaurus, 博客]
---

这是我的第一篇博客文章的开头内容。希望大家喜欢这篇文章！

<!--truncate-->

这部分是文章的详细内容，只有当你点击博客标题后才会看到。
```

### 行为

1. **在博客列表页**：只有 `<!--truncate-->` 之前的内容会显示在列表页中，这样可以让页面加载更快，同时读者能快速预览多个博客内容。
2. **在博客详情页**：当读者点击进入文章详情页时，整个文章的内容，包括 `<!--truncate-->` 之后的部分，都会显示。

### 缺省行为

如果你不添加 `<!--truncate-->`，Docusaurus 会在博客列表页面显示文章的全部内容，而不是只显示部分摘要。

#### 示例 1：带 `<!--truncate-->` 的行为
- **博客列表页面**：显示“这是我的第一篇博客文章的开头内容。希望大家喜欢这篇文章！”
- **博客详情页面**：显示完整内容，包括“这部分是文章的详细内容...”

#### 示例 2：没有 `<!--truncate-->` 的行为
- **博客列表页面**：显示文章的所有内容，文章详情页也显示全部内容。

### 什么时候使用 `<!--truncate-->`

1. **博客列表摘要**：当你希望每篇博客在列表页仅展示引言或概要，而不是全文时，`<!--truncate-->` 是非常有用的。
2. **优化阅读体验**：通过展示精简的摘要，吸引读者点击阅读更多内容，同时避免长篇文章占据页面太多空间。
3. **提高加载性能**：如果博客文章比较长或有较多图片，在列表页上仅显示部分内容可以加快页面加载速度。

### 注意事项

- `<!--truncate-->` 是一个 HTML 注释标记，它不会在网页上显示出来，只是被 Docusaurus 用来决定内容的分割。
- 标记应该放在文章内容中合适的位置，比如在简介段落后，或者在第一段之后。

### 总结

`<!--truncate-->` 是 Docusaurus 用来帮助你管理博客内容展示的一个简单但有效的工具，它允许你灵活地控制文章在博客列表页面上的显示长度。通过在适当位置插入 `<!--truncate-->`，你可以提供简洁的摘要并吸引读者深入阅读完整文章。