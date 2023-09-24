+++
title = "关于软件包和模块"
date = 2023-09-22T20:54:22+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/about-packages-and-modules](https://docs.npmjs.com/about-packages-and-modules)

# About packages and modules - 关于软件包和模块

The npm registry contains packages, many of which are also Node modules, or contain Node modules. Read on to understand how they differ and how they interact.

​	npm注册表包含许多软件包，其中许多软件包也是Node模块，或者包含Node模块。请继续阅读以了解它们的区别以及它们之间的交互方式。

## 关于软件包 About packages

A **package** is a file or directory that is described by a `package.json` file. A package must contain a `package.json` file in order to be published to the npm registry. For more information on creating a `package.json` file, see "[Creating a package.json file](creating-a-package-json-file)".

​	**软件包**是由 `package.json` 文件描述的文件或目录。软件包必须包含一个 `package.json` 文件才能发布到npm注册表。有关创建 `package.json` 文件的更多信息，请参阅“[创建 `package.json` 文件](creating-a-package-json-file)”。

Packages can be unscoped or scoped to a user or organization, and scoped packages can be private or public. For more information, see

​	软件包可以是无作用域的，也可以是作用域为用户或组织的，并且有作用域的软件包可以是私有的或公共的。有关更多信息，请参阅

- "[About scopes](../Aboutscopes)"
- 关于作用域
- "[About private packages](../Aboutprivatepackages)"
- 关于私有软件包
- "[Package scope, access level, and visibility](../npmpackagescopeaccesslevelandvisibility)"
- 软件包作用域、访问级别和可见性

### 关于软件包格式 About package formats

A package is any of the following:

​	软件包可以是以下任何一种：

- a) A folder containing a program described by a `package.json` file.
- a) 包含由 `package.json` 文件描述的程序的文件夹。
- b) A gzipped tarball containing (a).
- b) 包含（a）的gzip压缩的tarball。
- c) A URL that resolves to (b).
- c) 解析为（b）的URL。
- d) A `<name>@<version>` that is published on the registry with (c).
- d) 在注册表上以（c）发布的 `<name>@<version>` 。
- e) A `<name>@<tag>` that points to (d).
- e) 指向（d）的 `<name>@<tag>` 。
- f) A `<name>` that has a `latest` tag satisfying (e).
- f) 具有满足（e）的 `latest` 标签的 `<name>` 。
- g) A `git` url that, when cloned, results in (a).
- g) 当克隆时，结果是（a）的 `git`  URL。

### npm软件包的git URL格式 npm package git URL formats

Git URLs used for npm packages can be formatted in the following ways:

​	用于npm软件包的git URL可以采用以下格式：

- `git://github.com/user/project.git#commit-ish`
- `git+ssh://user@hostname:project.git#commit-ish`
- `git+http://user@hostname/project/blah.git#commit-ish`
- `git+https://user@hostname/project/blah.git#commit-ish`

The `commit-ish` can be any tag, sha, or branch that can be supplied as an argument to `git checkout`. The default `commit-ish` is `master`.

​	`commit-ish` 可以是作为 `git checkout` 参数提供的任何标签、sha或分支。默认的 `commit-ish` 是 `master` 。

## 关于模块 About modules

A **module** is any file or directory in the `node_modules` directory that can be loaded by the Node.js `require()` function.

​	**模块**是 `node_modules` 目录中可以被Node.js的 `require()` 函数加载的任何文件或目录。

To be loaded by the Node.js `require()` function, a module must be one of the following:

​	要被Node.js的 `require()` 函数加载，模块必须是以下之一：

- A folder with a `package.json` file containing a `"main"` field.
- 包含一个 `package.json` 文件并且该文件包含一个 `"main"` 字段的文件夹。
- A JavaScript file.
- 一个JavaScript文件。

**Note:** Since modules are not required to have a `package.json` file, not all modules are packages. Only modules that have a `package.json` file are also packages.

**注意：**由于模块不需要有 `package.json` 文件，因此并非所有模块都是软件包。只有具有 `package.json` 文件的模块才是软件包。

In the context of a Node program, the `module` is also the thing that was loaded *from* a file. For example, in the following program:

​	在Node程序的上下文中， `module` 也是从文件中加载的内容。例如，在以下程序中：

```
var req = require('request')
```

we might say that "The variable `req` refers to the `request` module".

​	我们可以说“变量 `req` 引用了 `request` 模块”。
