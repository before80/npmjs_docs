+++
title = "下载和全局安装软件包"
date = 2023-09-22T20:58:16+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/downloading-and-installing-packages-globally](https://docs.npmjs.com/downloading-and-installing-packages-globally)

# Downloading and installing packages globally - 下载和全局安装软件包

**Tip:** If you are using npm 5.2 or higher, we recommend using `npx` to run packages globally.

**提示：**如果您使用的是npm 5.2或更高版本，我们建议使用 `npx` 来运行全局软件包。

[Installing](https://docs.npmjs.com/cli/install) a package globally allows you to use the code in the package as a set of tools on your local computer.

​	将软件包全局[安装](https://docs.npmjs.com/cli/install)可以让您在本地计算机上将软件包中的代码作为一组工具使用。

To download and install packages globally, on the command line, run the following command:

​	要下载和全局安装软件包，请在命令行上运行以下命令：

```
npm install -g <package_name>
```

If you get an EACCES permissions error, you may need to reinstall npm with a version manager or manually change npm's default directory. For more information, see "[Resolving EACCES permissions errors when installing packages globally](resolving-eacces-permissions-errors-when-installing-packages-globally)".

​	如果出现EACCES权限错误，您可能需要使用版本管理器重新安装npm或手动更改npm的默认目录。有关更多信息，请参阅“[解决全局安装软件包时的EACCES权限错误](解决全局安装软件包时的EACCES权限错误)”。
