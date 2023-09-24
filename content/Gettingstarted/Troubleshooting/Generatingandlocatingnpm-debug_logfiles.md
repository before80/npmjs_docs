+++
title = "生成和定位 npm-debug.log 文件"
date = 2023-09-22T20:53:30+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/generating-and-locating-npm-debug.log-files](https://docs.npmjs.com/generating-and-locating-npm-debug.log-files)

# Generating and locating npm-debug.log files - 生成和定位 npm-debug.log 文件

When a package fails to install or publish, the npm CLI will generate an `npm-debug.log` file. This log file can help you figure out what went wrong.

​	当一个包安装或发布失败时，npm CLI 将生成一个  `npm-debug.log`  文件。这个日志文件可以帮助您找出问题出在哪里。

If you need to generate a `npm-debug.log` file, you can run one of these commands.

​	如果您需要生成一个  `npm-debug.log`  文件，您可以运行以下命令之一。

For installing packages:

​	对于安装包：

```
npm install --timing
```

For publishing packages:

​	对于发布包：

```
npm publish --timing
```

You can find the `npm-debug.log` file in your `.npm` directory. To find your `.npm` directory, use `npm config get cache`.

​	您可以在您的  `.npm`  目录中找到  `npm-debug.log`  文件。要找到您的  `.npm`  目录，请使用  `npm config get cache` 。

If you use a CI environment, your logs are likely located elsewhere. For example, in Travis CI, you can find them in the `/home/travis/build` directory.

​	如果您使用的是 CI 环境，您的日志可能位于其他位置。例如，在 Travis CI 中，您可以在  `/home/travis/build`  目录中找到它们。
