+++
title = "下载和本地安装软件包"
date = 2023-09-22T20:58:06+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/downloading-and-installing-packages-locally](https://docs.npmjs.com/downloading-and-installing-packages-locally)

# Downloading and installing packages locally - 下载和本地安装软件包

You can [install](https://docs.npmjs.com/cli-documentation/install) a package locally if you want to depend on the package from your own module, using something like Node.js `require`. This is `npm install`'s default behavior.

​	如果您想要从自己的模块中依赖软件包，可以[本地安装](https://docs.npmjs.com/cli-documentation/install)软件包，使用类似Node.js的 `require` 。这是 `npm install` 的默认行为。

## 安装无作用域的软件包 Installing an unscoped package

Unscoped packages are always public, which means they can be searched for, downloaded, and installed by anyone. To install a public package, on the command line, run

​	无作用域的软件包始终是公开的，这意味着任何人都可以搜索、下载和安装它们。要安装公共软件包，请在命令行上运行

```
npm install <package_name>
```

This will create the `node_modules` directory in your current directory (if one doesn't exist yet) and will download the package to that directory.

​	这将在当前目录中创建 `node_modules` 目录（如果尚不存在），并将软件包下载到该目录中。

**Note:** If there is no `package.json` file in the local directory, the latest version of the package is installed.

**注意：**如果本地目录中没有 `package.json` 文件，则会安装最新版本的软件包。

If there is a `package.json` file, npm installs the latest version that satisfies the [semver rule](about-semantic-versioning) declared in `package.json`.

​	如果存在 `package.json` 文件，npm将安装满足 `package.json` 中声明的[语义化版本规则](about-semantic-versioning)的最新版本。

## 安装有作用域的公共软件包 Installing a scoped public package

[Scoped public packages](about-scopes) can be downloaded and installed by anyone, as long as the scope name is referenced during installation:

​	[有作用域的公共软件包](about-scopes)可以被任何人下载和安装，只要在安装过程中引用了作用域名称：

```
npm install @scope/package-name
```

## 安装私有软件包 Installing a private package

[Private packages](about-private-packages) can only be downloaded and installed by those who have been granted read access to the package. Since private packages are always scoped, you must reference the scope name during installation:

​	[私有软件包](about-private-packages)只能被被授予对该软件包读取权限的人下载和安装。由于私有软件包始终有作用域，因此在安装过程中必须引用作用域名称：

```
npm install @scope/private-package-name
```

## 测试软件包安装 Testing package installation

To confirm that `npm install` worked correctly, in your module directory, check that a `node_modules` directory exists and that it contains a directory for the package(s) you installed:

​	要确认 `npm install` 是否正确工作，请在您的模块目录中检查是否存在 `node_modules` 目录，并且该目录中包含您安装的软件包的目录：

```
ls node_modules
```

## 已安装软件包的版本 Installed package version

If there is a `package.json` file in the directory in which `npm install` is run, npm installs the latest version of the package that satisfies the [semantic versioning rule](about-semantic-versioning) declared in `package.json`.

​	如果在运行 `npm install` 的目录中存在 `package.json` 文件，npm将安装满足 `package.json` 中声明的[语义化版本规则](about-semantic-versioning)的最新版本的软件包。

If there is no `package.json` file, the latest version of the package is installed.

​	如果不存在 `package.json` 文件，则会安装最新版本的软件包。

## 使用dist-tags安装软件包 Installing a package with dist-tags

Like `npm publish`, `npm install <package_name>` will use the `latest` tag by default.

​	与 `npm publish` 一样， `npm install <package_name>` 默认使用 `latest` 标签。

To override this behavior, use `npm install <package_name>@<tag>`. For example, to install the `example-package` at the version tagged with `beta`, you would run the following command:

​	要覆盖此行为，请使用 `npm install <package_name>@<tag>` 。例如，要安装使用 `beta` 标签标记的版本的 `example-package` ，您将运行以下命令：

```
npm install example-package@beta
```

## 资源 Resources

<iframe src="https://www.youtube.com/embed/JDSfqFFbNYQ" frameborder="0" allowfullscreen=""></iframe>
