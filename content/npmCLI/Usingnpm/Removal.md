+++
title = "卸载"
date = 2023-09-22T21:25:01+08:00
weight = 100
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/cli/v10/using-npm/removal](https://docs.npmjs.com/cli/v10/using-npm/removal)

# removal - 卸载

Cleaning the Slate

​	清理干净

Select CLI Version:Version 10.0.0 (Latest Release)

### 概要 Synopsis

So sad to see you go.

​	很遗憾看到您要离开。

```bash
sudo npm uninstall npm -g
```

Or, if that fails, get the npm source code, and do:

​	或者，如果失败了，获取npm源代码，然后执行：

```bash
sudo make uninstall
```

### 更彻底的卸载 More Severe Uninstalling

Usually, the above instructions are sufficient. That will remove npm, but leave behind anything you've installed.

​	通常，上述说明已足够。这将删除npm，但会保留您安装的所有内容。

If that doesn't work, or if you require more drastic measures, continue reading.

​	如果这不起作用，或者您需要更严厉的措施，请继续阅读。

Note that this is only necessary for globally-installed packages. Local installs are completely contained within a project's `node_modules` folder. Delete that folder, and everything is gone unless a package's install script is particularly ill-behaved.

​	请注意，这仅适用于全局安装的软件包。本地安装完全包含在项目的 `node_modules` 文件夹中。删除该文件夹，除非软件包的安装脚本特别不良，否则一切都会消失。

This assumes that you installed node and npm in the default place. If you configured node with a different `--prefix`, or installed npm with a different prefix setting, then adjust the paths accordingly, replacing `/usr/local` with your install prefix.

​	这假设您在默认位置安装了node和npm。如果您使用不同的 `--prefix` 配置了node，或者使用不同的前缀设置安装了npm，则需要相应地调整路径，将 `/usr/local` 替换为您的安装前缀。

To remove everything npm-related manually:

​	要手动删除与npm相关的所有内容：

```bash
rm -rf /usr/local/{lib/node{,/.npm,_modules},bin,share/man}/npm*
```

If you installed things *with* npm, then your best bet is to uninstall them with npm first, and then install them again once you have a proper install. This can help find any symlinks that are lying around:

​	如果您使用npm安装了东西，那么您最好先使用npm卸载它们，然后在正确安装后再次安装它们。这可以帮助查找任何存在的符号链接：

```bash
ls -laF /usr/local/{lib/node{,/.npm},bin,share/man} | grep npm
```

Prior to version 0.3, npm used shim files for executables and node modules. To track those down, you can do the following:

​	在0.3版本之前，npm使用shim文件来执行可执行文件和节点模块。要找到它们，可以执行以下操作：

```bash
find /usr/local/{lib/node,bin} -exec grep -l npm \{\} \; ;
```

### See also

- [npm uninstall](https://docs.npmjs.com/cli/v10/commands/npm-uninstall)
- [npm prune](https://docs.npmjs.com/cli/v10/commands/npm-prune)
