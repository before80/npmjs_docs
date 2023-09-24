+++
title = "下载和安装 Node.js 和 npm"
date = 2023-09-22T20:53:19+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

# Downloading and installing Node.js and npm - 下载和安装 Node.js 和 npm

To publish and install packages to and from the public npm registry or a private npm registry, you must install Node.js and the npm command line interface using either a Node version manager or a Node installer. **We strongly recommend using a Node version manager like [nvm](https://github.com/nvm-sh/nvm) to install Node.js and npm.** We do not recommend using a Node installer, since the Node installation process installs npm in a directory with local permissions and can cause permissions errors when you run npm packages globally.

​	要将软件包发布到公共 npm 注册表或私有 npm 注册表，并从中安装软件包，您必须使用 Node.js 和 npm 命令行界面进行安装。您可以使用 Node 版本管理器或 Node 安装程序来完成此操作，**我们强烈建议使用像 [nvm](https://github.com/nvm-sh/nvm) 这样的 Node 版本管理器来安装 Node.js 和 npm**。我们不建议使用 Node 安装程序，因为 Node 安装过程会在具有本地权限的目录中安装 npm，并且在全局运行 npm 软件包时可能会导致权限错误。

**Note:** to download the latest version of npm, on the command line, run the following command:

**注意：**要下载最新版本的 npm，请在命令行中运行以下命令：

```
npm install -g npm
```

## 概述 Overview

- [Checking your version of npm and Node.js](#checking-your-version-of-npm-and-nodejs)
- [Using a Node version manager to install Node.js and npm](#using-a-node-version-manager-to-install-nodejs-and-npm)
- [Using a Node installer to install Node.js and npm](#using-a-node-installer-to-install-nodejs-and-npm)
- [检查 npm 和 Node.js 的版本](#检查-npm-和-nodejs-的版本)
- [使用 Node 版本管理器安装 Node.js 和 npm](#使用-node-版本管理器安装-nodejs-和-npm)
- [使用 Node 安装程序安装 Node.js 和 npm](#使用-node-安装程序安装-nodejs-和-npm)

## 检查 npm 和 Node.js 的版本 Checking your version of npm and Node.js

To see if you already have Node.js and npm installed and check the installed version, run the following commands:

​	要查看是否已安装 Node.js 和 npm 并检查已安装的版本，请运行以下命令：

```
node -v
npm -v
```

## 使用 Node 版本管理器安装 Node.js 和 npm Using a Node version manager to install Node.js and npm

Node version managers allow you to install and switch between multiple versions of Node.js and npm on your system so you can test your applications on multiple versions of npm to ensure they work for users on different versions.

​	Node 版本管理器允许您在系统上安装和切换多个 Node.js 和 npm 版本，以便您可以在多个 npm 版本上测试应用程序，以确保它们适用于不同版本的用户。

### OS X 或 Linux Node 版本管理器 OSX or Linux Node version managers

- [nvm](https://github.com/creationix/nvm)
- [n](https://github.com/tj/n)

### Windows Node 版本管理器 Windows Node version managers

- [nodist](https://github.com/marcelklehr/nodist)
- [nvm-windows](https://github.com/coreybutler/nvm-windows)

## 使用 Node 安装程序安装 Node.js 和 npm - Using a Node installer to install Node.js and npm

If you are unable to use a Node version manager, you can use a Node installer to install both Node.js and npm on your system.

​	如果无法使用 Node 版本管理器，您可以使用 Node 安装程序在系统上同时安装 Node.js 和 npm。

- [Node.js installer](https://nodejs.org/en/download/)
- [NodeSource installer](https://github.com/nodesource/distributions)

If you use Linux, we recommend that you use a NodeSource installer.

​	如果您使用的是 Linux，我们建议您使用 NodeSource 安装程序。

### OS X 或 Windows Node 安装程序 OS X or Windows Node installers

If you're using OS X or Windows, use one of the installers from the [Node.js download page](https://nodejs.org/en/download/). Be sure to install the version labeled **LTS**. Other versions have not yet been tested with npm.

​	如果您使用的是 OS X 或 Windows，请使用 [Node.js 下载页面](https://nodejs.org/en/download/) 上的安装程序之一。请确保安装标有 **LTS** 的版本。其他版本尚未与 npm 进行测试。

### Linux 或其他操作系统 Node 安装程序 Linux or other operating systems Node installers

If you're using Linux or another operating system, use one of the following installers:

​	如果您使用的是 Linux 或其他操作系统，请使用以下安装程序之一：

- [NodeSource installer](https://github.com/nodesource/distributions) (recommended)
- One of the installers on the [Node.js download page](https://nodejs.org/en/download/)

Or see [this page](https://nodejs.org/en/download/package-manager/) to install npm for Linux in the way many Linux developers prefer.

​	或参考 [此页面](https://nodejs.org/en/download/package-manager/) 以使用许多 Linux 开发人员偏爱的方式安装 Linux 的 npm。

### 不常见的操作系统 Less-common operating systems

For more information on installing Node.js on a variety of operating systems, see [this page](https://nodejs.org/en/download/package-manager/).

​	有关在各种操作系统上安装 Node.js 的更多信息，请参阅 [此页面](https://nodejs.org/en/download/package-manager/)。
