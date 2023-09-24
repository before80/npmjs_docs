+++
title = "开发者"
date = 2023-09-22T21:24:51+08:00
weight = 90
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/cli/v10/using-npm/developers](https://docs.npmjs.com/cli/v10/using-npm/developers)

# developers - 开发者

Developer Guide

​	开发者指南

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

So, you've decided to use npm to develop (and maybe publish/deploy) your project.

​	所以，您决定使用npm来开发（可能还发布/部署）您的项目。

Fantastic!

​	太棒了！

There are a few things that you need to do above the simple steps that your users will do to install your program.

​	除了用户安装程序的简单步骤外，您还需要做一些事情。

### 关于这些文档 About These Documents

These are man pages. If you install npm, you should be able to then do `man npm-thing` to get the documentation on a particular topic, or `npm help thing` to see the same information.

​	这些是man页面。如果您安装了npm，您应该能够使用 `man npm-thing` 来获取有关特定主题的文档，或者使用 `npm help thing` 查看相同的信息。

### 什么是包 What is a Package

A package is:

​	一个包是：

- a) a folder containing a program described by a package.json file
- a）包含由package.json文件描述的程序的文件夹
- b) a gzipped tarball containing (a)
- b）包含（a）的gzip压缩tarball
- c) a url that resolves to (b)
- c）解析为（b）的url
- d) a `<name>@<version>` that is published on the registry with (c)
- d）以（c）发布到注册表的 `<name>@<version>` 
- e) a `<name>@<tag>` that points to (d)
- e）指向（d）的 `<name>@<tag>` 
- f) a `<name>` that has a "latest" tag satisfying (e)
- f）具有满足（e）的“最新”标签的 `<name>` 
- g) a `git` url that, when cloned, results in (a).
- g）克隆时结果为（a）的 `git`  url。

Even if you never publish your package, you can still get a lot of benefits of using npm if you just want to write a node program (a), and perhaps if you also want to be able to easily install it elsewhere after packing it up into a tarball (b).

​	即使您从不发布您的软件包，如果您只想编写一个节点程序（a），并且也许您还希望能够将其打包成tarball（b）后轻松地在其他地方安装，那么您仍然可以从使用npm中获得很多好处。

Git urls can be of the form:

​	Git url可以是以下形式之一：

```bash
git://github.com/user/project.git#commit-ish
git+ssh://user@hostname:project.git#commit-ish
git+http://user@hostname/project/blah.git#commit-ish
git+https://user@hostname/project/blah.git#commit-ish
```

The `commit-ish` can be any tag, sha, or branch which can be supplied as an argument to `git checkout`. The default is whatever the repository uses as its default branch.

​	`commit-ish` 可以是任何可以作为参数提供给 `git checkout` 的标签、sha或分支。默认值是存储库使用的默认分支。

### package.json文件 The package.json File

You need to have a `package.json` file in the root of your project to do much of anything with npm. That is basically the whole interface.

​	您需要在项目的根目录中有一个 `package.json` 文件才能使用npm做任何事情。这基本上是整个接口。

See [`package.json`](https://docs.npmjs.com/cli/v10/configuring-npm/package-json) for details about what goes in that file. At the very least, you need:

​	有关在该文件中放入什么的详细信息，请参阅[ `package.json` ](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)。至少，您需要：

- name: This should be a string that identifies your project. Please do not use the name to specify that it runs on node, or is in JavaScript. You can use the "engines" field to explicitly state the versions of node (or whatever else) that your program requires, and it's pretty well assumed that it's JavaScript.

- name：这应该是一个标识您的项目的字符串。请不要使用名称来指定其在node上运行或是JavaScript的事实。您可以使用“engines”字段来明确说明您的程序所需的node（或其他内容）的版本，而且它基本上被认为是JavaScript。

  It does not necessarily need to match your github repository name.

  它不一定需要与您的github存储库名称匹配。

  So, `node-foo` and `bar-js` are bad names. `foo` or `bar` are better.

  因此， `node-foo` 和 `bar-js` 是不好的名称。 `foo` 或 `bar` 更好。

- version: A semver-compatible version.

- version：符合语义化版本的版本。

- engines: Specify the versions of node (or whatever else) that your program runs on. The node API changes a lot, and there may be bugs or new functionality that you depend on. Be explicit.

- engines：指定您的程序运行的node（或其他内容）的版本。node API经常发生变化，可能存在您依赖的错误或新功能。要明确。

- author: Take some credit.

- author：给自己一些信用。

- scripts: If you have a special compilation or installation script, then you should put it in the `scripts` object. You should definitely have at least a basic smoke-test command as the "scripts.test" field. See [scripts](https://docs.npmjs.com/cli/v10/using-npm/scripts).

- scripts：如果您有特殊的编译或安装脚本，那么您应该将其放在 `scripts` 对象中。您至少应该有一个基本的烟雾测试命令作为“scripts.test”字段。请参阅[scripts](https://docs.npmjs.com/cli/v10/using-npm/scripts)。

- main: If you have a single module that serves as the entry point to your program (like what the "foo" package gives you at require("foo")), then you need to specify that in the "main" field.

- main：如果您有一个单独的模块作为程序的入口点（就像“foo”包在require（"foo"）中给您的那样），那么您需要在“main”字段中指定它。

- directories: This is an object mapping names to folders. The best ones to include are "lib" and "doc", but if you use "man" to specify a folder full of man pages, they'll get installed just like these ones.

- directories：这是一个将名称映射到文件夹的对象。最好包括“lib”和“doc”，但是如果您使用“man”指定一个包含man页面的文件夹，它们将像这些一样被安装。

You can use `npm init` in the root of your package in order to get you started with a pretty basic package.json file. See [`npm init`](https://docs.npmjs.com/cli/v10/commands/npm-init) for more info.

​	您可以在软件包的根目录中使用 `npm init` 来开始使用一个相当基本的package.json文件。有关更多信息，请参阅[ `npm init` ](https://docs.npmjs.com/cli/v10/commands/npm-init)。

### 将文件排除在包外 Keeping files *out* of your Package

Use a `.npmignore` file to keep stuff out of your package. If there's no `.npmignore` file, but there *is* a `.gitignore` file, then npm will ignore the stuff matched by the `.gitignore` file. If you *want* to include something that is excluded by your `.gitignore` file, you can create an empty `.npmignore` file to override it. Like `git`, `npm` looks for `.npmignore` and `.gitignore` files in all subdirectories of your package, not only the root directory.

​	使用 `.npmignore` 文件将内容排除在包外。如果没有 `.npmignore` 文件，但是有 `.gitignore` 文件，那么npm将忽略与 `.gitignore` 文件匹配的内容。如果您希望包含被 `.gitignore` 文件排除的内容，可以创建一个空的 `.npmignore` 文件来覆盖它。与 `git` 一样， `npm` 在您的软件包的所有子目录中寻找 `.npmignore` 和 `.gitignore` 文件，而不仅仅是根目录。

`.npmignore` files follow the [same pattern rules](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_ignoring) as `.gitignore` files:

 	`.npmignore` 文件遵循与 `.gitignore` 文件相同的[模式规则](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_ignoring)：

- Blank lines or lines starting with `#` are ignored.
- 空行或以 `＃` 开头的行将被忽略。
- Standard glob patterns work.
- 标准的glob模式有效。
- You can end patterns with a forward slash `/` to specify a directory.
- 您可以在模式的末尾添加斜杠 `/` 来指定一个目录。
- You can negate a pattern by starting it with an exclamation point `!`.
- 您可以通过以感叹号 `!` 开头来否定一个模式。

By default, the following paths and files are ignored, so there's no need to add them to `.npmignore` explicitly:

​	默认情况下，以下路径和文件将被忽略，因此不需要将它们明确添加到 `.npmignore` 中：

- `.*.swp`
- `._*`
- `.DS_Store`
- `.git`
- `.gitignore`
- `.hg`
- `.npmignore`
- `.npmrc`
- `.lock-wscript`
- `.svn`
- `.wafpickle-*`
- `config.gypi`
- `CVS`
- `npm-debug.log`

Additionally, everything in `node_modules` is ignored, except for bundled dependencies. npm automatically handles this for you, so don't bother adding `node_modules` to `.npmignore`.

​	此外，除捆绑的依赖项之外， `node_modules` 中的所有内容都将被忽略。npm会自动为您处理，所以不要费心将 `node_modules` 添加到 `.npmignore` 中。

The following paths and files are never ignored, so adding them to `.npmignore` is pointless:

​	以下路径和文件永远不会被忽略，因此将它们添加到 `.npmignore` 是没有意义的：

- `package.json`
- `README` (and its variants)
- `README` （及其变体）
- `CHANGELOG` (and its variants)
- `CHANGELOG` （及其变体）
- `LICENSE` / `LICENCE`

If, given the structure of your project, you find `.npmignore` to be a maintenance headache, you might instead try populating the `files` property of `package.json`, which is an array of file or directory names that should be included in your package. Sometimes manually picking which items to allow is easier to manage than building a block list.

​	如果考虑到项目的结构，您发现 `.npmignore` 是一个维护上的麻烦，您可以尝试填充 `package.json` 的 `files` 属性，它是一个包含应包含在软件包中的文件或目录名称的数组。有时手动选择允许的项目比构建块列表更容易管理。

#### 测试 `.npmignore` 或 `files` 配置是否有效 Testing whether your `.npmignore` or `files` config works

If you want to double check that your package will include only the files you intend it to when published, you can run the `npm pack` command locally which will generate a tarball in the working directory, the same way it does for publishing.

​	如果您想要在发布时仅包含您打算的文件，可以在本地运行 `npm pack` 命令，它将在工作目录中生成一个tarball，就像发布一样。

### 链接软件包 Link Packages

`npm link` is designed to install a development package and see the changes in real time without having to keep re-installing it. (You do need to either re-link or `npm rebuild -g` to update compiled packages, of course.)

​	 `npm link` 旨在安装开发软件包，并实时查看更改，无需反复安装它（当然，您需要重新链接或 `npm rebuild -g` 以更新编译的软件包）。

More info at [`npm link`](https://docs.npmjs.com/cli/v10/commands/npm-link).

​	更多信息请参阅[ `npm link` ](https://docs.npmjs.com/cli/v10/commands/npm-link)。

### 发布之前：确保您的软件包安装并正常工作 Before Publishing: Make Sure Your Package Installs and Works

**This is important.**

​	**这很重要。**

If you can not install it locally, you'll have problems trying to publish it. Or, worse yet, you'll be able to publish it, but you'll be publishing a broken or pointless package. So don't do that.

​	如果您无法在本地安装它，您在尝试发布它时将会遇到问题。或者，更糟糕的是，您将能够发布它，但您将发布一个损坏或无意义的软件包。所以不要这样做。

In the root of your package, do this:

​	在您的软件包的根目录中，执行以下操作：

```bash
npm install . -g
```

That'll show you that it's working. If you'd rather just create a symlink package that points to your working directory, then do this:

​	这将显示它正在工作。如果您更愿意只创建一个指向您的工作目录的符号链接软件包，那么执行以下操作：

```bash
npm link
```

Use `npm ls -g` to see if it's there.

​	使用 `npm ls -g` 查看它是否存在。

To test a local install, go into some other folder, and then do:

​	要测试本地安装，请进入其他某个文件夹，然后执行：

```bash
cd ../some-other-folder
npm install ../my-package
```

to install it locally into the node_modules folder in that other place.

将其本地安装到该其他位置的node_modules文件夹中。

Then go into the node-repl, and try using require("my-thing") to bring in your module's main module.

​	然后进入node-repl，尝试使用require（"my-thing"）来引入您模块的主模块。

### 创建用户帐户 Create a User Account

Create a user with the adduser command. It works like this:

​	使用adduser命令创建用户。操作如下：

```bash
npm adduser
```

and then follow the prompts.

然后按照提示进行操作。

This is documented better in [npm adduser](https://docs.npmjs.com/cli/v10/commands/npm-adduser).

​	更详细的文档可以参考[npm adduser](https://docs.npmjs.com/cli/v10/commands/npm-adduser)。

### 发布你的软件包 Publish your Package

This part's easy. In the root of your folder, do this:

​	这部分很简单。在你的项目根目录下，执行以下命令：

```bash
npm publish
```

You can give publish a url to a tarball, or a filename of a tarball, or a path to a folder.

​	你可以给publish命令提供一个tarball的URL、文件名或者文件夹路径。

Note that pretty much **everything in that folder will be exposed** by default. So, if you have secret stuff in there, use a `.npmignore` file to list out the globs to ignore, or publish from a fresh checkout.

请注意，默认情况下，**该文件夹中的几乎所有内容都会被公开**。所以，如果你的文件夹中有秘密文件，请使用 `.npmignore` 文件列出要忽略的文件，或者从一个干净的副本中进行发布。

### 炫耀一下 Brag about it

Send emails, write blogs, blab in IRC.

​	发送电子邮件，写博客，在IRC上大肆宣传。

Tell the world how easy it is to install your program!

​	告诉世界安装你的程序有多么简单！

### See also

- [npm](https://docs.npmjs.com/cli/v10/commands/npm)
- [npm init](https://docs.npmjs.com/cli/v10/commands/npm-init)
- [package.json](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)
- [npm scripts](https://docs.npmjs.com/cli/v10/using-npm/scripts)
- [npm publish](https://docs.npmjs.com/cli/v10/commands/npm-publish)
- [npm adduser](https://docs.npmjs.com/cli/v10/commands/npm-adduser)
- [npm registry](https://docs.npmjs.com/cli/v10/using-npm/registry)
