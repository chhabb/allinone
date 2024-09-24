# GitHub Pages
将静态网站部署到 GitHub Pages 的过程基于 GitHub 的功能，允许你将静态网页文件（如 HTML、CSS、JavaScript）托管到 GitHub 上并通过一个公开的 URL 访问。其基本原理是利用 GitHub 提供的托管能力，将你仓库中的静态资源直接映射为一个公开访问的网页服务。

### 原理
GitHub Pages 的工作原理是，GitHub 从你指定的分支（如 `main` 或 `gh-pages`）提取内容，使用 GitHub Pages 的服务器托管这些静态文件，并生成一个可以公开访问的 URL，如 `https://username.github.io/repositoryname/`。你也可以将整个网站绑定到自定义域名上。

GitHub Pages 支持两种类型的网站：
1. **用户或组织页面**：托管在 `https://username.github.io/`，代码存储在名为 `username.github.io` 的仓库中。
2. **项目页面**：托管在 `https://username.github.io/repositoryname/`，代码存储在任意 GitHub 仓库中。

### 部署步骤
1. **创建 GitHub 仓库**：首先，需要在 GitHub 上创建一个用于存储静态网站的仓库。你可以将其命名为项目名或 `username.github.io`（用于用户页面）。

2. **本地准备静态文件**：在本地计算机上准备好网站的 HTML、CSS、JS 及其他静态资源文件。如果使用生成器（如 Jekyll、Hugo 等），可以先生成静态网站文件。

3. **将文件推送到仓库**：
   - 将准备好的静态文件推送到 GitHub 仓库的指定分支（通常是 `main` 或 `gh-pages`）。如果你需要使用 `gh-pages` 分支，你可以使用以下步骤：
     ```bash
     git init
     git add .
     git commit -m "Initial commit"
     git branch -M gh-pages
     git remote add origin https://github.com/username/repositoryname.git
     git push -u origin gh-pages
     ```
   
4. **启用 GitHub Pages**：在仓库页面中，进入 "Settings" -> "Pages"，在 "Source" 一栏选择部署分支，如 `main` 或 `gh-pages`，然后保存。GitHub 会自动生成网站，并提供公开访问链接。

5. **访问网站**：完成部署后，你可以在 GitHub 提供的 URL 下查看你的网站，例如：
   - 项目页面：`https://username.github.io/repositoryname/`
   - 用户页面：`https://username.github.io/`

### 注意事项
1. **分支选择**：部署项目页面时，你可以选择将网站文件放在 `main` 分支的根目录、`docs/` 目录下，或者使用 `gh-pages` 分支。确保正确设置 GitHub Pages 的来源分支。

2. **CNAME 文件**：如果你希望使用自定义域名，需要在仓库中创建一个 `CNAME` 文件，里面包含你的自定义域名。同时，你需要在域名服务商处设置 DNS，将域名指向 GitHub Pages 的服务器。

3. **404 页面**：如果网站中有自定义 404 页面，需要在根目录放置一个名为 `404.html` 的文件。

4. **HTTPS 支持**：GitHub Pages 自动提供 HTTPS 加密支持，确保你的网站是通过安全连接访问的。

5. **项目页面路径**：如果你部署的是项目页面（不是用户页面），静态文件中的资源路径要以相对路径设置，以确保在 `https://username.github.io/repositoryname/` 这样的 URL 下正常加载。

### 操作细节
- 本地可以使用 GitHub 提供的 Git CLI 工具进行版本控制和推送操作。
- 对于大型项目，使用 `gh-pages` 分支来管理静态网站生成的文件，可以将代码文件与静态网站生成文件分开管理。
- 对于使用框架（如 React、Vue）的项目，通常在生成静态文件时需要指定 `homepage` 为 `https://username.github.io/repositoryname/` 以确保正确的路径设置。

通过这些步骤和注意点，你可以成功地将静态网站部署到 GitHub Pages 上，并通过网络公开访问。