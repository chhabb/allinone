# tags.yml

在 Docusaurus 中，`tags.yml` 文件主要用于管理博客标签的元数据。Docusaurus 的博客系统允许你为每篇博文添加标签，而这些标签可以通过 `tags.yml` 文件进行统一定义和管理。

### 作用

`tags.yml` 的主要作用是为每个标签提供更多的定制信息，如标签的显示名称和描述。它可以帮助你为标签创建更丰富的页面，从而改善用户浏览体验。

### 示例结构

一个典型的 `tags.yml` 文件可能如下所示：

```yaml
tags:
  - label: 开发
    permalink: /tags/开发
  - label: 教程
    permalink: /tags/教程
  - label: React
    permalink: /tags/react
```

### 字段解释

1. **`label`**: 这是标签的名称，表示在博客文章页面和标签页面中如何显示该标签。
  
2. **`permalink`**: 这是标签页面的链接。用户点击某个标签时，Docusaurus 会生成一个页面显示所有相关的文章，这个链接就是该页面的 URL。

### 工作机制

- 当你在某篇文章中使用了某个标签时，Docusaurus 会自动在该标签的页面中列出所有拥有这个标签的博文。
- `tags.yml` 文件的作用是让你可以手动为标签定义更友好的名称或链接，而不是依赖自动生成的名称。

### 应用场景

假设你有一个标签 `React`，你希望该标签的页面在 URL 中使用小写形式，如 `/tags/react`，而不是默认的 `/tags/React`，你可以通过在 `tags.yml` 中为 `React` 标签指定一个 `permalink` 来实现这一点。

此外，`tags.yml` 可以帮助你避免标签名称在不同文章中出现不一致的情况。