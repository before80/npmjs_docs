+++
title = "在 package.json 文件中指定依赖项和 devDependencies"
date = 2023-09-22T20:56:15+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/specifying-dependencies-and-devdependencies-in-a-package-json-file](https://docs.npmjs.com/specifying-dependencies-and-devdependencies-in-a-package-json-file)

# Specifying dependencies and devDependencies in a package.json file - 在 package.json 文件中指定依赖项和 devDependencies

To specify the packages your project depends on, you must list them as `"dependencies"` or `"devDependencies"` in your package's [`package.json`](creating-a-package-json-file) file. When you (or another user) run `npm install`, npm will download dependencies and devDependencies that are listed in `package.json` that meet the [semantic version](about-semantic-versioning) requirements listed for each. To see which versions of a package will be installed, use the [semver calculator](https://semver.npmjs.com/).

​	要指定项目依赖的包，您必须在包的 [ `package.json` ](creating-a-package-json-file) 文件中将它们列为  `"dependencies"`  或  `"devDependencies"` 。当您（或其他用户）运行  `npm install`  时，npm 将根据每个依赖项的[语义化版本](about-semantic-versioning)要求下载列在  `package.json`  中的依赖项和 devDependencies。要查看将安装的包的哪些版本，请使用[语义版本计算器](https://semver.npmjs.com/)。

- `"dependencies"`: Packages required by your application in production.
- `"dependencies"` ：应用程序在生产环境中需要的包。
- `"devDependencies"`: Packages that are only needed for local development and testing.
- `"devDependencies"` ：仅在本地开发和测试中需要的包。

## 在 package.json 文件中添加依赖项 Adding dependencies to a `package.json` file

You can add dependencies to a `package.json` file from the command line or by manually editing the `package.json` file.

​	您可以从命令行或通过手动编辑  `package.json`  文件向其中添加依赖项。

### 从命令行向 package.json 文件添加依赖项 Adding dependencies to a `package.json` file from the command line

To add dependencies and devDependencies to a `package.json` file from the command line, you can install them in the root directory of your package using the `--save-prod` flag for dependencies (the default behavior of `npm install`) or the `--save-dev` flag for devDependencies.

​	要从命令行向  `package.json`  文件添加依赖项和 devDependencies，您可以在包的根目录中使用  `--save-prod`  标志（ `npm install`  的默认行为）为依赖项安装它们，或者使用  `--save-dev`  标志为 devDependencies 安装它们。

To add an entry to the `"dependencies"` attribute of a `package.json` file, on the command line, run the following command:

​	要将条目添加到  `package.json`  文件的  `"dependencies"`  属性中，请在命令行中运行以下命令：

```
npm install <package-name> [--save-prod]
```

To add an entry to the `"devDependencies"` attribute of a `package.json` file, on the command line, run the following command:

​	要将条目添加到  `package.json`  文件的  `"devDependencies"`  属性中，请在命令行中运行以下命令：

```
npm install <package-name> --save-dev
```

### 手动编辑 package.json 文件 Manually editing the `package.json` file

To add dependencies to a `package.json` file, in a text editor, add an attribute called `"dependencies"` that references the name and [semantic version](about-semantic-versioning) of each dependency:

​	要向  `package.json`  文件添加依赖项，请在文本编辑器中添加一个名为  `"dependencies"`  的属性，该属性引用每个依赖项的名称和[语义化版本](about-semantic-versioning)：

```
{
  "name": "my_package",
  "version": "1.0.0",
  "dependencies": {
    "my_dep": "^1.0.0",
    "another_dep": "~2.2.0"
  }
}
```

To add devDependencies to a `package.json` file, in a text editor, add an attribute called `"devDependencies"` that references the name and [semantic version](about-semantic-versioning) of each devDependency:

​	要向  `package.json`  文件添加 devDependencies，请在文本编辑器中添加一个名为  `"devDependencies"`  的属性，该属性引用每个 devDependency 的名称和[语义化版本](about-semantic-versioning)：

```
"name": "my_package",
"version": "1.0.0",
"dependencies": {
  "my_dep": "^1.0.0",
  "another_dep": "~2.2.0"
},
"devDependencies" : {
  "my_test_framework": "^3.1.0",
  "another_dev_dep": "1.0.0 - 1.2.0"
}
```
