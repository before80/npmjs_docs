+++
title = "更新从注册表下载的包"
date = 2023-09-22T20:58:35+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/updating-packages-downloaded-from-the-registry](https://docs.npmjs.com/updating-packages-downloaded-from-the-registry)

# Updating packages downloaded from the registry - 更新从注册表下载的包

Updating local and global packages you downloaded from the registry helps keep your code and tools stable, usable, and secure.

​	更新从注册表下载的本地和全局包有助于保持您的代码和工具的稳定性、可用性和安全性。

## 更新本地包 Updating local packages

We recommend regularly updating the local packages your project depends on to improve your code as improvements to its dependencies are made.

​	我们建议定期更新项目所依赖的本地包，以改进代码并使其依赖项的改进生效。

1. Navigate to the root directory of your project and ensure it contains a `package.json` file:

2. 导航到项目的根目录并确保其中包含一个  `package.json`  文件：

   ```
   cd /path/to/project
   ```

3. In your project root directory, run the [`update` command](https://docs.npmjs.com/cli/update):

4. 在项目的根目录中，运行 [ `update`  命令](https://docs.npmjs.com/cli/update)：

   ```
   npm update
   ```

5. To test the update, run the [`outdated` command](https://docs.npmjs.com/cli/outdated). There should not be any output.

6. 要测试更新，请运行 [ `outdated`  命令](https://docs.npmjs.com/cli/outdated)。不应该有任何输出。

   ```
   npm outdated
   ```

## 更新全局安装的包 Updating globally-installed packages

**Note:** If you are using npm version 2.6.0 or less, run [this script](https://gist.github.com/othiym23/4ac31155da23962afd0e) to update all outdated global packages.

**注意：**如果您使用的是 npm 2.6.0 或更低版本，请运行[此脚本](https://gist.github.com/othiym23/4ac31155da23962afd0e)以更新所有过时的全局包。

However, please consider upgrading to the latest version of npm:

​	但是，请考虑升级到最新版本的 npm：

```
npm install npm@latest -g
```

### 确定需要更新的全局包 Determining which global packages need updating

To see which global packages need to be updated, on the command line, run:

​	要查看需要更新的全局包，可以在命令行中运行：

```
npm outdated -g --depth=0
```

### 更新单个全局包 Updating a single global package

To update a single global package, on the command line, run:

​	要更新单个全局包，请在命令行中运行：

```
npm update -g <package_name>
```

### 更新所有全局安装的包 Updating all globally-installed packages

To update all global packages, on the command line, run:

​	要更新所有全局包，请在命令行中运行：

```
npm update -g
```

## 资源 Resources

<iframe src="https://www.youtube.com/embed/HRudtPGcOt4" frameborder="0" allowfullscreen=""></iframe>

### CLI 命令 CLI commands

- [npm-update](https://docs.npmjs.com/cli/update)
- [npm-outdated](https://docs.npmjs.com/cli/outdated)
