+++
title = "npm-shrinkwrap.json"
date = 2023-09-22T21:22:39+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false
+++

> 原文: [https://docs.npmjs.com/cli/v10/configuring-npm/npm-shrinkwrap-json](https://docs.npmjs.com/cli/v10/configuring-npm/npm-shrinkwrap-json)

# npm-shrinkwrap.json

A publishable lockfile

​	可发布的锁定文件

Select CLI Version:Version 10.0.0 (Latest Release)

### Description

`npm-shrinkwrap.json` is a file created by [`npm shrinkwrap`](https://docs.npmjs.com/cli/v10/commands/npm-shrinkwrap). It is identical to `package-lock.json`, with one major caveat: Unlike `package-lock.json`, `npm-shrinkwrap.json` may be included when publishing a package.

 	`npm-shrinkwrap.json`  是由 [ `npm shrinkwrap` ](https://docs.npmjs.com/cli/v10/commands/npm-shrinkwrap) 创建的文件。它与  `package-lock.json`  完全相同，但有一个重要的限制：与  `package-lock.json`  不同，可以在发布软件包时包含  `npm-shrinkwrap.json` 。

The recommended use-case for `npm-shrinkwrap.json` is applications deployed through the publishing process on the registry: for example, daemons and command-line tools intended as global installs or `devDependencies`. It's strongly discouraged for library authors to publish this file, since that would prevent end users from having control over transitive dependency updates.

​	推荐使用  `npm-shrinkwrap.json`  的用例是通过注册表上的发布过程部署的应用程序：例如，作为全局安装或  `devDependencies`  的守护进程和命令行工具。强烈不建议库作者发布此文件，因为这将阻止最终用户对传递依赖项的更新进行控制。

If both `package-lock.json` and `npm-shrinkwrap.json` are present in a package root, `npm-shrinkwrap.json` will be preferred over the `package-lock.json` file.

​	如果软件包根目录中同时存在  `package-lock.json`  和  `npm-shrinkwrap.json` ，则  `npm-shrinkwrap.json`  优先于  `package-lock.json`  文件。

For full details and description of the `npm-shrinkwrap.json` file format, refer to the manual page for [package-lock.json](https://docs.npmjs.com/cli/v10/configuring-npm/package-lock-json).

​	有关  `npm-shrinkwrap.json`  文件格式的详细信息和描述，请参阅 [package-lock.json](https://docs.npmjs.com/cli/v10/configuring-npm/package-lock-json) 的手册页面。

### See also

- [npm shrinkwrap](https://docs.npmjs.com/cli/v10/commands/npm-shrinkwrap)
- [package-lock.json](https://docs.npmjs.com/cli/v10/configuring-npm/package-lock-json)
- [package.json](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)
- [npm install](https://docs.npmjs.com/cli/v10/commands/npm-install)
