+++
title = "文件夹"
date = 2023-09-22T21:22:16+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/cli/v10/configuring-npm/folders](https://docs.npmjs.com/cli/v10/configuring-npm/folders)

# folders - 文件夹

Folder Structures Used by npm

npm使用的文件夹结构

Select CLI Version:Version 10.0.0 (Latest Release)

选择CLI版本：版本10.0.0（最新版本）

### 描述 Description

npm puts various things on your computer. That's its job.

​	npm将各种内容放在您的计算机上。这是它的工作。

This document will tell you what it puts where.

​	本文档将告诉您它将这些内容放在哪里。

#### tl;dr

- Local install (default): puts stuff in `./node_modules` of the current package root.
- 本地安装（默认）：将内容放在当前软件包根目录的 `./node_modules` 中。
- Global install (with `-g`): puts stuff in /usr/local or wherever node is installed.
- 全局安装（使用 `-g` ）：将内容放在/usr/local或node安装的任何其他位置。
- Install it **locally** if you're going to `require()` it.
- 如果您要使用 `require()` 加载它，请将其**本地**安装。
- Install it **globally** if you're going to run it on the command line.
- 如果您要在命令行上运行它，请将其**全局**安装。
- If you need both, then install it in both places, or use `npm link`.
- 如果您两者都需要，请在两个位置安装它，或者使用 `npm link` 。

#### 前缀配置 prefix Configuration

The [`prefix` config](https://docs.npmjs.com/cli/v10/using-npm/config#prefix) defaults to the location where node is installed. On most systems, this is `/usr/local`. On Windows, it's `%AppData%\npm`. On Unix systems, it's one level up, since node is typically installed at `{prefix}/bin/node` rather than `{prefix}/node.exe`.

​	[ `前缀` 配置](https://docs.npmjs.com/cli/v10/using-npm/config#prefix)默认为node安装的位置。在大多数系统上，这是 `/usr/local` 。在Windows上，它是 `%AppData%\npm` 。在Unix系统上，它在一级目录上，因为通常将node安装在 `{prefix}/bin/node` 而不是 `{prefix}/node.exe` 。

When the `global` flag is set, npm installs things into this prefix. When it is not set, it uses the root of the current package, or the current working directory if not in a package already.

​	当设置了 `global` 标志时，npm将内容安装到此前缀中。当未设置时，它使用当前软件包的根目录，或者如果尚未在软件包中，则使用当前工作目录。

#### Node模块 Node Modules

Packages are dropped into the `node_modules` folder under the `prefix`. When installing locally, this means that you can `require("packagename")` to load its main module, or `require("packagename/lib/path/to/sub/module")` to load other modules.

​	软件包被放置在前缀下的 `node_modules` 文件夹中。在本地安装时，这意味着您可以使用 `require("packagename")` 来加载其主要模块，或者使用 `require("packagename/lib/path/to/sub/module")` 来加载其他模块。

Global installs on Unix systems go to `{prefix}/lib/node_modules`. Global installs on Windows go to `{prefix}/node_modules` (that is, no `lib` folder.)

​	Unix系统上的全局安装放在 `{prefix}/lib/node_modules` 中。Windows上的全局安装放在 `{prefix}/node_modules` 中（即没有 `lib` 文件夹）。

Scoped packages are installed the same way, except they are grouped together in a sub-folder of the relevant `node_modules` folder with the name of that scope prefix by the @ symbol, e.g. `npm install @myorg/package` would place the package in `{prefix}/node_modules/@myorg/package`. See [`scope`](https://docs.npmjs.com/cli/v10/using-npm/scope) for more details.

​	作用域包的安装方式与此相同，只是它们在相关的 `node_modules` 文件夹的子文件夹中以该作用域前缀的名称分组，前缀由@符号表示，例如 `npm install @myorg/package` 会将软件包放置在 `{prefix}/node_modules/@myorg/package` 中。有关更多详细信息，请参阅[ `scope` ](https://docs.npmjs.com/cli/v10/using-npm/scope)。

If you wish to `require()` a package, then install it locally.

​	如果您希望使用 `require()` 加载软件包，请将其本地安装。

#### 可执行文件 Executables

When in global mode, executables are linked into `{prefix}/bin` on Unix, or directly into `{prefix}` on Windows. Ensure that path is in your terminal's `PATH` environment to run them.

​	在全局模式下，可执行文件链接到Unix的 `{prefix}/bin` 目录，或直接链接到Windows的 `{prefix}` 目录。确保该路径在您的终端的 `PATH` 环境变量中以便运行它们。

When in local mode, executables are linked into `./node_modules/.bin` so that they can be made available to scripts run through npm. (For example, so that a test runner will be in the path when you run `npm test`.)

​	在本地模式下，可执行文件链接到 `./node_modules/.bin` 中，以便在通过npm运行的脚本中可以使用它们（例如，在运行 `npm test` 时，测试运行程序将在路径中）。

#### 手册页 Man Pages

When in global mode, man pages are linked into `{prefix}/share/man`.

​	在全局模式下，手册页链接到 `{prefix}/share/man` 。

When in local mode, man pages are not installed.

​	在本地模式下，不安装手册页。

Man pages are not installed on Windows systems.

​	Windows系统上不安装手册页。

#### 缓存 Cache

See [`npm cache`](https://docs.npmjs.com/cli/v10/commands/npm-cache). Cache files are stored in `~/.npm` on Posix, or `%LocalAppData%/npm-cache` on Windows.

​	请参阅[ `npm cache` ](https://docs.npmjs.com/cli/v10/commands/npm-cache)。缓存文件存储在Posix上的 `~/.npm` 中，或者在Windows上的 `%LocalAppData%/npm-cache` 中。

This is controlled by the [`cache` config](https://docs.npmjs.com/cli/v10/using-npm/config#cache) param.

​	这由[ `cache` 配置](https://docs.npmjs.com/cli/v10/using-npm/config#cache)参数控制。

#### 临时文件 Temp Files

Temporary files are stored by default in the folder specified by the [`tmp` config](https://docs.npmjs.com/cli/v10/using-npm/config#tmp), which defaults to the TMPDIR, TMP, or TEMP environment variables, or `/tmp` on Unix and `c:\windows\temp` on Windows.

​	默认情况下，临时文件存储在由[ `tmp` 配置](https://docs.npmjs.com/cli/v10/using-npm/config#tmp)指定的文件夹中，它默认为TMPDIR、TMP或TEMP环境变量，或者在Unix上为/tmp，在Windows上为c:\windows\temp。

Temp files are given a unique folder under this root for each run of the program, and are deleted upon successful exit.

​	每次运行程序时，临时文件都会在此根目录下获得一个唯一的文件夹，并在成功退出时删除。

### 更多信息 More Information

When installing locally, npm first tries to find an appropriate `prefix` folder. This is so that `npm install foo@1.2.3` will install to the sensible root of your package, even if you happen to have `cd`ed into some other folder.

​	在本地安装时，npm首先尝试找到一个合适的 `前缀` 文件夹。这样，即使您恰好进入其他文件夹， `npm install foo@1.2.3` 也会安装到您软件包的合理根目录。

Starting at the $PWD, npm will walk up the folder tree checking for a folder that contains either a `package.json` file, or a `node_modules` folder. If such a thing is found, then that is treated as the effective "current directory" for the purpose of running npm commands. (This behavior is inspired by and similar to git's .git-folder seeking logic when running git commands in a working dir.)

​	从 `$PWD` 开始，npm将沿着文件夹树向上查找，检查是否存在包含 `package.json` 文件或 `node_modules` 文件夹的文件夹。如果找到这样的内容，则将其视为运行npm命令的有效“当前目录”。（此行为受到git在工作目录中运行git命令时寻找 `.git` 文件夹的逻辑启发和类似。）

If no package root is found, then the current folder is used.

​	如果找不到软件包根目录，则使用当前文件夹。

When you run `npm install foo@1.2.3`, then the package is loaded into the cache, and then unpacked into `./node_modules/foo`. Then, any of foo's dependencies are similarly unpacked into `./node_modules/foo/node_modules/...`.

​	当您运行 `npm install foo@1.2.3` 时，软件包将加载到缓存中，然后解压到 `./node_modules/foo` 中。然后，foo的任何依赖项也会以类似的方式解压到 `./node_modules/foo/node_modules/...` 中。

Any bin files are symlinked to `./node_modules/.bin/`, so that they may be found by npm scripts when necessary.

​	任何bin文件都会在 `./node_modules/.bin/` 中创建符号链接，以便在需要时可以通过npm脚本找到它们。

#### 全局安装 Global Installation

If the [`global` config](https://docs.npmjs.com/cli/v10/using-npm/config#global) is set to true, then npm will install packages "globally".

​	如果将[ `global` 配置](https://docs.npmjs.com/cli/v10/using-npm/config#global)设置为true，则npm将“全局”安装软件包。

For global installation, packages are installed roughly the same way, but using the folders described above.

​	对于全局安装，软件包的安装方式与上述描述的文件夹相同。

#### 循环、冲突和文件夹紧凑性 Cycles, Conflicts, and Folder Parsimony

Cycles are handled using the property of node's module system that it walks up the directories looking for `node_modules` folders. So, at every stage, if a package is already installed in an ancestor `node_modules` folder, then it is not installed at the current location.

​	循环是通过node模块系统的属性处理的，该属性在查找 `node_modules` 文件夹时向上遍历目录。因此，在每个阶段，如果软件包已经安装在祖先 `node_modules` 文件夹中，则不会在当前位置安装它。

Consider the case above, where `foo -> bar -> baz`. Imagine if, in addition to that, baz depended on bar, so you'd have: `foo -> bar -> baz -> bar -> baz ...`. However, since the folder structure is: `foo/node_modules/bar/node_modules/baz`, there's no need to put another copy of bar into `.../baz/node_modules`, since when baz calls `require("bar")`, it will get the copy that is installed in `foo/node_modules/bar`.

​	考虑上面的情况，其中 `foo -> bar -> baz` 。假设除此之外，baz还依赖于bar，因此您将得到： `foo -> bar -> baz -> bar -> baz ...` 。然而，由于文件夹结构是： `foo/node_modules/bar/node_modules/baz` ，所以无需将另一个副本的bar放入 `.../baz/node_modules` 中，因为当baz调用 `require("bar")` 时，它将获得安装在 `foo/node_modules/bar` 中的副本。

This shortcut is only used if the exact same version would be installed in multiple nested `node_modules` folders. It is still possible to have `a/node_modules/b/node_modules/a` if the two "a" packages are different versions. However, without repeating the exact same package multiple times, an infinite regress will always be prevented.

​	只有在多个嵌套的 `node_modules` 文件夹中将安装完全相同的版本时，才使用此快捷方式。如果两个“a”软件包的版本不同，仍然可以有 `a/node_modules/b/node_modules/a` 。然而，如果不重复安装完全相同的软件包多次，将始终防止无限回归。

Another optimization can be made by installing dependencies at the highest level possible, below the localized "target" folder (hoisting). Since version 3, npm hoists dependencies by default.

​	通过在尽可能高的级别下，在本地化的“目标”文件夹下安装依赖项，可以进行另一个优化（hoisting）。自版本3以来，默认情况下，npm通过hoisting来安装依赖项。

#### 示例 Example

Consider this dependency graph:

​	考虑以下依赖关系图：

```bash
foo
+-- blerg@1.2.5
+-- bar@1.2.3
|   +-- blerg@1.x (latest=1.3.7)
|   +-- baz@2.x
|   |   `-- quux@3.x
|   |       `-- bar@1.2.3 (cycle)
|   `-- asdf@*
`-- baz@1.2.3
    `-- quux@3.x
        `-- bar
```

In this case, we might expect a folder structure like this (with all dependencies hoisted to the highest level possible):

​	在这种情况下，我们可能期望的文件夹结构如下（将所有依赖项提升到可能的最高级别）：

```bash
foo
+-- node_modules
    +-- blerg (1.2.5) <---[A]
    +-- bar (1.2.3) <---[B]
    |   +-- node_modules
    |       +-- baz (2.0.2) <---[C]
    +-- asdf (2.3.4)
    +-- baz (1.2.3) <---[D]
    +-- quux (3.2.0) <---[E]
```

Since foo depends directly on `bar@1.2.3` and `baz@1.2.3`, those are installed in foo's `node_modules` folder.

​	由于foo直接依赖于 `bar@1.2.3` 和 `baz@1.2.3` ，因此它们安装在foo的 `node_modules` 文件夹中。

Even though the latest copy of blerg is 1.3.7, foo has a specific dependency on version 1.2.5. So, that gets installed at [A]. Since the parent installation of blerg satisfies bar's dependency on `blerg@1.x`, it does not install another copy under [B].

​	即使最新版本的blerg是1.3.7，foo对版本1.2.5有特定的依赖关系。因此，它会安装在[A]处。由于blerg的父级安装满足bar对 `blerg@1.x` 的依赖关系，因此它不会在[B]下安装另一个副本。

Bar [B] also has dependencies on baz and asdf. Because it depends on `baz@2.x`, it cannot re-use the `baz@1.2.3` installed in the parent `node_modules` folder [D], and must install its own copy [C]. In order to minimize duplication, npm hoists dependencies to the top level by default, so asdf is installed under [A].

​	Bar [B]还依赖于baz和asdf。因为它依赖于 `baz@2.x` ，所以不能重用在父级 `node_modules` 文件夹[D]中安装的 `baz@1.2.3` ，必须安装自己的副本[C]。为了最小化重复，npm默认情况下将依赖项提升到顶级，因此asdf在[A]下安装。

Underneath bar, the `baz -> quux -> bar` dependency creates a cycle. However, because bar is already in quux's ancestry [B], it does not unpack another copy of bar into that folder. Likewise, quux's [E] folder tree is empty, because its dependency on bar is satisfied by the parent folder copy installed at [B].

​	在bar下面， `baz -> quux -> bar` 的依赖关系创建了一个循环。然而，因为bar已经在quux的祖先[B]中，所以它不会在该文件夹中解压另一个bar的副本。同样，quux的[E]文件夹树为空，因为它对bar的依赖关系已经被安装在[B]处的父文件夹中。

For a graphical breakdown of what is installed where, use `npm ls`.

​	要查看安装在哪里的详细图形，请使用 `npm ls` 。

#### 发布 Publishing

Upon publishing, npm will look in the `node_modules` folder. If any of the items there are not in the `bundleDependencies` array, then they will not be included in the package tarball.

​	发布时，npm将查看 `node_modules` 文件夹。如果其中的任何项不在 `bundleDependencies` 数组中，则不会包含在软件包tarball中。

This allows a package maintainer to install all of their dependencies (and dev dependencies) locally, but only re-publish those items that cannot be found elsewhere. See [`package.json`](https://docs.npmjs.com/cli/v10/configuring-npm/package-json) for more information.

​	这允许软件包维护人员在本地安装所有依赖项（和开发依赖项），但仅重新发布无法在其他地方找到的那些项。有关更多信息，请参阅[ `package.json` ](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)。

### 另请参阅 See also

- [package.json](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)
- [npm install](https://docs.npmjs.com/cli/v10/commands/npm-install)
- [npm pack](https://docs.npmjs.com/cli/v10/commands/npm-pack)
- [npm cache](https://docs.npmjs.com/cli/v10/commands/npm-cache)
- [npm config](https://docs.npmjs.com/cli/v10/commands/npm-config)
- [npmrc](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc)
- [config](https://docs.npmjs.com/cli/v10/using-npm/config)
- [npm publish](https://docs.npmjs.com/cli/v10/commands/npm-publish)
