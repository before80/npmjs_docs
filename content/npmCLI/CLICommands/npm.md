+++
title = "npm"
date = 2023-09-22T21:09:49+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false
+++

> 原文: [https://docs.npmjs.com/cli/v10/commands/npm](https://docs.npmjs.com/cli/v10/commands/npm)

# npm

javascript package manager

​	JavaScript 包管理器

Select CLI Version:Version 10.0.0 (Latest Release)

​	选择 CLI 版本：版本 10.0.0（最新发布）

### 概述 Synopsis

```bash
npm
```

Note: This command is unaware of workspaces.

注意：此命令不支持工作区。

### 版本 Version

10.0.0

### 描述 Description

npm is the package manager for the Node JavaScript platform. It puts modules in place so that node can find them, and manages dependency conflicts intelligently.

​	npm 是 Node JavaScript 平台的包管理器。它将模块放置在适当的位置，以便 Node 可以找到它们，并智能地管理依赖冲突。

It is extremely configurable to support a variety of use cases. Most commonly, you use it to publish, discover, install, and develop node programs.

​	它可以根据不同的用例进行极高的配置。通常，您可以使用它来发布、发现、安装和开发 Node 程序。

Run `npm help` to get a list of available commands.

​	运行  `npm help`  可以获取可用命令的列表。

### 重要信息 Important

npm comes preconfigured to use npm's public registry at https://registry.npmjs.org by default. Use of the npm public registry is subject to terms of use available at https://docs.npmjs.com/policies/terms.

​	npm 默认配置为使用 npm 的公共注册表 https://registry.npmjs.org。使用 npm 公共注册表需遵守使用条款，详情请参阅 https://docs.npmjs.com/policies/terms。

You can configure npm to use any compatible registry you like, and even run your own registry. Use of someone else's registry is governed by their terms of use.

​	您可以配置 npm 使用任何兼容的注册表，甚至运行自己的注册表。使用他人的注册表受其使用条款的管理。

### 简介 Introduction

You probably got npm because you want to install stuff.

​	您可能使用 npm 是因为您想要安装一些东西。

The very first thing you will most likely want to run in any node program is `npm install` to install its dependencies.

​	在任何 Node 程序中，您最有可能要运行的第一件事是  `npm install` ，以安装其依赖项。

You can also run `npm install blerg` to install the latest version of "blerg". Check out [`npm install`](https://docs.npmjs.com/cli/v10/commands/npm-install) for more info. It can do a lot of stuff.

​	您还可以运行  `npm install blerg`  来安装最新版本的 "blerg"。查看 [ `npm install` ](https://docs.npmjs.com/cli/v10/commands/npm-install) 获取更多信息。它可以做很多事情。

Use the `npm search` command to show everything that's available in the public registry. Use `npm ls` to show everything you've installed.

​	使用  `npm search`  命令显示公共注册表中的所有可用内容。使用  `npm ls`  显示您已安装的所有内容。

### 依赖项 Dependencies

If a package lists a dependency using a git URL, npm will install that dependency using the [`git`](https://github.com/git-guides/install-git) command and will generate an error if it is not installed.

​	如果一个软件包使用 Git URL 列出依赖项，npm 将使用 [ `git` ](https://github.com/git-guides/install-git) 命令安装该依赖项，并在未安装时生成错误。

If one of the packages npm tries to install is a native node module and requires compiling of C++ Code, npm will use [node-gyp](https://github.com/nodejs/node-gyp) for that task. For a Unix system, [node-gyp](https://github.com/nodejs/node-gyp) needs Python, make and a buildchain like GCC. On Windows, Python and Microsoft Visual Studio C++ are needed. For more information visit [the node-gyp repository](https://github.com/nodejs/node-gyp) and the [node-gyp Wiki](https://github.com/nodejs/node-gyp/wiki).

​	如果 npm 尝试安装的软件包之一是原生的 Node 模块，并且需要编译 C++ 代码，npm 将使用 [node-gyp](https://github.com/nodejs/node-gyp) 完成该任务。对于 Unix 系统，[node-gyp](https://github.com/nodejs/node-gyp) 需要 Python、make 和类似 GCC 的构建链。在 Windows 上，需要 Python 和 Microsoft Visual Studio C++。有关更多信息，请访问 [node-gyp 仓库](https://github.com/nodejs/node-gyp) 和 [node-gyp Wiki](https://github.com/nodejs/node-gyp/wiki)。

### 目录 Directories

See [`folders`](https://docs.npmjs.com/cli/v10/configuring-npm/folders) to learn about where npm puts stuff.

​	请参阅 [ `folders` ](https://docs.npmjs.com/cli/v10/configuring-npm/folders) 了解 npm 将文件放置的位置。

In particular, npm has two modes of operation:

​	特别是，npm 有两种操作模式：

- local mode: npm installs packages into the current project directory, which defaults to the current working directory. Packages install to `./node_modules`, and bins to `./node_modules/.bin`.
- 本地模式：npm 将软件包安装到当前项目目录中，默认为当前工作目录。软件包安装到  `./node_modules` ，二进制文件安装到  `./node_modules/.bin` 。
- global mode: npm installs packages into the install prefix at `$npm_config_prefix/lib/node_modules` and bins to `$npm_config_prefix/bin`.
- 全局模式：npm 将软件包安装到安装前缀  `$npm_config_prefix/lib/node_modules` ，二进制文件安装到  `$npm_config_prefix/bin` 。

Local mode is the default. Use `-g` or `--global` on any command to run in global mode instead.

​	本地模式是默认模式。在任何命令上使用  `-g`  或  `--global`  以在全局模式下运行。

### 开发者用法 Developer Usage

If you're using npm to develop and publish your code, check out the following help topics:

​	如果您使用 npm 开发和发布代码，请查看以下帮助主题：

- json: Make a package.json file. See [`package.json`](https://docs.npmjs.com/cli/v10/configuring-npm/package-json).
- json：创建一个 package.json 文件。请参阅 [ `package.json` ](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)。
- link: Links your current working code into Node's path, so that you don't have to reinstall every time you make a change. Use [`npm link`](https://docs.npmjs.com/cli/v10/commands/npm-link) to do this.
- link：将当前工作代码链接到 Node 的路径，这样您就不必每次更改时重新安装。使用 [ `npm link` ](https://docs.npmjs.com/cli/v10/commands/npm-link) 完成此操作。
- install: It's a good idea to install things if you don't need the symbolic link. Especially, installing other peoples code from the registry is done via [`npm install`](https://docs.npmjs.com/cli/v10/commands/npm-install)
- install：如果您不需要符号链接，安装软件包是一个好主意。特别是，通过注册表安装他人的代码使用 [ `npm install` ](https://docs.npmjs.com/cli/v10/commands/npm-install)。
- adduser: Create an account or log in. When you do this, npm will store credentials in the user config file.
- adduser：创建一个账户或登录。当您这样做时，npm 将在用户配置文件中存储凭据。
- publish: Use the [`npm publish`](https://docs.npmjs.com/cli/v10/commands/npm-publish) command to upload your code to the registry.
- publish：使用 [ `npm publish` ](https://docs.npmjs.com/cli/v10/commands/npm-publish) 命令将代码上传到注册表。

#### 配置 Configuration

npm is extremely configurable. It reads its configuration options from 5 places.

​	npm 可以进行极高的配置。它从 5 个位置读取配置选项。

- Command line switches: Set a config with `--key val`. All keys take a value, even if they are booleans (the config parser doesn't know what the options are at the time of parsing). If you do not provide a value (`--key`) then the option is set to boolean `true`.
- 命令行开关：使用  `--key val`  设置配置。所有键都需要一个值，即使它们是布尔值（配置解析器在解析时不知道选项是什么）。如果您没有提供值（ `--key` ），则该选项将设置为布尔值  `true` 。
- Environment Variables: Set any config by prefixing the name in an environment variable with `npm_config_`. For example, `export npm_config_key=val`.
- 环境变量：通过在环境变量中使用  `npm_config_`  前缀来设置任何配置。例如， `export npm_config_key=val` 。
- User Configs: The file at `$HOME/.npmrc` is an ini-formatted list of configs. If present, it is parsed. If the `userconfig` option is set in the cli or env, that file will be used instead.
- 用户配置：位于  `$HOME/.npmrc`  的文件是配置的 ini 格式列表。如果存在，它将被解析。如果 cli 或 env 中设置了  `userconfig`  选项，则将使用该文件。
- Global Configs: The file found at `./etc/npmrc` (relative to the global prefix will be parsed if it is found. See [`npm prefix`](https://docs.npmjs.com/cli/v10/commands/npm-prefix) for more info on the global prefix. If the `globalconfig` option is set in the cli, env, or user config, then that file is parsed instead.
- 全局配置：如果找到位于  `./etc/npmrc`  的文件（相对于全局前缀），则将解析它。有关全局前缀的更多信息，请参阅 [ `npm prefix` ](https://docs.npmjs.com/cli/v10/commands/npm-prefix)。如果 cli、env 或用户配置中设置了  `globalconfig`  选项，则将解析该文件。
- Defaults: npm's default configuration options are defined in `lib/utils/config/definitions.js`. These must not be changed.
- 默认配置：npm 的默认配置选项定义在  `lib/utils/config/definitions.js`  中。这些选项不得更改。

See [`config`](https://docs.npmjs.com/cli/v10/using-npm/config) for much much more information.

​	请参阅 [ `config` ](https://docs.npmjs.com/cli/v10/using-npm/config) 了解更多信息。

### 贡献 Contributions

Patches welcome!

​	欢迎提交补丁！

If you would like to help, but don't know what to work on, read the [contributing guidelines](https://github.com/npm/cli/blob/latest/CONTRIBUTING.md) and check the issues list.

​	如果您想提供帮助，但不知道从哪里开始，请阅读[贡献指南](https://github.com/npm/cli/blob/latest/CONTRIBUTING.md)并查看问题列表。

### Bugs

When you find issues, please report them: https://github.com/npm/cli/issues

​	当您发现问题时，请报告它们：https://github.com/npm/cli/issues

Please be sure to follow the template and bug reporting guidelines.

​	请确保遵循模板和错误报告准则。

### 功能请求 Feature Requests

Discuss new feature ideas on our discussion forum:

​	在我们的讨论论坛上讨论新的功能想法：

- https://github.com/npm/feedback

Or suggest formal RFC proposals:

​	或提出正式的 RFC 提案：

- https://github.com/npm/rfcs

### 参见 See Also

- [npm help](https://docs.npmjs.com/cli/v10/commands/npm-help)
- [package.json](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)
- [npmrc](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc)
- [npm config](https://docs.npmjs.com/cli/v10/commands/npm-config)
- [npm install](https://docs.npmjs.com/cli/v10/commands/npm-install)
- [npm prefix](https://docs.npmjs.com/cli/v10/commands/npm-prefix)
- [npm publish](https://docs.npmjs.com/cli/v10/commands/npm-publish)
