+++
title = "尝试最新稳定版的 node"
date = 2023-09-22T20:53:49+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/try-the-latest-stable-version-of-node](https://docs.npmjs.com/try-the-latest-stable-version-of-node)

#  Try the latest stable version of node - 尝试最新稳定版的 node

If you're experiencing issues while using a version of node which is unsupported or unstable (odd numbered versions e.g. 0.7.x, 0.9.x, 0.11.x), it's very possible your issue will be fixed by simply using the [LTS](https://github.com/nodejs/LTS) version of node.

​	如果您在使用不受支持或不稳定的 node 版本（奇数版本，例如 0.7.x、0.9.x、0.11.x）时遇到问题，那么使用[LTS](https://github.com/nodejs/LTS)版本的 node 很可能会解决您的问题。

## 查看您正在运行的 Node.js 版本： See what version of node you're running:



```
node -v
```

### 在 Linux 上更新 Node.js Updating node on Linux

For some Linux distributions (Debian/Ubuntu and RedHat/CentOS), the latest node version provided by the distribution may lag behind the stable version. Here are [instructions from NodeSource](https://github.com/nodesource/distributions) on getting the latest node.

​	对于某些 Linux 发行版（Debian/Ubuntu 和 RedHat/CentOS），发行版提供的最新 Node.js 版本可能落后于稳定版本。以下是从 NodeSource 获取最新 Node.js 的[说明](https://github.com/nodesource/distributions)。

### 在 Windows 上更新 Node.js Updating node on Windows

Install the latest msi from https://nodejs.org/en/download

​	从 https://nodejs.org/en/download 安装最新的 msi 文件。

### 在 macOS 上更新 Node.js Updating node on OSX

Install the latest package from https://nodejs.org/en/download or if you are using [homebrew](http://brew.sh/)

​	从 https://nodejs.org/en/download 安装最新的软件包，或者如果您使用 [homebrew](http://brew.sh/)，可以使用以下命令：

```
brew install node
```

### 保持更新的简便方法 An easy way to stay up-to-date

Node.js has lots of versions, and its development is very active. As a good practice to manage the various versions, we recommend that you use a version manager for your Node.js installation. There are many great options, here are a few:

​	Node.js 有很多版本，它的开发非常活跃。为了管理各个版本，我们建议您使用版本管理器来安装 Node.js。有很多不错的选择，以下是其中几个：

- [NVM](https://github.com/creationix/nvm)
- [nodist](https://github.com/marcelklehr/nodist)
- [n](https://github.com/tj/n)
- [nave](https://github.com/isaacs/nave)
- [nodebrew](https://github.com/hokaccha/nodebrew)
