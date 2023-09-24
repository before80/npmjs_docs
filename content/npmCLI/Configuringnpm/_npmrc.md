+++
title = ".npmrc"
date = 2023-09-22T21:22:27+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false
+++

> 原文: [https://docs.npmjs.com/cli/v10/configuring-npm/npmrc](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc)

# npmrc

The npm config files

npm配置文件

Select CLI Version:Version 10.0.0 (Latest Release)

选择CLI版本：版本10.0.0（最新发布）

### 描述 Description

npm gets its config settings from the command line, environment variables, and `npmrc` files.

​	npm从命令行、环境变量和 `npmrc` 文件中获取其配置设置。

The `npm config` command can be used to update and edit the contents of the user and global npmrc files.

​	 `npm config` 命令可用于更新和编辑用户和全局npmrc文件的内容。

For a list of available configuration options, see [config](https://docs.npmjs.com/cli/v10/using-npm/config).

​	有关可用配置选项的列表，请参阅[config](https://docs.npmjs.com/cli/v10/using-npm/config)。

### 文件 Files

The four relevant files are:

​	四个相关的文件如下：

- per-project config file (/path/to/my/project/.npmrc)
- 项目配置文件（/path/to/my/project/.npmrc）
- per-user config file (~/.npmrc)
- 用户配置文件（~/.npmrc）
- global config file ($PREFIX/etc/npmrc)
- 全局配置文件（$PREFIX/etc/npmrc）
- npm builtin config file (/path/to/npm/npmrc)
- npm内置配置文件（/path/to/npm/npmrc）

All npm config files are an ini-formatted list of `key = value` parameters. Environment variables can be replaced using `${VARIABLE_NAME}`. For example:

​	所有npm配置文件都是一个ini格式的 `key = value` 参数列表。可以使用 `${VARIABLE_NAME}` 替换环境变量。例如：

```bash
prefix = ${HOME}/.npm-packages
```

Each of these files is loaded, and config options are resolved in priority order. For example, a setting in the userconfig file would override the setting in the globalconfig file.

​	这些文件中的每一个都会被加载，并按优先顺序解析配置选项。例如，用户配置文件中的设置将覆盖全局配置文件中的设置。

Array values are specified by adding "[]" after the key name. For example:

​	数组值通过在键名后添加"[]"来指定。例如：

```bash
key[] = "first value"
key[] = "second value"
```

#### 注释 Comments

Lines in `.npmrc` files are interpreted as comments when they begin with a `;` or `#` character. `.npmrc` files are parsed by [npm/ini](https://github.com/npm/ini), which specifies this comment syntax.

​	当 `.npmrc` 文件的行以`;` 或 `＃` 字符开头时，它们被解释为注释。 `.npmrc` 文件由[npm/ini](https://github.com/npm/ini)解析，该解析器指定了此注释语法。

For example:

例如：

```bash
# last modified: 01 Jan 2016
; Set a new registry for a scoped package
@myscope:registry=https://mycustomregistry.example.org
```

#### 项目配置文件 Per-project config file

When working locally in a project, a `.npmrc` file in the root of the project (ie, a sibling of `node_modules` and `package.json`) will set config values specific to this project.

​	在本地项目中工作时，在项目的根目录下的 `.npmrc` 文件（即与 `node_modules` 和 `package.json` 同级的文件）将设置特定于该项目的配置值。

Note that this only applies to the root of the project that you're running npm in. It has no effect when your module is published. For example, you can't publish a module that forces itself to install globally, or in a different location.

​	请注意，这仅适用于您在其中运行npm的项目的根目录。当您的模块被发布时，它没有任何影响。例如，您不能发布一个将自身强制安装到全局或其他位置的模块。

Additionally, this file is not read in global mode, such as when running `npm install -g`.

​	此外，在全局模式下（例如运行 `npm install -g` 时），不会读取此文件。

#### 用户配置文件 Per-user config file

`$HOME/.npmrc` (or the `userconfig` param, if set in the environment or on the command line)

​	 `$HOME/.npmrc` （如果在环境变量或命令行中设置了 `userconfig` 参数）

#### 全局配置文件 Global config file

`$PREFIX/etc/npmrc` (or the `globalconfig` param, if set above): This file is an ini-file formatted list of `key = value` parameters. Environment variables can be replaced as above.

 	`$PREFIX/etc/npmrc` （如果在上面设置了 `globalconfig` 参数）：此文件是一个ini格式的 `key = value` 参数列表。可以像上面那样替换环境变量。

#### 内置配置文件 Built-in config file

```
path/to/npm/itself/npmrc
```

This is an unchangeable "builtin" configuration file that npm keeps consistent across updates. Set fields in here using the `./configure` script that comes with npm. This is primarily for distribution maintainers to override default configs in a standard and consistent manner.

​	这是一个不可更改的“内置”配置文件，npm在更新过程中保持一致。使用npm附带的 `./configure` 脚本在此处设置字段。这主要是为了分发维护者以标准和一致的方式覆盖默认配置。

### 与认证相关的配置 Auth related configuration

The settings `_auth`, `_authToken`, `username` and `_password` must all be scoped to a specific registry. This ensures that `npm` will never send credentials to the wrong host.

​	设置 `_auth` 、 `_authToken` 、 `username` 和 `_password` 必须都针对特定的注册表进行作用域限定。这确保 `npm` 永远不会将凭据发送到错误的主机。

The full list is:

​	完整列表如下：

- `_auth` (base64 authentication string)
- `_auth` （base64编码的身份验证字符串）
- `_authToken` (authentication token)
- `_authToken` （身份验证令牌）
- `username`
- `_password`
- `email`
- `certfile` (path to certificate file)
- `certfile` （证书文件路径）
- `keyfile` (path to key file)
- `keyfile` （密钥文件路径）

In order to scope these values, they must be prefixed by a URI fragment. If the credential is meant for any request to a registry on a single host, the scope may look like `//registry.npmjs.org/:`. If it must be scoped to a specific path on the host that path may also be provided, such as `//my-custom-registry.org/unique/path:`.

​	为了对这些值进行作用域限定，它们必须以URI片段为前缀。如果凭证适用于单个主机上的任何请求，作用域可能看起来像 `//registry.npmjs.org/:` 。如果它必须作用域限定到主机上的特定路径，那么该路径也可以提供，例如 `//my-custom-registry.org/unique/path:` 。

```
; bad config
_authToken=MYTOKEN

; good config
@myorg:registry=https://somewhere-else.com/myorg
@another:registry=https://somewhere-else.com/another
//registry.npmjs.org/:_authToken=MYTOKEN
; would apply to both @myorg and @another
; //somewhere-else.com/:_authToken=MYTOKEN
; would apply only to @myorg
//somewhere-else.com/myorg/:_authToken=MYTOKEN1
; would apply only to @another
//somewhere-else.com/another/:_authToken=MYTOKEN2
```

### 另请参阅 See also

- [npm folders](https://docs.npmjs.com/cli/v10/configuring-npm/folders)
- [npm config](https://docs.npmjs.com/cli/v10/commands/npm-config)
- [config](https://docs.npmjs.com/cli/v10/using-npm/config)
- [package.json](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)
- [npm](https://docs.npmjs.com/cli/v10/commands/npm)
