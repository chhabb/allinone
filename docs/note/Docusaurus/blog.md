# blog

Docusaurus 的博客功能允许你快速搭建一个带有完整博客功能的文档网站，它内置了生成博客文章列表、标签、归档以及侧边栏等功能。接下来我将一步步解释它的使用方法、配置项，并详细说明如何设置博客页面的侧边栏。

### Docusaurus 博客功能概述

Docusaurus 的博客系统是内置的，不需要额外安装。你可以通过创建 Markdown 文件编写博客文章。每篇文章都会自动生成一个页面，并且可以通过标签、日期、作者等进行分类和筛选。

### 如何使用 Docusaurus 博客

1. **创建博客文件夹**：默认情况下，Docusaurus 的博客文件存放在 `blog` 目录中。如果你安装了 Docusaurus v2，`blog` 文件夹已经存在，你只需往里面添加文章。

2. **编写博客文章**：每篇博客文章是一个 Markdown 文件。可以在每篇文章的文件头（YAML front matter）中定义元数据，比如文章标题、发布日期、标签和作者。

   例如，创建一个 `blog/2023-09-23-my-first-blog-post.md` 文件：

   ```md
   ---
   title: 我的第一篇博客
   authors: [alice]
   tags: [Docusaurus, 博客]
   date: 2023-09-23
   ---

   这是我的第一篇博客文章，使用了 Docusaurus。
   ```

   每篇文章可以包含 Markdown 格式的正文，Docusaurus 会自动渲染这些文章为 HTML，并生成文章页面。

3. **运行博客**：通过命令启动 Docusaurus 开发服务器：

   ```bash
   npm start
   ```

   然后访问 `http://localhost:3000/blog` 就能看到你的博客页面。

### 博客配置选项

Docusaurus 博客的主要配置项在 `docusaurus.config.js` 中，通过 `blog` 这个键来配置：

```js
module.exports = {
  presets: [
    [
      '@docusaurus/preset-classic',
      {
        blog: {
          showReadingTime: true,
          routeBasePath: '/blog',  // 博客的 URL 基础路径
          blogTitle: '我的博客',    // 博客页面的标题
          blogDescription: '关于我的技术博客',  // 博客页面的描述
          postsPerPage: 10,       // 每页显示的博客文章数
          blogSidebarCount: 'ALL', // 博客侧边栏显示的文章数量，可以是 'ALL' 或数字
          blogSidebarTitle: '最近的文章',  // 博客侧边栏标题
        },
      },
    ],
  ],
};
```

- `showReadingTime`: 显示每篇文章的预估阅读时间。
- `routeBasePath`: 博客的 URL 路径，可以自定义为 `/articles` 等。
- `blogTitle`: 设置博客页面的主标题。
- `blogDescription`: 设置博客页面的描述。
- `postsPerPage`: 每页展示的文章数量，超过数量时会自动分页。
- `blogSidebarCount`: 控制博客侧边栏显示的文章数量。可以设置为 `'ALL'`（显示全部文章）或具体数字。
- `blogSidebarTitle`: 侧边栏的标题。

### 如何配置博客页面的侧边栏

博客页面的侧边栏可以显示最近的文章或特定文章的列表。你可以通过 `blogSidebarCount` 和 `blogSidebarTitle` 来控制侧边栏的显示内容。

例如：

```js
blogSidebarCount: 5,  // 显示最近5篇文章
blogSidebarTitle: '最近的文章',  // 侧边栏标题
```

- 如果你想让侧边栏显示特定数量的最近文章，设置 `blogSidebarCount` 为数字即可。
- 你还可以将 `blogSidebarCount` 设置为 `'ALL'`，让侧边栏显示所有博客文章。

#### 自定义侧边栏

如果你需要更复杂的侧边栏内容，Docusaurus 支持自定义组件。在 `src/theme/BlogSidebar.js` 中创建一个新的 React 组件，用以替代默认的侧边栏。

例如，自定义侧边栏可以包含作者分类、标签列表等：

```jsx
import React from 'react';
import { useBlogSidebar } from '@docusaurus/theme-common';

export default function CustomBlogSidebar() {
  const sidebar = useBlogSidebar();
  return (
    <div>
      <h3>自定义博客侧边栏</h3>
      <ul>
        {sidebar.items.map((item) => (
          <li key={item.permalink}>
            <a href={item.permalink}>{item.title}</a>
          </li>
        ))}
      </ul>
    </div>
  );
}
```

通过自定义组件，你可以完全掌控博客页面侧边栏的显示内容。

### 标签页面

Docusaurus 会自动生成每个标签的页面。每当你在某篇博客中使用了标签，Docusaurus 就会生成一个 `/tags` 页面，展示所有标签，以及点击标签时显示带有该标签的所有文章。

默认情况下，标签页面的路径是 `/tags`。你可以自定义标签页面的路径和样式，通过 `docusaurus.config.js` 中的 `tags` 配置项进行修改。

### 总结

Docusaurus 的博客系统非常灵活且易于配置。你可以通过 `blog` 选项自定义博客的结构和侧边栏，也可以通过 Markdown 文件轻松编写文章。侧边栏可以根据需求显示最新文章或通过自定义组件来丰富功能。

如果你需要更多的定制功能，比如复杂的侧边栏布局或额外的页面元素，Docusaurus 提供了强大的主题和插件系统，允许你自由扩展功能。