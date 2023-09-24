+++
title = "工作区"
date = 2023-09-22T21:24:20+08:00
weight = 60
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/cli/v10/using-npm/workspaces](https://docs.npmjs.com/cli/v10/using-npm/workspaces)

# workspaces - 工作区

Working with workspaces

​	使用工作区

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

**Workspaces** is a generic term that refers to the set of features in the npm cli that provides support to managing multiple packages from your local file system from within a singular top-level, root package.

​	**工作区**是一个通用术语，指的是npm cli中的一组功能，用于从单个顶级根软件包内部管理本地文件系统中的多个软件包。

This set of features makes up for a much more streamlined workflow handling linked packages from the local file system. Automating the linking process as part of `npm install` and avoiding manually having to use `npm link` in order to add references to packages that should be symlinked into the current `node_modules` folder.

​	这组功能可以更高效地处理来自本地文件系统的链接软件包的工作流程。它将链接过程自动化为 `npm install` 的一部分，避免手动使用 `npm link` 来添加应该链接到当前 `node_modules` 文件夹中的软件包的引用。

We also refer to these packages being auto-symlinked during `npm install` as a single **workspace**, meaning it's a nested package within the current local file system that is explicitly defined in the [`package.json`](https://docs.npmjs.com/cli/v10/configuring-npm/package-json#workspaces) `workspaces` configuration.

​	我们还将在 `npm install` 期间自动创建的这些软件包的符号链接称为单个**工作区**，这意味着它是当前本地文件系统中的一个嵌套软件包，明确定义在[ `package.json` ](https://docs.npmjs.com/cli/v10/configuring-npm/package-json#workspaces)的 `workspaces` 配置中。

### 定义工作区 Defining workspaces

Workspaces are usually defined via the `workspaces` property of the [`package.json`](https://docs.npmjs.com/cli/v10/configuring-npm/package-json#workspaces) file, e.g:

​	通常，工作区是通过[ `package.json` ](https://docs.npmjs.com/cli/v10/configuring-npm/package-json#workspaces)文件的 `workspaces` 属性来定义的，例如：

```json
{
  "name": "my-workspaces-powered-project",
  "workspaces": [
    "packages/a"
  ]
}
```

Given the above `package.json` example living at a current working directory `.` that contains a folder named `packages/a` that itself contains a `package.json` inside it, defining a Node.js package, e.g:

​	给定上述 `package.json` 示例，它位于当前工作目录 `.` 下，并包含一个名为 `packages/a` 的文件夹，该文件夹本身包含一个 `package.json` 文件，定义了一个Node.js软件包，例如：

```
.
+-- package.json
`-- packages
   +-- a
   |   `-- package.json
```

The expected result once running `npm install` in this current working directory `.` is that the folder `packages/a` will get symlinked to the `node_modules` folder of the current working dir.

​	在当前工作目录 `.` 中运行 `npm install` 后，预期的结果是文件夹 `packages/a` 将被链接到当前工作目录的 `node_modules` 文件夹中。

Below is a post `npm install` example, given that same previous example structure of files and folders:

​	下面是一个 `npm install` 后的示例，给定相同的文件和文件夹结构：

```
.
+-- node_modules
|  `-- a -> ../packages/a
+-- package-lock.json
+-- package.json
`-- packages
   +-- a
   |   `-- package.json
```

### 开始使用工作区 Getting started with workspaces

You may automate the required steps to define a new workspace using [npm init](https://docs.npmjs.com/cli/v10/commands/npm-init). For example in a project that already has a `package.json` defined you can run:

​	您可以使用[npm init](https://docs.npmjs.com/cli/v10/commands/npm-init)自动化定义新工作区所需的步骤。例如，在已定义 `package.json` 的项目中，您可以运行：

```
npm init -w ./packages/a
```

This command will create the missing folders and a new `package.json` file (if needed) while also making sure to properly configure the `"workspaces"` property of your root project `package.json`.

​	此命令将创建缺失的文件夹和一个新的 `package.json` 文件（如果需要的话），同时确保正确配置根项目 `package.json` 的 `"workspaces"` 属性。

### 向工作区添加依赖项 Adding dependencies to a workspace

It's possible to directly add/remove/update dependencies of your workspaces using the [`workspace` config](https://docs.npmjs.com/cli/v10/using-npm/config#workspace).

​	可以使用[ `workspace` 配置](https://docs.npmjs.com/cli/v10/using-npm/config#workspace)直接添加/删除/更新工作区的依赖项。

For example, assuming the following structure:

​	例如，假设有以下结构：

```
.
+-- package.json
`-- packages
   +-- a
   |   `-- package.json
   `-- b
       `-- package.json
```

If you want to add a dependency named `abbrev` from the registry as a dependency of your workspace **a**, you may use the workspace config to tell the npm installer that package should be added as a dependency of the provided workspace:

​	如果要将名为 `abbrev` 的依赖项从注册表添加为工作区**a**的依赖项，可以使用工作区配置告诉npm安装程序将该软件包添加为所提供工作区的依赖项：

```
npm install abbrev -w a
```

Note: other installing commands such as `uninstall`, `ci`, etc will also respect the provided `workspace` configuration.

​	注意：其他安装命令（如 `uninstall` 、 `ci` 等）也将遵循所提供的 `workspace` 配置。

### 使用工作区 Using workspaces

Given the [specifities of how Node.js handles module resolution](https://nodejs.org/dist/latest-v14.x/docs/api/modules.html#modules_all_together) it's possible to consume any defined workspace by its declared `package.json` `name`. Continuing from the example defined above, let's also create a Node.js script that will require the workspace `a` example module, e.g:

​	根据Node.js处理模块解析的[规范](https://nodejs.org/dist/latest-v14.x/docs/api/modules.html#modules_all_together)，可以通过其声明的 `package.json`   `name` 来使用任何定义的工作区。继续使用上面定义的示例，让我们创建一个Node.js脚本，该脚本将需要工作区 `a` 示例模块，例如：

```
// ./packages/a/index.js
module.exports = 'a'

// ./lib/index.js
const moduleA = require('a')
console.log(moduleA) // -> a
```

When running it with:

运行：

```
node lib/index.js
```

This demonstrates how the nature of `node_modules` resolution allows for **workspaces** to enable a portable workflow for requiring each **workspace** in such a way that is also easy to [publish](https://docs.npmjs.com/cli/v10/commands/npm-publish) these nested workspaces to be consumed elsewhere.

​	这演示了 `node_modules` 解析的性质，使得**工作区**能够以易于[发布](https://docs.npmjs.com/cli/v10/commands/npm-publish)这些嵌套工作区以在其他地方使用的方式启用可移植的工作流程。

### 在工作区上下文中运行命令 Running commands in the context of workspaces

You can use the `workspace` configuration option to run commands in the context of a configured workspace. Additionally, if your current directory is in a workspace, the `workspace` configuration is implicitly set, and `prefix` is set to the root workspace.

​	您可以使用 `workspace` 配置选项在配置的工作区上下文中运行命令。此外，如果当前目录位于工作区中，则 `workspace` 配置会被隐式设置，并且 `prefix` 设置为根工作区。

Following is a quick example on how to use the `npm run` command in the context of nested workspaces. For a project containing multiple workspaces, e.g:

​	以下是如何在嵌套工作区的上下文中使用 `npm run` 命令的快速示例。对于包含多个工作区的项目，例如：

```
.
+-- package.json
`-- packages
   +-- a
   |   `-- package.json
   `-- b
       `-- package.json
```

By running a command using the `workspace` option, it's possible to run the given command in the context of that specific workspace. e.g:

​	通过使用 `workspace` 选项运行命令，可以在特定工作区的上下文中运行给定的命令。例如：

```
npm run test --workspace=a
```

You could also run the command within the workspace.

​	您还可以在工作区内运行命令。

```
cd packages/a && npm run test
```

Either will run the `test` script defined within the `./packages/a/package.json` file.

​	任何一种方式都将运行 `./packages/a/package.json` 文件中定义的 `test` 脚本。

Please note that you can also specify this argument multiple times in the command-line in order to target multiple workspaces, e.g:

​	请注意，您还可以在命令行中多次指定此参数，以便针对多个工作区进行操作。例如：

```
npm run test --workspace=a --workspace=b
```

Or run the command for each workspace within the 'packages' folder:

​	或者在“packages”文件夹中的每个工作区中运行该命令：

```
npm run test --workspace=packages
```

It's also possible to use the `workspaces` (plural) configuration option to enable the same behavior but running that command in the context of **all** configured workspaces. e.g:

​	还可以使用 `workspaces` （复数）配置选项以启用相同的行为，但在**所有**配置的工作区上下文中运行该命令。例如：

```
npm run test --workspaces
```

Will run the `test` script in both `./packages/a` and `./packages/b`.

​	将在 `./packages/a` 和 `./packages/b` 中运行 `test` 脚本。

Commands will be run in each workspace in the order they appear in your `package.json`

​	命令将按照它们在 `package.json` 中出现的顺序在每个工作区中运行。

```
{
  "workspaces": [ "packages/a", "packages/b" ]
}
```

Order of run is different with:

​	与之不同的运行顺序是：

```
{
  "workspaces": [ "packages/b", "packages/a" ]
}
```

### 忽略缺失的脚本 Ignoring missing scripts

It is not required for all of the workspaces to implement scripts run with the `npm run` command.

​	并非所有的工作区都需要实现使用 `npm run` 命令运行的脚本。

By running the command with the `--if-present` flag, npm will ignore workspaces missing target script.

​	通过使用 `--if-present` 标志运行命令，npm将忽略缺少目标脚本的工作区。

```
npm run test --workspaces --if-present
```

### See also

- [npm install](https://docs.npmjs.com/cli/v10/commands/npm-install)
- [npm publish](https://docs.npmjs.com/cli/v10/commands/npm-publish)
- [npm run-script](https://docs.npmjs.com/cli/v10/commands/npm-run-script)
- [config](https://docs.npmjs.com/cli/v10/using-npm/config)
