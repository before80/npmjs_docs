+++
title = "关于公共软件包"
date = 2023-09-22T20:54:41+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/about-public-packages](https://docs.npmjs.com/about-public-packages)

# About public packages - 关于公共软件包

As an npm user or organization member, you can create and publish public packages that anyone can download and use in their own projects.

​	作为npm用户或组织成员，您可以创建和发布公共软件包，任何人都可以下载和在自己的项目中使用。

- **Unscoped** public packages exist in the global public registry namespace and can be referenced in a `package.json` file with the package name alone: `package-name`.

- **无作用域的**公共软件包存在于全局公共注册表命名空间中，可以在 `package.json` 文件中仅使用软件包名称引用： `package-name` 。

- Scoped public packages belong to a user or organization and must be preceded by the user or organization name when included as a dependency in a `package.json` file:

- **有作用域的**公共软件包属于用户或组织，当作为依赖项包含在 `package.json` 文件中时，必须在用户或组织名称之前加上前缀：
  - `@username/package-name`
  - `@org-name/package-name`

## 下一步 Next steps

- "[Creating and publishing scoped public packages](creating-and-publishing-scoped-public-packages)"
- 创建和发布有作用域的公共软件包
- "[Creating and publishing unscoped public packages](creating-and-publishing-unscoped-public-packages)"
- 创建和发布无作用域的公共软件包
- "[Using npm packages in your projects](using-npm-packages-in-your-projects)"
- 在您的项目中使用npm软件包
