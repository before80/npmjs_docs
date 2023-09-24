+++
title = "package.json"
date = 2023-09-22T21:22:49+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false
+++

> 原文: [https://docs.npmjs.com/cli/v10/configuring-npm/package-json](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)

# package.json

Specifics of npm's package.json handling

​	npm的package.json处理细节

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

This document is all you need to know about what's required in your package.json file. It must be actual JSON, not just a JavaScript object literal.

​	这个文档包含了关于package.json文件中所需内容的所有信息。它必须是一个实际的JSON，而不仅仅是一个JavaScript对象字面量。

A lot of the behavior described in this document is affected by the config settings described in [`config`](https://docs.npmjs.com/cli/v10/using-npm/config).

​	此文档中描述的许多行为受到[ `config` ](https://docs.npmjs.com/cli/v10/using-npm/config)中描述的配置设置的影响。

### name

If you plan to publish your package, the *most* important things in your package.json are the name and version fields as they will be required. The name and version together form an identifier that is assumed to be completely unique. Changes to the package should come along with changes to the version. If you don't plan to publish your package, the name and version fields are optional.

​	如果您计划发布您的软件包，那么在package.json中，name和version字段是*最*重要的，因为它们是必需的。name和version一起形成一个被认为是完全唯一的标识符。对软件包的更改应该伴随着对版本的更改。如果您不打算发布您的软件包，那么name和version字段是可选的。

The name is what your thing is called.

​	name是您的项目的名称。

Some rules:

​	一些规则：

- The name must be less than or equal to 214 characters. This includes the scope for scoped packages.
- name的长度必须小于等于214个字符。这包括作用域范围内的软件包。
- The names of scoped packages can begin with a dot or an underscore. This is not permitted without a scope.
- 作用域软件包的名称可以以点或下划线开头。没有作用域是不允许的。
- New packages must not have uppercase letters in the name.
- 新的软件包名称中不能有大写字母。
- The name ends up being part of a URL, an argument on the command line, and a folder name. Therefore, the name can't contain any non-URL-safe characters.
- name最终将成为URL的一部分、命令行上的参数和文件夹名称。因此，name不能包含任何非URL安全字符。

Some tips:

一些建议：

- Don't use the same name as a core Node module.
- 不要使用与核心Node模块相同的名称。
- Don't put "js" or "node" in the name. It's assumed that it's js, since you're writing a package.json file, and you can specify the engine using the "engines" field. (See below.)
- 不要在名称中加入"js"或"node"。由于你正在编写一个package.json文件，所以它默认是js，你可以使用"engines"字段指定引擎。（见下文。）
- The name will probably be passed as an argument to require(), so it should be something short, but also reasonably descriptive.
- name可能会作为require()的参数传递，所以它应该是一个简短的但相当描述性的名称。
- You may want to check the npm registry to see if there's something by that name already, before you get too attached to it. https://www.npmjs.com/
- 在您对其产生太大依赖之前，您可能希望在npm注册表中检查是否已经有这个名称的软件包。https://www.npmjs.com/

A name can be optionally prefixed by a scope, e.g. `@myorg/mypackage`. See [`scope`](https://docs.npmjs.com/cli/v10/using-npm/scope) for more detail.

​	名称可以选择由作用域前缀，例如 `@myorg/mypackage` 。有关详细信息，请参阅[ `scope` ](https://docs.npmjs.com/cli/v10/using-npm/scope)。

### version

If you plan to publish your package, the *most* important things in your package.json are the name and version fields as they will be required. The name and version together form an identifier that is assumed to be completely unique. Changes to the package should come along with changes to the version. If you don't plan to publish your package, the name and version fields are optional.

​	如果您计划发布您的软件包，那么在package.json中，name和version字段是*最*重要的，因为它们是必需的。name和version一起形成一个被认为是完全唯一的标识符。对软件包的更改应该伴随着对版本的更改。如果您不打算发布您的软件包，那么name和version字段是可选的。

Version must be parseable by [node-semver](https://github.com/npm/node-semver), which is bundled with npm as a dependency. (`npm install semver` to use it yourself.)

​	版本必须可以被[node-semver](https://github.com/npm/node-semver)解析，它作为npm的一个依赖项被捆绑在一起。（ `npm install semver` 可以自己使用它。）

### description

Put a description in it. It's a string. This helps people discover your package, as it's listed in `npm search`.

​	在其中放入一个描述。这是一个字符串。这有助于人们发现您的软件包，因为它会在 `npm search` 中列出。

### keywords

Put keywords in it. It's an array of strings. This helps people discover your package as it's listed in `npm search`.

​	在其中放入关键词。这是一个字符串数组。这有助于人们发现您的软件包，因为它会在 `npm search` 中列出。

### homepage

The url to the project homepage.

​	项目主页的URL。

Example:

​	示例：

```json
"homepage": "https://github.com/owner/project#readme"
```

### bugs

The url to your project's issue tracker and / or the email address to which issues should be reported. These are helpful for people who encounter issues with your package.

​	您的项目的问题跟踪器的URL和/或应报告问题的电子邮件地址。这对于遇到您的软件包问题的人们很有帮助。

It should look like this:

​	它应该如下所示：

```json
{
  "bugs": {
    "url": "https://github.com/owner/project/issues",
    "email": "project@hostname.com"
  }
}
```

You can specify either one or both values. If you want to provide only a url, you can specify the value for "bugs" as a simple string instead of an object.

​	您可以指定一个或两个值。如果您只想提供一个URL，您可以将"bugs"的值指定为一个简单的字符串，而不是一个对象。

If a url is provided, it will be used by the `npm bugs` command.

​	如果提供了一个URL，它将被 `npm bugs` 命令使用。

### license

You should specify a license for your package so that people know how they are permitted to use it, and any restrictions you're placing on it.

​	您应该为您的软件包指定一个许可证，以便人们知道他们如何使用它，以及您对它的任何限制。

If you're using a common license such as BSD-2-Clause or MIT, add a current SPDX license identifier for the license you're using, like this:

​	如果您使用的是像BSD-2-Clause或MIT这样的常见许可证，在您使用的许可证上添加一个当前的SPDX许可证标识符，如下所示：

```json
{
  "license" : "BSD-3-Clause"
}
```

You can check [the full list of SPDX license IDs](https://spdx.org/licenses/). Ideally you should pick one that is [OSI](https://opensource.org/licenses/) approved.

​	您可以检查[完整的SPDX许可证ID列表](https://spdx.org/licenses/)。理想情况下，您应该选择一个[OSI](https://opensource.org/licenses/)批准的许可证。

If your package is licensed under multiple common licenses, use an [SPDX license expression syntax version 2.0 string](https://spdx.dev/specifications/), like this:

​	如果您的软件包根据多个常见许可证授权，请使用[SPDX许可证表达式语法版本2.0字符串](https://spdx.dev/specifications/)，如下所示：

```json
{
  "license" : "(ISC OR GPL-3.0)"
}
```

If you are using a license that hasn't been assigned an SPDX identifier, or if you are using a custom license, use a string value like this one:

​	如果您使用的许可证尚未分配SPDX标识符，或者如果您使用的是自定义许可证，请使用类似于下面的字符串值：

```json
{
  "license" : "SEE LICENSE IN <filename>"
}
```

Then include a file named `<filename>` at the top level of the package.

​	然后在软件包的顶级目录中包含一个名为 `<filename>` 的文件。

Some old packages used license objects or a "licenses" property containing an array of license objects:

​	一些旧的软件包使用许可证对象或包含许可证对象数组的"licenses"属性：

```json
// Not valid metadata
// 不是有效的元数据
{
  "license" : {
    "type" : "ISC",
    "url" : "https://opensource.org/licenses/ISC"
  }
}

// Not valid metadata
// 不是有效的元数据
{
  "licenses" : [
    {
      "type": "MIT",
      "url": "https://www.opensource.org/licenses/mit-license.php"
    },
    {
      "type": "Apache-2.0",
      "url": "https://opensource.org/licenses/apache2.0.php"
    }
  ]
}
```

Those styles are now deprecated. Instead, use SPDX expressions, like this:

​	这些样式现在已经弃用。使用SPDX表达式，如下所示：

```json
{
  "license": "ISC"
}
```



```json
{
  "license": "(MIT OR Apache-2.0)"
}
```

Finally, if you do not wish to grant others the right to use a private or unpublished package under any terms:

​	最后，如果您不希望以任何条款授予他人使用私有或未发布的软件包的权利：

```json
{
  "license": "UNLICENSED"
}
```

Consider also setting `"private": true` to prevent accidental publication.

​	还可以设置 `"private": true` 以防止意外发布。

### 人员字段：作者、贡献者 people fields: author, contributors

The "author" is one person. "contributors" is an array of people. A "person" is an object with a "name" field and optionally "url" and "email", like this:

​	"author"是一个人。"contributors"是一个人的数组。一个"person"是一个对象，有一个"name"字段，还可以有"url"和"email"（可选），如下所示：

```json
{
  "name" : "Barney Rubble",
  "email" : "b@rubble.com",
  "url" : "http://barnyrubble.tumblr.com/"
}
```

Or you can shorten that all into a single string, and npm will parse it for you:

​	或者您可以将所有内容缩短为一个字符串，npm会为您解析它：

```json
{
  "author": "Barney Rubble <b@rubble.com> (http://barnyrubble.tumblr.com/)"
}
```

Both email and url are optional either way.

​	无论哪种方式，email和url都是可选的。

npm also sets a top-level "maintainers" field with your npm user info.

​	npm还会设置一个顶级的"maintainers"字段，其中包含您的npm用户信息。

### 资助 funding

You can specify an object containing a URL that provides up-to-date information about ways to help fund development of your package, or a string URL, or an array of these:

​	您可以指定一个包含提供有关帮助资助您的软件包开发的最新信息的URL的对象，或者一个字符串URL，或者这两者的数组：

```json
{
  "funding": {
    "type" : "individual",
    "url" : "http://example.com/donate"
  },

  "funding": {
    "type" : "patreon",
    "url" : "https://www.patreon.com/my-account"
  },

  "funding": "http://example.com/donate",

  "funding": [
    {
      "type" : "individual",
      "url" : "http://example.com/donate"
    },
    "http://example.com/donateAlso",
    {
      "type" : "patreon",
      "url" : "https://www.patreon.com/my-account"
    }
  ]
}
```

Users can use the `npm fund` subcommand to list the `funding` URLs of all dependencies of their project, direct and indirect. A shortcut to visit each funding url is also available when providing the project name such as: `npm fund <projectname>` (when there are multiple URLs, the first one will be visited)

​	用户可以使用 `npm fund` 子命令列出其项目的所有依赖项（直接和间接）的 `funding` URL。当提供项目名称时，还可以使用快捷方式访问每个资助URL，例如： `npm fund <projectname>` （当有多个URL时，将访问第一个URL）。

### files

The optional `files` field is an array of file patterns that describes the entries to be included when your package is installed as a dependency. File patterns follow a similar syntax to `.gitignore`, but reversed: including a file, directory, or glob pattern (`*`, `**/*`, and such) will make it so that file is included in the tarball when it's packed. Omitting the field will make it default to `["*"]`, which means it will include all files.

​	可选的 `files` 字段是一个文件模式的数组，描述了在将您的软件包安装为依赖项时要包含的条目。文件模式遵循与 `.gitignore` 类似的语法，但是相反：包含一个文件、目录或glob模式（ `*` 、 `**/*` 等）将使该文件在打包时包含在tarball中。省略该字段将使其默认为 `["*"]` ，这意味着它将包含所有文件。

Some special files and directories are also included or excluded regardless of whether they exist in the `files` array (see below).

​	某些特殊的文件和目录也会被包含或排除，而不管它们是否存在于 `files` 数组中（见下文）。

You can also provide a `.npmignore` file in the root of your package or in subdirectories, which will keep files from being included. At the root of your package it will not override the "files" field, but in subdirectories it will. The `.npmignore` file works just like a `.gitignore`. If there is a `.gitignore` file, and `.npmignore` is missing, `.gitignore`'s contents will be used instead.

​	您还可以在包的根目录或子目录中提供一个 `.npmignore` 文件，以防止文件被包含在内。在包的根目录中，它不会覆盖"files"字段，但在子目录中会覆盖。 `.npmignore` 文件的工作方式与 `.gitignore` 文件相同。如果存在 `.gitignore` 文件，并且缺少 `.npmignore` 文件，则将使用 `.gitignore` 文件的内容。

Certain files are always included, regardless of settings:

​	无论设置如何，某些文件始终会被包含在内：

- `package.json`
- `README`
- `LICENSE` / `LICENCE`
- The file in the "main" field
- "main"字段中的文件
- The file(s) in the "bin" field
- "bin"字段中的文件（们）

`README` & `LICENSE` can have any case and extension.

​	`README` 和 `LICENSE` 可以具有任何大小写和扩展名。

Conversely, some files are always ignored:

​	相反，某些文件始终会被忽略：

- `.git`
- `CVS`
- `.svn`
- `.hg`
- `.lock-wscript`
- `.wafpickle-N`
- `.*.swp`
- `.DS_Store`
- `._*`
- `npm-debug.log`
- `.npmrc`
- `node_modules`
- `config.gypi`
- `*.orig`
- `package-lock.json` (use [`npm-shrinkwrap.json`](https://docs.npmjs.com/cli/v10/configuring-npm/npm-shrinkwrap-json) if you wish it to be published)
- `package-lock.json` （如果希望发布它，请使用[ `npm-shrinkwrap.json` ](https://docs.npmjs.com/cli/v10/configuring-npm/npm-shrinkwrap-json)）

### main

The main field is a module ID that is the primary entry point to your program. That is, if your package is named `foo`, and a user installs it, and then does `require("foo")`, then your main module's exports object will be returned.

​	main字段是一个模块ID，它是您程序的主要入口点。也就是说，如果您的软件包名为 `foo` ，用户安装了它，然后执行 `require("foo")` ，那么您的主模块的导出对象将被返回。

This should be a module relative to the root of your package folder.

​	这应该是相对于您软件包文件夹的根目录的模块。

For most modules, it makes the most sense to have a main script and often not much else.

​	对于大多数模块来说，只有一个主要的脚本是最合理的，通常不需要太多其他文件。

If `main` is not set, it defaults to `index.js` in the package's root folder.

​	如果未设置 `main` ，它默认为软件包根目录中的 `index.js` 。

### browser

If your module is meant to be used client-side the browser field should be used instead of the main field. This is helpful to hint users that it might rely on primitives that aren't available in Node.js modules. (e.g. `window`)

​	如果您的模块是用于客户端的，则应使用browser字段，而不是main字段。这有助于提示用户，它可能依赖于在Node.js模块中不可用的基本功能（例如 `window` ）。

### bin

A lot of packages have one or more executable files that they'd like to install into the PATH. npm makes this pretty easy (in fact, it uses this feature to install the "npm" executable.)

​	许多软件包都有一个或多个可执行文件，它们希望安装到PATH中。npm使这变得非常容易（实际上，它使用此功能来安装“npm”可执行文件）。

To use this, supply a `bin` field in your package.json which is a map of command name to local file name. When this package is installed globally, that file will be either linked inside the global bins directory or a cmd (Windows Command File) will be created which executes the specified file in the `bin` field, so it is available to run by `name` or `name.cmd` (on Windows PowerShell). When this package is installed as a dependency in another package, the file will be linked where it will be available to that package either directly by `npm exec` or by name in other scripts when invoking them via `npm run-script`.

​	要使用此功能，请在您的package.json中提供一个 `bin` 字段，该字段是一个命令名称到本地文件名称的映射。当此软件包在全局范围内安装时，该文件将被链接到全局bins目录中，或者将创建一个cmd（Windows命令文件），该文件执行 `bin` 字段中指定的文件，因此可以通过 `name` 或 `name.cmd` （在Windows PowerShell中）运行它。当此软件包作为另一个软件包的依赖项安装时，该文件将被链接到该软件包中，可以通过 `npm exec` 直接访问，或者在调用其他脚本时通过名称运行它们时使用 `npm run-script` 。

For example, myapp could have this:

​	例如，myapp可以有以下内容：

```json
{
  "bin": {
    "myapp": "./cli.js"
  }
}
```

So, when you install myapp, in case of unix-like OS it'll create a symlink from the `cli.js` script to `/usr/local/bin/myapp` and in case of windows it will create a cmd file usually at `C:\Users\{Username}\AppData\Roaming\npm\myapp.cmd` which runs the `cli.js` script.

​	因此，当您安装myapp时，在类Unix操作系统中，它将创建一个从 `cli.js` 脚本到 `/usr/local/bin/myapp` 的符号链接，在Windows中，它将创建一个cmd文件，通常位于 `C:\Users\{Username}\AppData\Roaming\npm\myapp.cmd` ，该文件运行 `cli.js` 脚本。

If you have a single executable, and its name should be the name of the package, then you can just supply it as a string. For example:

​	如果您只有一个可执行文件，并且其名称应该是软件包的名称，则可以将其直接提供为字符串。例如：

```json
{
  "name": "my-program",
  "version": "1.2.5",
  "bin": "./path/to/program"
}
```

would be the same as this:

与以下内容相同：

```json
{
  "name": "my-program",
  "version": "1.2.5",
  "bin": {
    "my-program": "./path/to/program"
  }
}
```

Please make sure that your file(s) referenced in `bin` starts with `#!/usr/bin/env node`, otherwise the scripts are started without the node executable!

​	请确保在 `bin` 中引用的文件以 `#!/usr/bin/env node` 开头，否则脚本将在没有node可执行文件的情况下启动！

Note that you can also set the executable files using [directories.bin](#directoriesbin).

​	请注意，您也可以使用[directories.bin](#directoriesbin)来设置可执行文件。

See [folders](https://docs.npmjs.com/cli/v10/configuring-npm/folders#executables) for more info on executables.

​	有关更多关于可执行文件的信息，请参见[folders](https://docs.npmjs.com/cli/v10/configuring-npm/folders#executables)。

### man

Specify either a single file or an array of filenames to put in place for the `man` program to find.

​	指定要放置在 `man` 程序中的单个文件或文件数组。

If only a single file is provided, then it's installed such that it is the result from `man <pkgname>`, regardless of its actual filename. For example:

​	如果只提供一个单独的文件，则它将被安装为 `man <pkgname>` 的结果，而不管其实际文件名。例如：

```json
{
  "name": "foo",
  "version": "1.2.3",
  "description": "A packaged foo fooer for fooing foos",
  "main": "foo.js",
  "man": "./man/doc.1"
}
```

would link the `./man/doc.1` file in such that it is the target for `man foo`

将链接 `./man/doc.1` 文件，以便它是 `man foo` 的目标。

If the filename doesn't start with the package name, then it's prefixed. So, this:

​	如果文件名不以软件包名称开头，则会添加前缀。因此，这样：

```json
{
  "name": "foo",
  "version": "1.2.3",
  "description": "A packaged foo fooer for fooing foos",
  "main": "foo.js",
  "man": [
    "./man/foo.1",
    "./man/bar.1"
  ]
}
```

will create files to do `man foo` and `man foo-bar`.

将创建文件以执行 `man foo` 和 `man foo-bar` 。

Man files must end with a number, and optionally a `.gz` suffix if they are compressed. The number dictates which man section the file is installed into.

​	Man文件必须以数字结尾，如果它们被压缩，则可以选择使用 `.gz` 后缀。数字决定文件安装到哪个man章节。

```json
{
  "name": "foo",
  "version": "1.2.3",
  "description": "A packaged foo fooer for fooing foos",
  "main": "foo.js",
  "man": [
    "./man/foo.1",
    "./man/foo.2"
  ]
}
```

will create entries for `man foo` and `man 2 foo`

将创建 `man foo` 和 `man 2 foo` 的条目。

### directories

The CommonJS [Packages](http://wiki.commonjs.org/wiki/Packages/1.0) spec details a few ways that you can indicate the structure of your package using a `directories` object. If you look at [npm's package.json](https://registry.npmjs.org/npm/latest), you'll see that it has directories for doc, lib, and man.

​	CommonJS [Packages](http://wiki.commonjs.org/wiki/Packages/1.0)规范详细介绍了几种使用 `directories` 对象指示软件包结构的方法。如果查看[npm的package.json](https://registry.npmjs.org/npm/latest)，您将看到它具有用于doc、lib和man的目录。

In the future, this information may be used in other creative ways.

​	将来，此信息可能会以其他创造性的方式使用。

#### directories.bin

If you specify a `bin` directory in `directories.bin`, all the files in that folder will be added.

​	如果在 `directories.bin` 中指定了 `bin` 目录，则该文件夹中的所有文件都将被添加。

Because of the way the `bin` directive works, specifying both a `bin` path and setting `directories.bin` is an error. If you want to specify individual files, use `bin`, and for all the files in an existing `bin` directory, use `directories.bin`.

​	由于 `bin` 指令的工作方式，同时指定 `bin` 路径和设置 `directories.bin` 是一个错误。如果要指定单个文件，请使用 `bin` ，如果要使用现有 `bin` 目录中的所有文件，请使用 `directories.bin` 。

#### directories.man

A folder that is full of man pages. Sugar to generate a "man" array by walking the folder.

​	一个包含man页面的文件夹。通过遍历文件夹生成“man”数组。

### repository

Specify the place where your code lives. This is helpful for people who want to contribute. If the git repo is on GitHub, then the `npm docs` command will be able to find you.

​	指定代码所在的位置。这对于想要贡献代码的人很有帮助。如果git仓库在GitHub上，那么 `npm docs` 命令将能够找到您。

Do it like this:

​	请按照以下方式进行设置：

```json
{
  "repository": {
    "type": "git",
    "url": "https://github.com/npm/cli.git"
  }
}
```

The URL should be a publicly available (perhaps read-only) url that can be handed directly to a VCS program without any modification. It should not be a url to an html project page that you put in your browser. It's for computers.

​	URL应该是一个公开可用（可能是只读）的URL，可以直接传递给VCS程序，而不需要进行任何修改。它不应该是一个在浏览器中打开的html项目页面的URL。它是为计算机而不是人类。

For GitHub, GitHub gist, Bitbucket, or GitLab repositories you can use the same shortcut syntax you use for `npm install`:

​	对于GitHub、GitHub gist、Bitbucket或GitLab仓库，您可以使用与 `npm install` 相同的快捷语法：

```json
{
  "repository": "npm/npm",

  "repository": "github:user/repo",

  "repository": "gist:11081aaa281",

  "repository": "bitbucket:user/repo",

  "repository": "gitlab:user/repo"
}
```

If the `package.json` for your package is not in the root directory (for example if it is part of a monorepo), you can specify the directory in which it lives:

​	如果您的软件包的 `package.json` 不在根目录中（例如，如果它是monorepo的一部分），您可以指定它所在的目录：

```json
{
  "repository": {
    "type": "git",
    "url": "https://github.com/facebook/react.git",
    "directory": "packages/react-dom"
  }
}
```

### scripts

The "scripts" property is a dictionary containing script commands that are run at various times in the lifecycle of your package. The key is the lifecycle event, and the value is the command to run at that point.

​	"scripts"属性是一个包含在软件包的生命周期中的各个时间点运行的脚本命令的字典。键是生命周期事件，值是在该时间点运行的命令。

See [`scripts`](https://docs.npmjs.com/cli/v10/using-npm/scripts) to find out more about writing package scripts.

​	有关编写软件包脚本的更多信息，请参见[ `scripts` ](https://docs.npmjs.com/cli/v10/using-npm/scripts)。

### config

A "config" object can be used to set configuration parameters used in package scripts that persist across upgrades. For instance, if a package had the following:

​	可以使用"config"对象设置在软件包脚本中使用的配置参数，这些参数在升级过程中保持不变。例如，如果软件包具有以下内容：

```json
{
  "name": "foo",
  "config": {
    "port": "8080"
  }
}
```

It could also have a "start" command that referenced the `npm_package_config_port` environment variable.

​	它还可以具有一个引用 `npm_package_config_port` 环境变量的"start"命令。

### dependencies

Dependencies are specified in a simple object that maps a package name to a version range. The version range is a string which has one or more space-separated descriptors. Dependencies can also be identified with a tarball or git URL.

​	依赖项在一个简单的对象中指定，该对象将软件包名称映射到版本范围。版本范围是一个字符串，其中有一个或多个以空格分隔的描述符。依赖项也可以用tarball或git URL标识。

**Please do not put test harnesses or transpilers or other "development" time tools in your `dependencies` object.** See `devDependencies`, below.

​	**请不要将测试工具、转译器或其他“开发”时工具放在 `dependencies` 对象中。**请参见下面的 `devDependencies` 。

See [semver](https://github.com/npm/node-semver#versions) for more details about specifying version ranges.

​	有关指定版本范围的更多详细信息，请参见[semver](https://github.com/npm/node-semver#versions)。

- `version` Must match `version` exactly
- `version`  必须与 `version` 完全匹配
- `>version` Must be greater than `version`
- `>version`  必须大于 `version` 
- `>=version` etc
- `<version`
- `<=version`
- `~version` "Approximately equivalent to version" See [semver](https://github.com/npm/node-semver#versions)
- `~version`  "大致等于版本"，请参见[semver](https://github.com/npm/node-semver#versions)
- `^version` "Compatible with version" See [semver](https://github.com/npm/node-semver#versions)
- `^version`  "与版本兼容"，请参见[semver](https://github.com/npm/node-semver#versions)
- `1.2.x` 1.2.0, 1.2.1, etc., but not 1.3.0
- `1.2.x`  1.2.0、1.2.1等，但不包括1.3.0
- `http://...` See 'URLs as Dependencies' below
- `http://...`  请参见下面的“URL作为依赖项”
- `*` Matches any version
- `*`  匹配任何版本
- `""` (just an empty string) Same as `*`
- `""` （空字符串）与 `*` 相同
- `version1 - version2` Same as `>=version1 <=version2`.
- `version1 - version2`  与 `>=version1 <=version2` 相同。
- `range1 || range2` Passes if either range1 or range2 are satisfied.
- `range1 || range2`  如果满足range1或range2，则通过。
- `git...` See 'Git URLs as Dependencies' below
- `git...`  请参见下面的“Git URL作为依赖项”
- `user/repo` See 'GitHub URLs' below
- `user/repo`  请参见下面的“GitHub URL”
- `tag` A specific version tagged and published as `tag` See [`npm dist-tag`](https://docs.npmjs.com/cli/v10/commands/npm-dist-tag)
- `tag`  作为 `tag` 标记和发布的特定版本，请参见[ `npm dist-tag` ](https://docs.npmjs.com/cli/v10/commands/npm-dist-tag)
- `path/path/path` See [Local Paths](#local-paths) below
- `path/path/path`  请参见下面的[本地路径](#local-paths)

For example, these are all valid:

​	例如，这些都是有效的：

```json
{
  "dependencies": {
    "foo": "1.0.0 - 2.9999.9999",
    "bar": ">=1.0.2 <2.1.2",
    "baz": ">1.0.2 <=2.3.4",
    "boo": "2.0.1",
    "qux": "<1.0.0 || >=2.3.1 <2.4.5 || >=2.5.2 <3.0.0",
    "asd": "http://asdf.com/asdf.tar.gz",
    "til": "~1.2",
    "elf": "~1.2.3",
    "two": "2.x",
    "thr": "3.3.x",
    "lat": "latest",
    "dyl": "file:../dyl"
  }
}
```

#### 作为依赖项的URL URLs as Dependencies

You may specify a tarball URL in place of a version range.

​	您可以在版本范围的位置指定一个tarball URL。

This tarball will be downloaded and installed locally to your package at install time.

​	该tarball将在安装时下载并本地安装到您的软件包中。

#### 作为依赖项的Git URL Git URLs as Dependencies

Git urls are of the form:

​	Git URL的格式如下：

```bash
<protocol>://[<user>[:<password>]@]<hostname>[:<port>][:][/]<path>[#<commit-ish> | #semver:<semver>]
```

`<protocol>` is one of `git`, `git+ssh`, `git+http`, `git+https`, or `git+file`.

`<protocol>` 可以是 `git` 、 `git+ssh` 、 `git+http` 、 `git+https` 或 `git+file` 之一。

If `#<commit-ish>` is provided, it will be used to clone exactly that commit. If the commit-ish has the format `#semver:<semver>`, `<semver>` can be any valid semver range or exact version, and npm will look for any tags or refs matching that range in the remote repository, much as it would for a registry dependency. If neither `#<commit-ish>` or `#semver:<semver>` is specified, then the default branch is used.

​	如果提供了 `#<commit-ish>` ，它将用于克隆确切的提交。如果commit-ish的格式为 `#semver:<semver>` ， `<semver>` 可以是任何有效的semver范围或确切的版本，并且npm将在远程存储库中查找与该范围匹配的任何标签或引用，就像对于注册表依赖项一样。如果未指定 `#<commit-ish>` 或 `#semver:<semver>` ，则使用默认分支。

Examples:

示例：

```bash
git+ssh://git@github.com:npm/cli.git#v1.0.27
git+ssh://git@github.com:npm/cli#semver:^5.0
git+https://isaacs@github.com/npm/cli.git
git://github.com/npm/cli.git#v1.0.27
```

When installing from a `git` repository, the presence of certain fields in the `package.json` will cause npm to believe it needs to perform a build. To do so your repository will be cloned into a temporary directory, all of its deps installed, relevant scripts run, and the resulting directory packed and installed.

​	在从 `git` 存储库安装时， `package.json` 中的某些字段的存在会使npm认为它需要执行构建操作。为此，将克隆您的存储库到一个临时目录中，安装所有的依赖项，运行相关的脚本，然后将结果目录打包并安装。

This flow will occur if your git dependency uses `workspaces`, or if any of the following scripts are present:

​	如果您的git依赖项使用了 `workspaces` ，或者如果以下任何脚本存在，将发生这种流程：

- `build`
- `prepare`
- `prepack`
- `preinstall`
- `install`
- `postinstall`

If your git repository includes pre-built artifacts, you will likely want to make sure that none of the above scripts are defined, or your dependency will be rebuilt for every installation.

​	如果您的git存储库包含预构建的构件，您可能希望确保没有定义上述任何脚本，否则您的依赖项将在每次安装时重新构建。

#### GitHub URLs

As of version 1.1.65, you can refer to GitHub urls as just "foo": "user/foo-project". Just as with git URLs, a `commit-ish` suffix can be included. For example:

​	从版本1.1.65开始，您可以将GitHub URL简写为"user/foo-project"。与git URL一样，可以包含 `commit-ish` 后缀。例如：

```json
{
  "name": "foo",
  "version": "0.0.0",
  "dependencies": {
    "express": "expressjs/express",
    "mocha": "mochajs/mocha#4727d357ea",
    "module": "user/repo#feature\/branch"
  }
}
```

#### 本地路径 Local Paths

As of version 2.0.0 you can provide a path to a local directory that contains a package. Local paths can be saved using `npm install -S` or `npm install --save`, using any of these forms:

​	从版本2.0.0开始，您可以提供指向包含软件包的本地目录的路径。可以使用 `npm install -S` 或 `npm install --save` 将本地路径保存为依赖项，使用以下任意形式：

```bash
../foo/bar
~/foo/bar
./foo/bar
/foo/bar
```

in which case they will be normalized to a relative path and added to your `package.json`. For example:

在这种情况下，它们将被规范化为相对路径并添加到您的 `package.json` 中。例如：

```json
{
  "name": "baz",
  "dependencies": {
    "bar": "file:../foo/bar"
  }
}
```

This feature is helpful for local offline development and creating tests that require npm installing where you don't want to hit an external server, but should not be used when publishing packages to the public registry.

​	这个功能对于本地离线开发和创建需要npm安装的测试非常有用，而您不希望访问外部服务器，但在发布软件包到公共注册表时不应使用。

*note*: Packages linked by local path will not have their own dependencies installed when `npm install` is ran in this case. You must run `npm install` from inside the local path itself.

*注意*：使用本地路径链接的软件包在运行 `npm install` 时不会安装其自己的依赖项。在这种情况下，您必须从本地路径本身运行 `npm install` 。

### devDependencies

If someone is planning on downloading and using your module in their program, then they probably don't want or need to download and build the external test or documentation framework that you use.

​	如果有人计划下载和使用您的模块在他们的程序中，那么他们可能不希望或不需要下载和构建您使用的外部测试或文档框架。

In this case, it's best to map these additional items in a `devDependencies` object.

​	在这种情况下，最好将这些额外的项目映射到  `devDependencies`  对象中。

These things will be installed when doing `npm link` or `npm install` from the root of a package, and can be managed like any other npm configuration param. See [`config`](https://docs.npmjs.com/cli/v10/using-npm/config) for more on the topic.

​	这些内容将在从软件包的根目录执行  `npm link`  或  `npm install`  时安装，并且可以像任何其他 npm 配置参数一样进行管理。有关更多详细信息，请参阅 [ `config` ](https://docs.npmjs.com/cli/v10/using-npm/config)。

For build steps that are not platform-specific, such as compiling CoffeeScript or other languages to JavaScript, use the `prepare` script to do this, and make the required package a devDependency.

​	对于不特定于平台的构建步骤（例如将 CoffeeScript 或其他语言编译为 JavaScript），请使用  `prepare`  脚本来完成此操作，并将所需的软件包设置为  `devDependencies` 。

For example:

​	例如：

```json
{
  "name": "ethopia-waza",
  "description": "a delightfully fruity coffee varietal",
  "version": "1.2.3",
  "devDependencies": {
    "coffee-script": "~1.6.3"
  },
  "scripts": {
    "prepare": "coffee -o lib/ -c src/waza.coffee"
  },
  "main": "lib/waza.js"
}
```

The `prepare` script will be run before publishing, so that users can consume the functionality without requiring them to compile it themselves. In dev mode (ie, locally running `npm install`), it'll run this script as well, so that you can test it easily.

​	`prepare`  脚本将在发布之前运行，以便用户可以在不要求他们自己进行编译的情况下使用功能。在开发模式下（即在本地运行  `npm install` ），它也会运行此脚本，以便您可以轻松测试它。

### peerDependencies

In some cases, you want to express the compatibility of your package with a host tool or library, while not necessarily doing a `require` of this host. This is usually referred to as a *plugin*. Notably, your module may be exposing a specific interface, expected and specified by the host documentation.

​	在某些情况下，您希望表达您的软件包与主机工具或库的兼容性，而不一定要对此主机进行  `require` 。这通常称为*插件*。值得注意的是，您的模块可能会公开主机文档所期望和指定的特定接口。

For example:

​	例如：

```json
{
  "name": "tea-latte",
  "version": "1.3.5",
  "peerDependencies": {
    "tea": "2.x"
  }
}
```

This ensures your package `tea-latte` can be installed *along* with the second major version of the host package `tea` only. `npm install tea-latte` could possibly yield the following dependency graph:

​	这样可以确保您的软件包  `tea-latte`  仅能与第二个主要版本的主机软件包  `tea`  一起安装。 `npm install tea-latte`  可能会产生以下依赖图：

```bash
├── tea-latte@1.3.5
└── tea@2.2.0
```

In npm versions 3 through 6, `peerDependencies` were not automatically installed, and would raise a warning if an invalid version of the peer dependency was found in the tree. As of npm v7, peerDependencies *are* installed by default.

​	在 npm 3 到 6 版本中， `peerDependencies`  不会自动安装，并且如果在树中找到与对等依赖项的无效版本，则会引发警告。从 npm v7 开始，默认情况下会安装 peerDependencies。

Trying to install another plugin with a conflicting requirement may cause an error if the tree cannot be resolved correctly. For this reason, make sure your plugin requirement is as broad as possible, and not to lock it down to specific patch versions.

​	如果尝试安装与冲突要求的另一个插件可能会导致错误，如果无法正确解析树，则会出现错误。因此，请确保您的插件要求尽可能广泛，并且不要将其锁定到特定的修补程序版本。

Assuming the host complies with [semver](https://semver.org/), only changes in the host package's major version will break your plugin. Thus, if you've worked with every 1.x version of the host package, use `"^1.0"` or `"1.x"` to express this. If you depend on features introduced in 1.5.2, use `"^1.5.2"`.

​	假设主机符合 [semver](https://semver.org/)，则只有主机软件包的主要版本更改才会破坏您的插件。因此，如果您使用过主机软件包的每个 1.x 版本，请使用  `"^1.0"`  或  `"1.x"`  表示这一点。如果您依赖于 1.5.2 中引入的功能，请使用  `"^1.5.2"` 。

### peerDependenciesMeta

When a user installs your package, npm will emit warnings if packages specified in `peerDependencies` are not already installed. The `peerDependenciesMeta` field serves to provide npm more information on how your peer dependencies are to be used. Specifically, it allows peer dependencies to be marked as optional.

​	当用户安装您的软件包时，如果在  `peerDependencies`  中指定的软件包未安装，npm 将发出警告。 `peerDependenciesMeta`  字段用于向 npm 提供有关如何使用对等依赖项的更多信息。具体来说，它允许将对等依赖项标记为可选。

For example:

例如：

```json
{
  "name": "tea-latte",
  "version": "1.3.5",
  "peerDependencies": {
    "tea": "2.x",
    "soy-milk": "1.2"
  },
  "peerDependenciesMeta": {
    "soy-milk": {
      "optional": true
    }
  }
}
```

Marking a peer dependency as optional ensures npm will not emit a warning if the `soy-milk` package is not installed on the host. This allows you to integrate and interact with a variety of host packages without requiring all of them to be installed.

​	将对等依赖项标记为可选，可以确保如果主机上未安装  `soy-milk`  软件包，则 npm 不会发出警告。这样，您可以集成和与各种主机软件包进行交互，而无需安装所有软件包。

### bundleDependencies

This defines an array of package names that will be bundled when publishing the package.

​	这定义了在发布软件包时将捆绑的一组软件包名称。

In cases where you need to preserve npm packages locally or have them available through a single file download, you can bundle the packages in a tarball file by specifying the package names in the `bundleDependencies` array and executing `npm pack`.

​	在需要在本地保留 npm 软件包或通过单个文件下载使其可用的情况下，可以通过在  `bundleDependencies`  数组中指定软件包名称并执行  `npm pack`  来将软件包捆绑到 tarball 文件中。

For example:

​	例如：

If we define a package.json like this:

​	如果我们定义一个如下的 package.json：

```json
{
  "name": "awesome-web-framework",
  "version": "1.0.0",
  "bundleDependencies": [
    "renderized",
    "super-streams"
  ]
}
```

we can obtain `awesome-web-framework-1.0.0.tgz` file by running `npm pack`. This file contains the dependencies `renderized` and `super-streams` which can be installed in a new project by executing `npm install awesome-web-framework-1.0.0.tgz`. Note that the package names do not include any versions, as that information is specified in `dependencies`.

​	我们可以通过运行  `npm pack`  来获得  `awesome-web-framework-1.0.0.tgz`  文件。该文件包含了依赖项  `renderized`  和  `super-streams` ，可以通过执行  `npm install awesome-web-framework-1.0.0.tgz`  在新项目中安装它们。请注意，软件包名称不包含任何版本信息，因为该信息在  `dependencies`  中指定。

If this is spelled `"bundledDependencies"`, then that is also honored.

​	如果将其拼写为  `"bundledDependencies"` ，则也会被接受。

Alternatively, `"bundleDependencies"` can be defined as a boolean value. A value of `true` will bundle all dependencies, a value of `false` will bundle none.

​	或者， `"bundleDependencies"`  可以定义为布尔值。 `true`  的值将捆绑所有依赖项， `false`  的值将不捆绑任何依赖项。

### optionalDependencies

If a dependency can be used, but you would like npm to proceed if it cannot be found or fails to install, then you may put it in the `optionalDependencies` object. This is a map of package name to version or url, just like the `dependencies` object. The difference is that build failures do not cause installation to fail. Running `npm install --omit=optional` will prevent these dependencies from being installed.

​	如果一个依赖项可以使用，但是如果找不到或安装失败，您希望npm继续进行，则可以将其放在 `optionalDependencies` 对象中。这是一个包名称到版本或URL的映射，就像 `dependencies` 对象一样。不同之处在于构建失败不会导致安装失败。运行 `npm install --omit=optional` 将阻止安装这些依赖项。

It is still your program's responsibility to handle the lack of the dependency. For example, something like this:

​	仍然需要您的程序负责处理缺少依赖项的情况。例如，类似于以下内容：

```js
try {
  var foo = require('foo')
  var fooVersion = require('foo/package.json').version
} catch (er) {
  foo = null
}
if ( notGoodFooVersion(fooVersion) ) {
  foo = null
}

// .. then later in your program ..

if (foo) {
  foo.doFooThings()
}
```

Entries in `optionalDependencies` will override entries of the same name in `dependencies`, so it's usually best to only put in one place.

​	`optionalDependencies` 中的条目将覆盖 `dependencies` 中相同名称的条目，因此通常最好只放在一个地方。

### overrides

If you need to make specific changes to dependencies of your dependencies, for example replacing the version of a dependency with a known security issue, replacing an existing dependency with a fork, or making sure that the same version of a package is used everywhere, then you may add an override.

​	如果您需要对依赖项的依赖项进行特定更改，例如替换具有已知安全问题的依赖项的版本，替换现有依赖项的分支，或确保在所有地方使用相同版本的软件包，则可以添加一个override。

Overrides provide a way to replace a package in your dependency tree with another version, or another package entirely. These changes can be scoped as specific or as vague as desired.

​	overrides提供了一种用另一个版本或完全不同的软件包替换依赖树中的软件包的方法。这些更改可以具体或模糊地限定。

To make sure the package `foo` is always installed as version `1.0.0` no matter what version your dependencies rely on:

​	为了确保软件包 `foo` 始终安装为 `1.0.0` 版本，无论您的依赖项依赖于什么版本：

```json
{
  "overrides": {
    "foo": "1.0.0"
  }
}
```

The above is a short hand notation, the full object form can be used to allow overriding a package itself as well as a child of the package. This will cause `foo` to always be `1.0.0` while also making `bar` at any depth beyond `foo` also `1.0.0`:

​	上述是一种简写表示法，完整的对象形式可以用于允许覆盖软件包本身以及软件包的子级。这将导致 `foo` 始终为 `1.0.0` ，同时使 `foo` 以任何深度超出 `foo` 的 `bar` 也为 `1.0.0` ：

```json
{
  "overrides": {
    "foo": {
      ".": "1.0.0",
      "bar": "1.0.0"
    }
  }
}
```

To only override `foo` to be `1.0.0` when it's a child (or grandchild, or great grandchild, etc) of the package `bar`:

​	仅在 `foo` 是 `bar` 的子级（或子子级，或曾子级等）时，将 `foo` 覆盖为 `1.0.0` ：

```json
{
  "overrides": {
    "bar": {
      "foo": "1.0.0"
    }
  }
}
```

Keys can be nested to any arbitrary length. To override `foo` only when it's a child of `bar` and only when `bar` is a child of `baz`:

​	键可以嵌套到任意长度。仅在 `foo` 是 `bar` 的子级，且只有在 `bar` 是 `baz` 的子级时，才覆盖 `foo` ：

```json
{
  "overrides": {
    "baz": {
      "bar": {
        "foo": "1.0.0"
      }
    }
  }
}
```

The key of an override can also include a version, or range of versions. To override `foo` to `1.0.0`, but only when it's a child of `bar@2.0.0`:

​	覆盖的键还可以包含版本或版本范围。要将 `foo` 覆盖为 `1.0.0` ，但仅当它是 `bar@2.0.0` 的子级时：

```json
{
  "overrides": {
    "bar@2.0.0": {
      "foo": "1.0.0"
    }
  }
}
```

You may not set an override for a package that you directly depend on unless both the dependency and the override itself share the exact same spec. To make this limitation easier to deal with, overrides may also be defined as a reference to a spec for a direct dependency by prefixing the name of the package you wish the version to match with a `$`.

​	除非依赖项和覆盖本身具有完全相同的规范，否则您不能为直接依赖项设置覆盖。为了更容易处理此限制，覆盖还可以定义为对直接依赖项规范的引用，方法是在希望匹配版本的软件包名称前缀中添加 `$` 。

```json
{
  "dependencies": {
    "foo": "^1.0.0"
  },
  "overrides": {
    // BAD, will throw an EOVERRIDE error
    // "foo": "^2.0.0"
    // GOOD, specs match so override is allowed
    // "foo": "^1.0.0"
    // BEST, the override is defined as a reference to the dependency
    "foo": "$foo",
    // the referenced package does not need to match the overridden one
    "bar": "$foo"
  }
}
```

### engines

You can specify the version of node that your stuff works on:

​	您可以指定您的代码适用的node版本：

```json
{
  "engines": {
    "node": ">=0.10.3 <15"
  }
}
```

And, like with dependencies, if you don't specify the version (or if you specify "*" as the version), then any version of node will do.

​	与依赖项一样，如果不指定版本（或将版本指定为"*"），则任何版本的node都可以。

You can also use the "engines" field to specify which versions of npm are capable of properly installing your program. For example:

​	您还可以使用"engines"字段指定能够正确安装您的程序的npm的版本。例如：

```json
{
  "engines": {
    "npm": "~1.0.20"
  }
}
```

Unless the user has set the [`engine-strict` config](https://docs.npmjs.com/cli/v10/using-npm/config#engine-strict) flag, this field is advisory only and will only produce warnings when your package is installed as a dependency.

​	除非用户设置了[ `engine-strict` 配置](https://docs.npmjs.com/cli/v10/using-npm/config#engine-strict)标志，否则该字段仅供参考，并且仅在将您的软件包安装为依赖项时产生警告。

### os

You can specify which operating systems your module will run on:

​	您可以指定您的模块将在哪些操作系统上运行：

```json
{
  "os": [
    "darwin",
    "linux"
  ]
}
```

You can also block instead of allowing operating systems, just prepend the blocked os with a '!':

​	您还可以阻止而不是允许操作系统，只需在被阻止的操作系统前加上'!'：

```json
{
  "os": [
    "!win32"
  ]
}
```

The host operating system is determined by `process.platform`

​	主机操作系统由 `process.platform` 确定。

It is allowed to both block and allow an item, although there isn't any good reason to do this.

​	可以同时阻止和允许一个项目，尽管没有任何好的理由这样做。

### cpu

If your code only runs on certain cpu architectures, you can specify which ones.

​	如果您的代码仅在某些CPU架构上运行，可以指定使用哪些架构。

```json
{
  "cpu": [
    "x64",
    "ia32"
  ]
}
```

Like the `os` option, you can also block architectures:

​	与 `os` 选项一样，您还可以阻止架构：

```json
{
  "cpu": [
    "!arm",
    "!mips"
  ]
}
```

The host architecture is determined by `process.arch`

​	主机架构由 `process.arch` 确定。

### private

If you set `"private": true` in your package.json, then npm will refuse to publish it.

​	如果在您的package.json中设置了 `"private": true` ，那么npm将拒绝发布它。

This is a way to prevent accidental publication of private repositories. If you would like to ensure that a given package is only ever published to a specific registry (for example, an internal registry), then use the `publishConfig` dictionary described below to override the `registry` config param at publish-time.

​	这是一种防止私有存储库意外发布的方法。如果您希望确保给定的软件包只发布到特定的注册表（例如内部注册表），那么可以使用下面描述的 `publishConfig` 字典来在发布时覆盖 `registry` 配置参数。

### publishConfig

This is a set of config values that will be used at publish-time. It's especially handy if you want to set the tag, registry or access, so that you can ensure that a given package is not tagged with "latest", published to the global public registry or that a scoped module is private by default.

​	这是一组在发布时使用的配置值。如果您想设置标签、注册表或访问权限，那么这将非常方便，这样您就可以确保给定的软件包不会被标记为"latest"，不会发布到全局公共注册表，或者一个作用域模块默认是私有的。

See [`config`](https://docs.npmjs.com/cli/v10/using-npm/config) to see the list of config options that can be overridden.

​	请参阅[ `config` ](https://docs.npmjs.com/cli/v10/using-npm/config)以查看可以被覆盖的配置选项列表。

### workspaces

The optional `workspaces` field is an array of file patterns that describes locations within the local file system that the install client should look up to find each [workspace](https://docs.npmjs.com/cli/v10/using-npm/workspaces) that needs to be symlinked to the top level `node_modules` folder.

​	可选的 `workspaces` 字段是一个文件模式的数组，描述了安装客户端应该查找的本地文件系统中的位置，以找到需要链接到顶级 `node_modules` 文件夹的每个[workspace](https://docs.npmjs.com/cli/v10/using-npm/workspaces)。

It can describe either the direct paths of the folders to be used as workspaces or it can define globs that will resolve to these same folders.

​	它可以描述要用作工作区的文件夹的直接路径，也可以定义将解析为这些相同文件夹的通配符。

In the following example, all folders located inside the folder `./packages` will be treated as workspaces as long as they have valid `package.json` files inside them:

​	在下面的示例中，只要在文件夹 `./packages` 中有有效的 `package.json` 文件，其中的所有文件夹都将被视为工作区：

```json
{
  "name": "workspace-example",
  "workspaces": [
    "./packages/*"
  ]
}
```

See [`workspaces`](https://docs.npmjs.com/cli/v10/using-npm/workspaces) for more examples.

​	有关更多示例，请参阅[ `workspaces` ](https://docs.npmjs.com/cli/v10/using-npm/workspaces)。

### 默认值 DEFAULT VALUES

npm will default some values based on package contents.

​	npm会根据软件包内容设置一些默认值。

- `"scripts": {"start": "node server.js"}`

  If there is a `server.js` file in the root of your package, then npm will default the `start` command to `node server.js`.

  如果在您的软件包的根目录中有一个 `server.js` 文件，那么npm将默认将 `start` 命令设置为 `node server.js` 。

- `"scripts":{"install": "node-gyp rebuild"}`

  If there is a `binding.gyp` file in the root of your package and you have not defined an `install` or `preinstall` script, npm will default the `install` command to compile using node-gyp.

  如果在您的软件包的根目录中有一个 `binding.gyp` 文件，并且您没有定义 `install` 或 `preinstall` 脚本，npm将默认使用node-gyp进行编译的 `install` 命令。

- `"contributors": [...]`

  If there is an `AUTHORS` file in the root of your package, npm will treat each line as a `Name <email> (url)` format, where email and url are optional. Lines which start with a `#` or are blank, will be ignored.
  
  如果在您的软件包的根目录中有一个 `AUTHORS` 文件，npm将将每行视为 `Name <email> (url)` 格式，其中email和url是可选的。以 `#` 开头或为空的行将被忽略。

### SEE ALSO

- [semver](https://github.com/npm/node-semver#versions)
- [workspaces](https://docs.npmjs.com/cli/v10/using-npm/workspaces)
- [npm init](https://docs.npmjs.com/cli/v10/commands/npm-init)
- [npm version](https://docs.npmjs.com/cli/v10/commands/npm-version)
- [npm config](https://docs.npmjs.com/cli/v10/commands/npm-config)
- [npm help](https://docs.npmjs.com/cli/v10/commands/npm-help)
- [npm install](https://docs.npmjs.com/cli/v10/commands/npm-install)
- [npm publish](https://docs.npmjs.com/cli/v10/commands/npm-publish)
- [npm uninstall](https://docs.npmjs.com/cli/v10/commands/npm-uninstall)
