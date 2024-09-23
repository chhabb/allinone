# docusaurus.config.js

## presets

在 Docusaurus 中，`presets` 是一种高层次的配置，它能帮助你快速集成常见的功能和插件，而不必手动逐一配置每个插件。`presets` 让站点的配置更加简单、模块化和可扩展。

### 什么是 `presets`

`presets` 是 Docusaurus 提供的一组预配置的插件和主题组合。每个 `preset` 都包含了一些默认的插件和主题，可以根据需要进一步定制。例如，Docusaurus 提供的默认 `classic` preset，集成了文档、博客、页面和主题等常见功能。

`presets` 的配置通常位于 `docusaurus.config.js` 文件中，用于定义项目的基础功能。以下是它们的结构和作用的详细解释。

### 典型 `presets` 示例

在 `docusaurus.config.js` 中，你可以这样配置 `presets`：

```js
module.exports = {
  presets: [
    [
      '@docusaurus/preset-classic',
      {
        docs: {
          sidebarPath: require.resolve('./sidebars.js'),
          editUrl: 'https://github.com/your-repo/edit/main/website/',
        },
        blog: {
          showReadingTime: true,
          editUrl: 'https://github.com/your-repo/edit/main/website/blog/',
        },
        theme: {
          customCss: require.resolve('./src/css/custom.css'),
        },
      },
    ],
  ],
};
```

这个例子使用了 `@docusaurus/preset-classic`，并自定义了 `docs`、`blog` 和 `theme` 相关的配置项。

### `presets` 的核心概念

#### 1. `@docusaurus/preset-classic`

这是 Docusaurus 官方提供的一个经典预设，适合大多数文档和博客驱动的网站。它包含以下插件：

- **文档插件 (`@docusaurus/plugin-content-docs`)**：用于管理和展示文档。
- **博客插件 (`@docusaurus/plugin-content-blog`)**：用于管理和展示博客文章。
- **页面插件 (`@docusaurus/plugin-content-pages`)**：用于创建自定义页面。
- **主题 (`@docusaurus/theme-classic`)**：用于控制站点的外观和样式。

这些功能是大多数 Docusaurus 网站的基础，使用 `@docusaurus/preset-classic` 能快速搭建一个包含文档、博客和自定义页面的站点。

#### 2. `docs` 配置

`docs` 是 `classic` preset 中的一个子配置项，用于控制文档插件的行为。常见的配置项包括：

- **`sidebarPath`**：定义侧边栏配置文件的路径，通常是 `sidebars.js`。它用来生成文档的导航结构。
- **`editUrl`**：用于设置“编辑此页”的链接，方便用户在 GitHub 上贡献文档内容。
- **`routeBasePath`**：自定义文档的 URL 路径。默认情况下，文档位于 `/docs`，可以通过此项更改。
- **`include`**：指定哪些文件类型应被包含在文档目录中，默认值为 `['**/*.{md,mdx}']`。
- **`showLastUpdateAuthor`**：是否显示最后一次更新的作者。
- **`showLastUpdateTime`**：是否显示文档的最后更新时间。

##### 示例：

```js
docs: {
  sidebarPath: require.resolve('./sidebars.js'),
  editUrl: 'https://github.com/your-repo/edit/main/website/',
  routeBasePath: '/my-docs',  // 文档的基础路径为 /my-docs
  showLastUpdateAuthor: true,
  showLastUpdateTime: true,
},
```

#### 3. `blog` 配置

`blog` 配置项控制博客插件的行为。常见的配置项包括：

- **`showReadingTime`**：是否显示阅读时间估计。
- **`editUrl`**：设置“编辑此页”的链接，方便用户对博客文章进行贡献。
- **`routeBasePath`**：自定义博客的 URL 路径，默认是 `/blog`。
- **`blogSidebarCount`**：定义博客侧边栏中显示的文章数目，可以是 `'ALL'` 显示所有文章，也可以设置为数字值。
- **`postsPerPage`**：设置每页显示的文章数量。

##### 示例：

```js
blog: {
  showReadingTime: true,
  editUrl: 'https://github.com/your-repo/edit/main/website/blog/',
  routeBasePath: '/news',  // 博客的基础路径为 /news
  postsPerPage: 10,
},
```

#### 4. `theme` 配置

`theme` 是 Docusaurus 中的主题相关配置，用于自定义站点的外观和样式。可以通过 `customCss` 来引用自定义 CSS 文件，覆盖默认样式。

##### 示例：

```js
theme: {
  customCss: require.resolve('./src/css/custom.css'),
},
```

这个配置告诉 Docusaurus 使用 `./src/css/custom.css` 文件中的样式来定制主题。

#### 5. `pages` 配置

虽然 `@docusaurus/preset-classic` 中没有 `pages` 的默认配置项，但它包含了自定义页面的功能，可以通过在 `src/pages` 目录下创建 `.js` 或 `.jsx` 文件来自定义页面。每个文件会自动映射为 URL 路径。

例如，`src/pages/about.js` 会生成 `/about` 页面。

### `presets` 的扩展性

`presets` 可以不仅仅使用官方提供的 `@docusaurus/preset-classic`。你还可以开发自己的 `presets` 或使用第三方 `presets`。每个 `preset` 事实上是一个插件集合，它包含了多个插件和主题的配置，因此你可以在一个 `preset` 内定义多个插件的默认行为。

例如，你可以创建一个自定义 `preset` 来包含你自己的文档、博客和定制化的插件配置。

##### 自定义 `preset` 示例：

你可以在 `docusaurus.config.js` 中使用多个 `presets`，例如：

```js
module.exports = {
  presets: [
    [
      '@docusaurus/preset-classic',
      { /* 配置 classic preset */ },
    ],
    [
      'custom-preset',
      { /* 配置自定义 preset */ },
    ],
  ],
};
```

### `presets` 和插件的关系

`presets` 本质上是插件的集合。因此，`preset` 中的配置项会直接影响其内部插件的行为。例如，`@docusaurus/preset-classic` 本质上是把文档、博客、页面和主题插件集合在一起。你可以在 `preset` 内部修改插件的配置，也可以直接在 `plugins` 数组中手动定义插件。

如果需要更加细粒度的控制，你可以不使用 `preset`，而是直接在 `docusaurus.config.js` 中配置 `plugins` 数组，并分别配置各个插件的选项。

### 总结

- **`presets`** 是 Docusaurus 的高层次配置，包含多个插件和主题。
- **`@docusaurus/preset-classic`** 是最常用的 `preset`，它包含文档、博客、页面和经典主题。
- **`docs`**、**`blog`** 和 **`theme`** 是 `classic` preset 中常见的子配置项，用于控制文档、博客和主题的行为。
- 你可以通过自定义 `presets` 或手动配置插件来进一步扩展站点的功能。

使用 `presets` 可以快速启动 Docusaurus 站点，同时保持高度的灵活性以适应不同的需求。

## themeConfig

在 Docusaurus 中，`themeConfig` 是配置站点外观、主题行为、布局和交互体验的核心部分。它位于 `docusaurus.config.js` 文件中，允许你自定义站点的导航栏、页脚、配色方案、代码块样式、国际化等各个方面。

### `themeConfig` 的作用

`themeConfig` 用于配置主题相关的所有设置，从导航栏、页脚的内容到代码块的配色方案，都可以通过它来定制。它包含了对站点主题的核心定制选项，是决定网站外观和用户交互体验的重要配置部分。

以下是 `themeConfig` 常见的配置项，以及如何自定义它们。

### `themeConfig` 常见配置项

#### 1. `navbar`

`navbar` 是 Docusaurus 站点顶部的导航栏，它允许你自定义站点的导航链接、徽标以及其他相关设置。典型配置如下：

```js
themeConfig: {
  navbar: {
    title: 'My Site',
    logo: {
      alt: 'My Site Logo',
      src: 'img/logo.svg',
    },
    items: [
      {
        type: 'doc',
        docId: 'intro', // 文档的默认 ID
        position: 'left',
        label: 'Docs',
      },
      {
        to: '/blog', // 博客的路径
        label: 'Blog',
        position: 'left',
      },
      {
        href: 'https://github.com/my-org/my-repo', // 外部链接
        label: 'GitHub',
        position: 'right',
      },
    ],
  },
},
```

- `title`：显示在导航栏左侧的站点标题。
- `logo`：站点的徽标，包含 `alt` 和 `src` 字段，表示图片的替代文本和路径。
- `items`：导航栏的项目，可以是文档、博客、外部链接、下拉菜单等。每个 `item` 都可以自定义 `label`（显示名称）、`position`（在左侧或右侧显示）和链接目标。

**支持的导航项类型：**

- **`type: 'doc'`**：指向某个文档。
- **`to`**：内部链接，指向某个页面或路径。
- **`href`**：外部链接，指向站外的 URL。
- **`type: 'dropdown'`**：定义下拉菜单。

#### 2. `footer`

`footer` 是站点底部的页脚部分，通常用来显示版权信息、链接、社交媒体图标等。配置示例：

```js
themeConfig: {
  footer: {
    style: 'dark', // 页脚的风格，可选值 'light' 或 'dark'
    links: [
      {
        title: 'Docs',
        items: [
          {
            label: 'Introduction',
            to: '/docs/intro',
          },
        ],
      },
      {
        title: 'Community',
        items: [
          {
            label: 'GitHub',
            href: 'https://github.com/my-org/my-repo',
          },
        ],
      },
    ],
    copyright: `Copyright © ${new Date().getFullYear()} My Project, Inc. Built with Docusaurus.`,
  },
},
```

- `style`：定义页脚的颜色风格，可以是 `'light'` 或 `'dark'`。
- `links`：页脚中的链接分组，每个分组都有 `title` 和 `items`，其中 `items` 包含具体的链接。
- `copyright`：页脚底部显示的版权信息，支持动态年份。

#### 3. `colorMode`

`colorMode` 配置支持站点的暗模式和亮模式切换。你可以设置默认模式和是否允许用户切换模式。

```js
themeConfig: {
  colorMode: {
    defaultMode: 'light',
    disableSwitch: false, // 是否允许切换主题
    respectPrefersColorScheme: true, // 自动根据用户系统的首选配色方案选择
  },
},
```

- `defaultMode`：设置站点的默认模式，可以是 `'light'` 或 `'dark'`。
- `disableSwitch`：是否允许用户在亮模式和暗模式之间切换。
- `respectPrefersColorScheme`：是否尊重用户设备的系统首选配色方案。

#### 4. `prism`

`prism` 配置用于自定义代码块的高亮显示，支持各种编程语言和配色方案。

```js
themeConfig: {
  prism: {
    theme: require('prism-react-renderer/themes/github'), // 亮色主题
    darkTheme: require('prism-react-renderer/themes/dracula'), // 暗色主题
    additionalLanguages: ['java', 'ruby'], // 支持额外的语言
  },
},
```

- `theme`：代码块在亮模式下的配色方案，通常使用 `prism-react-renderer` 提供的主题。
- `darkTheme`：暗模式下的代码块配色方案。
- `additionalLanguages`：支持额外的编程语言高亮。

#### 5. `sidebar`

`sidebar` 配置与文档相关，通常结合 `sidebars.js` 文件来定义文档的侧边栏结构。可以通过 `sidebarCollapsible` 和 `sidebarCollapsed` 配置侧边栏的默认行为。

```js
themeConfig: {
  sidebar: {
    hideable: true, // 是否允许用户隐藏侧边栏
    autoCollapseCategories: true, // 当展开某个分类时，自动折叠其他分类
  },
},
```

- `hideable`：允许用户通过按钮隐藏或显示侧边栏。
- `autoCollapseCategories`：控制当一个文档分类展开时，自动折叠其他分类。

#### 6. `algolia`

`algolia` 配置用于集成 Algolia 的站内搜索功能，提升搜索体验。你需要在 Algolia 注册，并获取 API 密钥。

```js
themeConfig: {
  algolia: {
    apiKey: 'your-api-key',
    indexName: 'your-index-name',
    appId: 'your-app-id',
    contextualSearch: true, // 是否启用上下文搜索
  },
},
```

- `apiKey`：Algolia 的搜索 API 密钥。
- `indexName`：Algolia 的索引名称，用于搜索特定站点内容。
- `appId`：Algolia 应用的 ID。
- `contextualSearch`：启用上下文搜索，以根据用户当前的文档页面进行相关搜索。

#### 7. `metadata`

`metadata` 用于设置站点的元信息，如 SEO 相关的 `meta` 标签等。

```js
themeConfig: {
  metadata: [
    { name: 'keywords', content: 'docusaurus, documentation, blog' },
    { name: 'description', content: 'My Docusaurus site' },
  ],
},
```

- `name` 和 `content`：指定元数据的名称和内容，常见的元数据包括 `keywords` 和 `description`，用于改善 SEO。

#### 8. `announcementBar`

`announcementBar` 配置一个公告栏，通常用于显示站点的公告、活动等。

```js
themeConfig: {
  announcementBar: {
    id: 'announcement',
    content: 'This is an important announcement!',
    backgroundColor: '#fafbfc',
    textColor: '#091E42',
    isCloseable: true, // 是否可以关闭
  },
},
```

- `id`：公告栏的唯一 ID，用于区分不同的公告。
- `content`：公告栏中显示的内容，可以是纯文本或 HTML。
- `backgroundColor`：公告栏的背景颜色。
- `textColor`：公告栏的文本颜色。
- `isCloseable`：是否允许用户关闭公告栏。

#### 9. `i18n`

`i18n` 配置用于站点的国际化，允许你支持多语言站点。

```js
themeConfig: {
  i18n: {
    defaultLocale: 'en',
    locales: ['en', 'fr', 'es'],
    localeConfigs: {
      en: {
        label: 'English',
        direction: 'ltr',
      },
      fr: {
        label: 'Français',
        direction: 'ltr',
      },
    },
  },
},
```

- `defaultLocale`：站点的默认语言。
- `locales`：支持的语言列表。
- `localeConfigs`：为每种语言提供特定配置，如标签和书写方向。

### 总结

- `themeConfig` 是 Docusaurus 中用于定制站点外观和用户体验的核心配置。
- 它包含了导航栏、页脚、配色方案、代码高亮、侧边栏、搜索、国际化等多个方面的设置。
- 通过修改 `themeConfig`，你可以高度定制站点的外观，使其符合你的品牌或需求。

使用 `themeConfig`，你能够快速调整站点的外观和交互方式，使 Docusaurus 更好地适应不同的使用场景。