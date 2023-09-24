+++
title = "Package spec"
date = 2023-09-22T21:23:22+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false
+++

> 原文: [https://docs.npmjs.com/cli/v10/using-npm/package-spec](https://docs.npmjs.com/cli/v10/using-npm/package-spec)

# package-spec

Package name specifier

​	软件包名称规范

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

Commands like `npm install` and the dependency sections in the `package.json` use a package name specifier. This can be many different things that all refer to a "package". Examples include a package name, git url, tarball, or local directory. These will generally be referred to as `<package-spec>` in the help output for the npm commands that use this package name specifier.

​	像 `npm install` 命令和 `package.json` 中的依赖部分使用了软件包名称规范。这可以是许多不同的东西，都指的是一个"软件包"。例如软件包名称、git URL、tarball或本地目录。在使用软件包名称规范的npm命令的帮助输出中，通常将其称为 `<package-spec>` 。

### 软件包名称 Package name

- `[<@scope>/]<pkg>`
- `[<@scope>/]<pkg>@<tag>`
- `[<@scope>/]<pkg>@<version>`
- `[<@scope>/]<pkg>@<version range>`

Refers to a package by name, with or without a scope, and optionally tag, version, or version range. This is typically used in combination with the [registry](https://docs.npmjs.com/cli/v10/using-npm/config#registry) config to refer to a package in a registry.

​	通过名称引用一个软件包，可以带有作用域，可选地包含标签、版本或版本范围。通常与[registry](https://docs.npmjs.com/cli/v10/using-npm/config#registry)配置一起使用，以引用注册表中的软件包。

Examples:

示例：

- `npm`
- `@npmcli/arborist`
- `@npmcli/arborist@latest`
- `npm@6.13.1`
- `npm@^4.0.0`

### 别名 Aliases

- `<alias>@npm:<name>`

Primarily used by commands like `npm install` and in the dependency sections in the `package.json`, this refers to a package by an alias. The `<alias>` is the name of the package as it is reified in the `node_modules` folder, and the `<name>` refers to a package name as found in the configured registry.

​	主要用于 `npm install` 等命令和 `package.json` 中的依赖部分，通过别名引用一个软件包。 `<alias>` 是软件包在 `node_modules` 文件夹中的名称， `<name>` 是配置的注册表中的软件包名称。

See `Package name` above for more info on referring to a package by name, and [registry](https://docs.npmjs.com/cli/v10/using-npm/config#registry) for configuring which registry is used when referring to a package by name.

​	有关按名称引用软件包的更多信息，请参见上面的“软件包名称”部分，有关配置按名称引用软件包时使用的注册表，请参见[registry](https://docs.npmjs.com/cli/v10/using-npm/config#registry)。

Examples:

示例：

- `semver:@npm:@npmcli/semver-with-patch`
- `semver:@npm:semver@7.2.2`
- `semver:@npm:semver@legacy`

### 文件夹 Folders

- `<folder>`

This refers to a package on the local filesystem. Specifically this is a folder with a `package.json` file in it. This *should* always be prefixed with a `/` or `./` (or your OS equivalent) to reduce confusion. npm currently will parse a string with more than one `/` in it as a folder, but this is legacy behavior that may be removed in a future version.

​	引用本地文件系统上的软件包。具体来说，这是一个包含 `package.json` 文件的文件夹。为了减少混淆，应始终在此前加上 `/` 或 `./` （或相应的操作系统等效形式）。npm当前会将包含多个 `/` 的字符串解析为文件夹，但这是一种可能在将来的版本中删除的旧行为。

Examples:

示例：

- `./my-package`
- `/opt/npm/my-package`

### Tarballs

- `<tarball file>`
- `<tarball url>`

Examples:

示例：

- `./my-package.tgz`
- `https://registry.npmjs.org/semver/-/semver-1.0.0.tgz`

Refers to a package in a tarball format, either on the local filesystem or remotely via url. This is the format that packages exist in when uploaded to a registry.

​	引用以tarball格式存在的软件包，可以是本地文件系统上的tarball，也可以是远程URL上的tarball。这是上传到注册表时软件包所处的格式。

### git urls

- `<git:// url>`
- `<github username>/<github project>`

Refers to a package in a git repo. This can be a full git url, git shorthand, or a username/package on GitHub. You can specify a git tag, branch, or other git ref by appending `#ref`.

​	引用git仓库中的软件包。可以是完整的git URL、git简写或GitHub上的用户名/项目。可以通过添加 `#ref` 来指定git标签、分支或其他git引用。

Examples:

示例：

- `https://github.com/npm/cli.git`
- `git@github.com:npm/cli.git`
- `git+ssh://git@github.com/npm/cli#v6.0.0`
- `github:npm/cli#HEAD`
- `npm/cli#c12ea07`

### See also

- [npm-package-arg](https://npm.im/npm-package-arg)
- [scope](https://docs.npmjs.com/cli/v10/using-npm/scope)
- [config](https://docs.npmjs.com/cli/v10/using-npm/config)
