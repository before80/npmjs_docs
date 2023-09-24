+++
title = "npm init"
date = 2023-09-22T21:14:01+08:00
weight = 240
type = "docs"
description = ""
isCJKLanguage = true
draft = false
+++

> 原文: [https://docs.npmjs.com/cli/v10/commands/npm-init](https://docs.npmjs.com/cli/v10/commands/npm-init)

# npm-init

Create a package.json file

​	创建一个package.json文件

Select CLI Version:Version 10.0.0 (Latest Release)

### 概要 Synopsis



```bash
npm init <package-spec> (same as `npx <package-spec>`)
npm init <@scope> (same as `npx <@scope>/create`)

aliases: create, innit
```

### 描述 Description

`npm init <initializer>` can be used to set up a new or existing npm package.

 	`npm init <initializer>` 用于设置一个新的或现有的npm包。

`initializer` in this case is an npm package named `create-<initializer>`, which will be installed by [`npm-exec`](https://docs.npmjs.com/cli/v10/commands/npm-exec), and then have its main bin executed -- presumably creating or updating `package.json` and running any other initialization-related operations.

​	在这种情况下， `initializer` 是一个名为 `create-<initializer>` 的npm包，它将通过[ `npm-exec` ](https://docs.npmjs.com/cli/v10/commands/npm-exec)安装，然后执行其主要bin文件--可能创建或更新 `package.json` 并运行任何其他与初始化相关的操作。

The init command is transformed to a corresponding `npm exec` operation as follows:

​	init命令将转换为相应的 `npm exec` 操作，如下所示：

- `npm init foo` -> `npm exec create-foo`
- `npm init @usr/foo` -> `npm exec @usr/create-foo`
- `npm init @usr` -> `npm exec @usr/create`
- `npm init @usr@2.0.0` -> `npm exec @usr/create@2.0.0`
- `npm init @usr/foo@2.0.0` -> `npm exec @usr/create-foo@2.0.0`

If the initializer is omitted (by just calling `npm init`), init will fall back to legacy init behavior. It will ask you a bunch of questions, and then write a package.json for you. It will attempt to make reasonable guesses based on existing fields, dependencies, and options selected. It is strictly additive, so it will keep any fields and values that were already set. You can also use `-y`/`--yes` to skip the questionnaire altogether. If you pass `--scope`, it will create a scoped package.

​	如果省略了initializer（只调用 `npm init` ），init将回退到传统的init行为。它会询问一系列问题，然后为您编写一个package.json文件。它将尝试根据现有字段、依赖项和选择的选项进行合理的猜测。它是严格增量的，因此它将保留任何已经设置的字段和值。您还可以使用 `-y` / `--yes` 跳过问卷调查。如果传递 `--scope` ，它将创建一个作用域包。

*Note:* if a user already has the `create-<initializer>` package globally installed, that will be what `npm init` uses. If you want npm to use the latest version, or another specific version you must specify it:

*注意：*如果用户已经全局安装了 `create-<initializer>` 包，那将是 `npm init` 使用的包。如果您希望npm使用最新版本或其他特定版本，必须指定它：

- `npm init foo@latest` # fetches and runs the latest `create-foo` from the registry
- `npm init foo@latest` ＃从注册表中获取并运行最新的 `create-foo` 
- `npm init foo@1.2.3` # runs `create-foo@1.2.3` specifically
- `npm init foo@1.2.3` ＃专门运行 `create-foo@1.2.3` 

#### 转发其他选项 Forwarding additional options

Any additional options will be passed directly to the command, so `npm init foo -- --hello` will map to `npm exec -- create-foo --hello`.

​	任何其他选项都将直接传递给命令，因此 `npm init foo -- --hello` 将映射到 `npm exec -- create-foo --hello` 。

To better illustrate how options are forwarded, here's a more evolved example showing options passed to both the **npm cli** and a create package, both following commands are equivalent:

​	为了更好地说明选项是如何转发的，以下是一个更详细的示例，显示了传递给**npm cli**和create包的选项，以下两个命令是等效的：

- `npm init foo -y --registry=<url> -- --hello -a`
- `npm exec -y --registry=<url> -- create-foo --hello -a`

### 示例 Examples

Create a new React-based project using [`create-react-app`](https://npm.im/create-react-app):

​	使用[ `create-react-app` ](https://npm.im/create-react-app)创建一个新的基于React的项目：

```bash
$ npm init react-app ./my-react-app
```

Create a new `esm`-compatible package using [`create-esm`](https://npm.im/create-esm):

​	使用[ `create-esm` ](https://npm.im/create-esm)创建一个新的 `esm` 兼容包：

```bash
$ mkdir my-esm-lib && cd my-esm-lib
$ npm init esm --yes
```

Generate a plain old package.json using legacy init:

​	使用传统的init生成一个普通的package.json：

```bash
$ mkdir my-npm-pkg && cd my-npm-pkg
$ git init
$ npm init
```

Generate it without having it ask any questions:

​	在不询问任何问题的情况下生成它：

```bash
$ npm init -y
```

### Workspaces支持 Workspaces support

It's possible to create a new workspace within your project by using the `workspace` config option. When using `npm init -w <dir>` the cli will create the folders and boilerplate expected while also adding a reference to your project `package.json` `"workspaces": []` property in order to make sure that new generated **workspace** is properly set up as such.

​	可以通过使用 `workspace` 配置选项在项目中创建一个新的工作区。使用 `npm init -w <dir>` 时，cli将创建所需的文件夹和样板，并在项目的 `package.json` 中添加对工作区的引用，即 `"workspaces": []` 属性，以确保新生成的**工作区**正确设置。

Given a project with no workspaces, e.g:

​	给定一个没有工作区的项目，例如：

```
.
+-- package.json
```

You may generate a new workspace using the legacy init:

​	您可以使用传统的init生成一个新的工作区：

```bash
$ npm init -w packages/a
```

That will generate a new folder and `package.json` file, while also updating your top-level `package.json` to add the reference to this new workspace:

​	这将生成一个新的文件夹和 `package.json` 文件，并更新顶级 `package.json` 以添加对这个新工作区的引用：

```
.
+-- package.json
`-- packages
   `-- a
       `-- package.json
```

The workspaces init also supports the `npm init <initializer> -w <dir>` syntax, following the same set of rules explained earlier in the initial **Description** section of this page. Similar to the previous example of creating a new React-based project using [`create-react-app`](https://npm.im/create-react-app), the following syntax will make sure to create the new react app as a nested **workspace** within your project and configure your `package.json` to recognize it as such:

​	工作区init也支持 `npm init <initializer> -w <dir>` 语法，遵循本页面初始**描述**部分中解释的相同规则集。类似于使用[ `create-react-app` ](https://npm.im/create-react-app)创建一个新的基于React的项目的先前示例，以下语法将确保将新的react应用程序作为嵌套的**工作区**创建在您的项目中，并配置您的 `package.json` 以将其识别为工作区：

```bash
npm init -w packages/my-react-app react-app .
```

This will make sure to generate your react app as expected, one important consideration to have in mind is that `npm exec` is going to be run in the context of the newly created folder for that workspace, and that's the reason why in this example the initializer uses the initializer name followed with a dot to represent the current directory in that context, e.g: `react-app .`:

​	这将确保按预期生成您的react应用程序，需要记住的一个重要问题是， `npm exec` 将在工作区的新创建的文件夹的上下文中运行，并且这就是为什么在此示例中，初始化器使用初始化器名称，后跟点来表示该上下文中的当前目录，例如： `react-app .` ：

```
.
+-- package.json
`-- packages
   +-- a
   |   `-- package.json
   `-- my-react-app
       +-- README
       +-- package.json
       `-- ...
```

### 配置 Configuration

#### `yes`

- Default: null
- Type: null or Boolean

Automatically answer "yes" to any prompts that npm might print on the command line.

​	自动回答npm在命令行上可能打印的任何提示。

#### `force`

- Default: false
- Type: Boolean

Removes various protections against unfortunate side effects, common mistakes, unnecessary performance degradation, and malicious input.

​	删除各种保护措施，以防止不幸的副作用、常见错误、不必要的性能降低和恶意输入。

- Allow clobbering non-npm files in global installs.
- 允许覆盖全局安装中的非npm文件。
- Allow the `npm version` command to work on an unclean git repository.
- 允许 `npm version` 命令在非干净的git存储库上工作。
- Allow deleting the cache folder with `npm cache clean`.
- 允许使用 `npm cache clean` 删除缓存文件夹。
- Allow installing packages that have an `engines` declaration requiring a different version of npm.
- 允许安装具有 `engines` 声明要求不同版本的npm的软件包。
- Allow installing packages that have an `engines` declaration requiring a different version of `node`, even if `--engine-strict` is enabled.
- 允许安装具有 `engines` 声明要求不同版本的 `node` 的软件包，即使启用了 `--engine-strict` 。
- Allow `npm audit fix` to install modules outside your stated dependency range (including SemVer-major changes).
- 允许 `npm audit fix` 安装超出您声明的依赖范围的模块（包括SemVer-major更改）。
- Allow unpublishing all versions of a published package.
- 允许取消发布已发布软件包的所有版本。
- Allow conflicting peerDependencies to be installed in the root project.
- 允许在根项目中安装冲突的peerDependencies。
- Implicitly set `--yes` during `npm init`.
- 在 `npm init` 期间隐式设置 `--yes` 。
- Allow clobbering existing values in `npm pkg`
- 允许覆盖 `npm pkg` 中的现有值
- Allow unpublishing of entire packages (not just a single version).
- 允许取消发布整个软件包（而不仅仅是单个版本）。

If you don't have a clear idea of what you want to do, it is strongly recommended that you do not use this option!

​	如果您对自己想要做什么没有明确的想法，强烈建议您不要使用此选项！

#### `scope`

- Default: the scope of the current project, if any, or ""
- 默认值：当前项目的作用域（如果有）或""
- Type: String

Associate an operation with a scope for a scoped registry.

​	将操作与作用域关联，以便与作用域注册表关联。

Useful when logging in to or out of a private registry:

​	在登录或退出私有注册表时非常有用：

```
# log in, linking the scope to the custom registry
# 登录，将范围链接到自定义注册表
npm login --scope=@mycorp --registry=https://registry.mycorp.com

# log out, removing the link and the auth token
# 退出，删除链接和身份验证令牌
npm logout --scope=@mycorp
```

This will cause `@mycorp` to be mapped to the registry for future installation of packages specified according to the pattern `@mycorp/package`.

​	这将导致 `@mycorp` 被映射到将来根据模式 `@mycorp/package` 指定的软件包的注册表。

This will also cause `npm init` to create a scoped package.

​	这还将导致 `npm init` 创建一个作用域软件包。

```
# accept all defaults, and create a package named "@foo/whatever",
# 接受所有默认值，并创建一个名为"@foo/whatever"的软件包，
# instead of just named "whatever"
# 而不仅仅是命名为"whatever"
npm init --scope=@foo --yes
```

#### `workspace`

- Default:
- Type: String (can be set multiple times)
- 类型：字符串（可以设置多次）

Enable running a command in the context of the configured workspaces of the current project while filtering by running only the workspaces defined by this configuration option.

​	在过滤器的作用下，以当前项目的配置工作区的上下文中运行命令，只运行由此配置选项定义的工作区。

Valid values for the `workspace` config are either:

 	`workspace` 配置的有效值为：

- Workspace names
- 工作区名称
- Path to a workspace directory
- 工作区目录的路径
- Path to a parent workspace directory (will result in selecting all workspaces within that folder)
- 父工作区目录的路径（将选择该文件夹中的所有工作区）

When set for the `npm init` command, this may be set to the folder of a workspace which does not yet exist, to create the folder and set it up as a brand new workspace within the project.

​	当为 `npm init` 命令设置时，可以将其设置为尚不存在的工作区的文件夹，以在项目中创建文件夹并将其设置为全新的工作区。

This value is not exported to the environment for child processes.

​	此值不会导出到子进程的环境中。

#### `workspaces`

- Default: null
- Type: null or Boolean

Set to true to run the command in the context of **all** configured workspaces.

​	将其设置为true，以在**所有**配置的工作区的上下文中运行命令。

Explicitly setting this to false will cause commands like `install` to ignore workspaces altogether. When not set explicitly:

​	明确将其设置为false将导致像 `install` 这样的命令完全忽略工作区。当未显式设置时：

- Commands that operate on the `node_modules` tree (install, update, etc.) will link workspaces into the `node_modules` folder. - Commands that do other things (test, exec, publish, etc.) will operate on the root project, *unless* one or more workspaces are specified in the `workspace` config.
- 操作 `node_modules` 树的命令（install、update等）将链接工作区到 `node_modules` 文件夹中。- 其他操作（test、exec、publish等）将在根项目上操作，*除非*在 `workspace` 配置中指定了一个或多个工作区。

This value is not exported to the environment for child processes.

​	此值不会导出到子进程的环境中。

#### `workspaces-update`

- Default: true
- Type: Boolean

If set to true, the npm cli will run an update after operations that may possibly change the workspaces installed to the `node_modules` folder.

​	如果设置为true，npm cli将在可能更改已安装到 `node_modules` 文件夹的工作区的操作之后运行更新。

#### `include-workspace-root`

- Default: false
- Type: Boolean

Include the workspace root when workspaces are enabled for a command.

​	在启用工作区的情况下，包括工作区根目录。

When false, specifying individual workspaces via the `workspace` config, or all workspaces via the `workspaces` flag, will cause npm to operate only on the specified workspaces, and not on the root project.

​	当为false时，通过 `workspace` 配置指定单个工作区，或通过 `workspaces` 标志指定所有工作区，将导致npm仅对指定的工作区进行操作，而不是对根项目进行操作。

This value is not exported to the environment for child processes.

​	此值不会导出到子进程的环境中。

### See Also

- [package spec](https://docs.npmjs.com/cli/v10/using-npm/package-spec)
- [init-package-json module](http://npm.im/init-package-json)
- [package.json](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)
- [npm version](https://docs.npmjs.com/cli/v10/commands/npm-version)
- [npm scope](https://docs.npmjs.com/cli/v10/using-npm/scope)
- [npm exec](https://docs.npmjs.com/cli/v10/commands/npm-exec)
- [npm workspaces](https://docs.npmjs.com/cli/v10/using-npm/workspaces)
