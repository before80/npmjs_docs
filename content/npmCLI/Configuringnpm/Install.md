+++
title = "安装"
date = 2023-09-22T21:21:55+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/cli/v10/configuring-npm/install](https://docs.npmjs.com/cli/v10/configuring-npm/install)

# install - 安装

Download and install node and npm

​	下载并安装Node.js和npm

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

To publish and install packages to and from the public npm registry, you must install Node.js and the npm command line interface using either a Node version manager or a Node installer. **We strongly recommend using a Node version manager to install Node.js and npm.** We do not recommend using a Node installer, since the Node installation process installs npm in a directory with local permissions and can cause permissions errors when you run npm packages globally.

​	要发布和安装来自公共npm注册表的软件包，您必须使用Node版本管理器或Node安装程序安装Node.js和npm命令行界面。**我们强烈建议使用Node版本管理器来安装Node.js和npm。**我们不建议使用Node安装程序，因为Node安装过程会在具有本地权限的目录中安装npm，并且在全局运行npm软件包时可能会导致权限错误。

### 检查npm和Node.js的版本 Checking your version of npm and Node.js

To see if you already have Node.js and npm installed and check the installed version, run the following commands:

​	要查看是否已安装Node.js和npm并检查已安装的版本，请运行以下命令：

```
node -v
npm -v
```

### 使用Node版本管理器安装Node.js和npm Using a Node version manager to install Node.js and npm

Node version managers allow you to install and switch between multiple versions of Node.js and npm on your system so you can test your applications on multiple versions of npm to ensure they work for users on different versions. You can [search for them on GitHub](https://github.com/search?q=node+version+manager+archived%3Afalse&type=repositories&ref=advsearch).

​	Node版本管理器允许您在系统上安装和切换多个Node.js和npm版本，以便您可以在多个npm版本上测试应用程序，以确保它们适用于使用不同版本的用户。您可以[在GitHub上搜索它们](https://github.com/search?q=node+version+manager+archived%3Afalse&type=repositories&ref=advsearch)。

### 使用Node安装程序安装Node.js和npm Using a Node installer to install Node.js and npm

If you are unable to use a Node version manager, you can use a Node installer to install both Node.js and npm on your system.

​	如果您无法使用Node版本管理器，您可以使用Node安装程序在系统上安装Node.js和npm。

- [Node.js installer](https://nodejs.org/en/download/)
- [NodeSource installer](https://github.com/nodesource/distributions). If you use Linux, we recommend that you use a NodeSource installer.
- [NodeSource安装程序](https://github.com/nodesource/distributions)。如果您使用Linux，我们建议您使用NodeSource安装程序。

#### OS X或Windows Node安装程序 OS X or Windows Node installers

If you're using OS X or Windows, use one of the installers from the [Node.js download page](https://nodejs.org/en/download/). Be sure to install the version labeled **LTS**. Other versions have not yet been tested with npm.

​	如果您使用的是OS X或Windows，请使用[Node.js下载页面](https://nodejs.org/en/download/)上的其中一个安装程序。请确保安装标记为**LTS**的版本。其他版本尚未与npm进行测试。

#### Linux或其他操作系统的Node安装程序 Linux or other operating systems Node installers

If you're using Linux or another operating system, use one of the following installers:

​	如果您使用的是Linux或其他操作系统，请使用以下安装程序之一：

- [NodeSource installer](https://github.com/nodesource/distributions) (recommended)
- One of the installers on the [Node.js download page](https://nodejs.org/en/download/)
- [Node.js下载页面](https://nodejs.org/en/download/)上的其中一个安装程序

Or see [this page](https://nodejs.org/en/download/package-manager/) to install npm for Linux in the way many Linux developers prefer.

​	或者参考[此页面](https://nodejs.org/en/download/package-manager/)以按照许多Linux开发人员喜欢的方式为Linux安装npm。

#### 不常见的操作系统 Less-common operating systems

For more information on installing Node.js on a variety of operating systems, see [this page](https://nodejs.org/en/download/package-manager/).

​	有关在各种操作系统上安装Node.js的更多信息，请参阅[此页面](https://nodejs.org/en/download/package-manager/)。
