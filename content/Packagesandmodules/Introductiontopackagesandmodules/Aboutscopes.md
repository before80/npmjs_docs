+++
title = "关于作用域"
date = 2023-09-22T20:54:32+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/about-scopes](https://docs.npmjs.com/about-scopes)

# About scopes - 关于作用域

Note: You must be using npm version 2 or greater to use scopes. To upgrade to the latest version of npm, on the command line, run

注意：您必须使用 npm 版本 2 或更高版本才能使用作用域。要升级到最新版本的 npm，请在命令行中运行：

```highlighter-rouge
npm install npm@latest -g
```

When you sign up for an npm user account or create an organization, you are granted a scope that matches your user or organization name. You can use this scope as a namespace for related packages.

​	当您注册 npm 用户账户或创建一个组织时，您将获得与您的用户或组织名称相匹配的作用域。您可以使用这个作用域作为相关包的命名空间。

A scope allows you to create a package with the same name as a package created by another user or organization without conflict.

​	作用域允许您创建与其他用户或组织创建的包具有相同名称的包，而不会发生冲突。

When listed as a dependent in a `package.json` file, scoped packages are preceded by their scope name. The scope name is everything between the `@` and the slash:

​	当在  `package.json`  文件中列出依赖项时，作用域包的名称前面会加上它们的作用域名称。作用域名称是在  `@`  和斜杠之间的所有内容：

- **"npm" scope:**
- **"npm" 作用域：**

```
@npm/package-name
```

- **"npmcorp" scope:**
- **"npmcorp" 作用域：**

```
@npmcorp/package-name
```

To create and publish public scoped packages, see "[Creating and publishing scoped public packages](creating-and-publishing-scoped-public-packages)".

​	要创建和发布公共作用域包，请参见 "[创建和发布公共作用域包](creating-and-publishing-scoped-public-packages)"。

To create and publish private scoped packages, see "[Creating and publishing private packages](creating-and-publishing-private-packages)".

​	要创建和发布私有作用域包，请参见 "[创建和发布私有包](creating-and-publishing-private-packages)"。

## 作用域和包的可见性 Scopes and package visibility

- Unscoped packages are always public.
- 无作用域的包始终是公共的。
- [Private packages](about-private-packages) are always scoped.
- [私有包](about-private-packages)始终是有作用域的。
- Scoped packages are private by default; you must pass a command-line flag when publishing to make them public.
- 作用域包默认是私有的；您必须在发布时传递一个命令行标志来使它们变为公共的。

For more information on package scope and visibility, see "[Package scope, access level, and visibility](package-scope-access-level-and-visibility)".

​	有关包作用域和可见性的更多信息，请参见 "[包作用域、访问级别和可见性](package-scope-access-level-and-visibility)"。
