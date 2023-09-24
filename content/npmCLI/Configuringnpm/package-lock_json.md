+++
title = "package-lock.json"
date = 2023-09-22T21:23:01+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false
+++

> 原文: [https://docs.npmjs.com/cli/v10/configuring-npm/package-lock-json](https://docs.npmjs.com/cli/v10/configuring-npm/package-lock-json)

# package-lock.json

A manifestation of the manifest

​	清单的体现

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

`package-lock.json` is automatically generated for any operations where npm modifies either the `node_modules` tree, or `package.json`. It describes the exact tree that was generated, such that subsequent installs are able to generate identical trees, regardless of intermediate dependency updates.

​	对于任何 npm 修改  `node_modules`  树或  `package.json`  的操作，都会自动生成  `package-lock.json` 。它描述了生成的确切树，以便后续的安装能够生成相同的树，而不管中间依赖项的更新。

This file is intended to be committed into source repositories, and serves various purposes:

​	此文件旨在提交到源代码库中，具有以下各种用途：

- Describe a single representation of a dependency tree such that teammates, deployments, and continuous integration are guaranteed to install exactly the same dependencies.
- 描述一棵依赖树的单一表示，以确保团队成员、部署和持续集成都能安装完全相同的依赖项。
- Provide a facility for users to "time-travel" to previous states of `node_modules` without having to commit the directory itself.
- 为用户提供“时光旅行”到先前的  `node_modules`  状态的功能，而无需提交目录本身。
- Facilitate greater visibility of tree changes through readable source control diffs.
- 通过可读的源代码控制差异，提供更大的树更改可见性。
- Optimize the installation process by allowing npm to skip repeated metadata resolutions for previously-installed packages.
- 通过允许 npm 跳过先前安装的软件包的重复元数据解析，优化安装过程。
- As of npm v7, lockfiles include enough information to gain a complete picture of the package tree, reducing the need to read `package.json` files, and allowing for significant performance improvements.
- 从 npm v7 开始，锁定文件包含足够的信息来获得完整的包树结构，减少了读取  `package.json`  文件的需求，从而实现了显著的性能改进。

### `package-lock.json` vs `npm-shrinkwrap.json`

Both of these files have the same format, and perform similar functions in the root of a project.

​	这两个文件具有相同的格式，在项目的根目录中执行类似的功能。

The difference is that `package-lock.json` cannot be published, and it will be ignored if found in any place other than the root project.

​	区别在于  `package-lock.json`  不能发布，并且如果在根项目以外的任何位置找到它，它将被忽略。

In contrast, [npm-shrinkwrap.json](https://docs.npmjs.com/cli/v10/configuring-npm/npm-shrinkwrap-json) allows publication, and defines the dependency tree from the point encountered. This is not recommended unless deploying a CLI tool or otherwise using the publication process for producing production packages.

​	相反，[npm-shrinkwrap.json](https://docs.npmjs.com/cli/v10/configuring-npm/npm-shrinkwrap-json) 允许发布，并从遇到的点定义依赖树。除非部署 CLI 工具或以其他方式使用发布过程生成生产软件包，否则不建议使用此功能。

If both `package-lock.json` and `npm-shrinkwrap.json` are present in the root of a project, `npm-shrinkwrap.json` will take precedence and `package-lock.json` will be ignored.

​	如果项目的根目录中同时存在  `package-lock.json`  和  `npm-shrinkwrap.json` ，则  `npm-shrinkwrap.json`  将优先，并且  `package-lock.json`  将被忽略。

### 隐藏的锁定文件 Hidden Lockfiles

In order to avoid processing the `node_modules` folder repeatedly, npm as of v7 uses a "hidden" lockfile present in `node_modules/.package-lock.json`. This contains information about the tree, and is used in lieu of reading the entire `node_modules` hierarchy provided that the following conditions are met:

​	为了避免重复处理  `node_modules`  文件夹，从 npm v7 开始，它使用位于  `node_modules/.package-lock.json`  的“隐藏”锁定文件。它包含有关树的信息，并在读取整个  `node_modules`  层次结构之前使用它，前提是满足以下条件：

- All package folders it references exist in the `node_modules` hierarchy.
- 它引用的所有软件包文件夹都存在于  `node_modules`  层次结构中。
- No package folders exist in the `node_modules` hierarchy that are not listed in the lockfile.
- `node_modules`  层次结构中不存在未在锁定文件中列出的软件包文件夹。
- The modified time of the file is at least as recent as all of the package folders it references.
- 文件的修改时间至少与它引用的所有软件包文件夹的修改时间一样新。

That is, the hidden lockfile will only be relevant if it was created as part of the most recent update to the package tree. If another CLI mutates the tree in any way, this will be detected, and the hidden lockfile will be ignored.

​	也就是说，如果隐藏的锁定文件是作为最近更新软件包树的一部分创建的，它才会相关。如果另一个 CLI 在任何方式上改变了树，这将被检测到，并且将忽略隐藏的锁定文件。

Note that it *is* possible to manually change the *contents* of a package in such a way that the modified time of the package folder is unaffected. For example, if you add a file to `node_modules/foo/lib/bar.js`, then the modified time on `node_modules/foo` will not reflect this change. If you are manually editing files in `node_modules`, it is generally best to delete the file at `node_modules/.package-lock.json`.

​	请注意，您可以手动更改软件包的 *内容*，而不会影响软件包文件夹的修改时间。例如，如果您向  `node_modules/foo/lib/bar.js`  添加一个文件，则  `node_modules/foo`  上的修改时间不会反映此更改。如果您手动编辑  `node_modules`  中的文件，通常最好删除  `node_modules/.package-lock.json`  中的文件。

As the hidden lockfile is ignored by older npm versions, it does not contain the backwards compatibility affordances present in "normal" lockfiles. That is, it is `lockfileVersion: 3`, rather than `lockfileVersion: 2`.

​	由于旧的 npm 版本会忽略隐藏的锁定文件，因此它不包含“正常”锁定文件中存在的向后兼容性。也就是说，它的  `lockfileVersion`  是 3，而不是 2。

### 处理旧的锁定文件 Handling Old Lockfiles

When npm detects a lockfile from npm v6 or before during the package installation process, it is automatically updated to fetch missing information from either the `node_modules` tree or (in the case of empty `node_modules` trees or very old lockfile formats) the npm registry.

​	当 npm 在软件包安装过程中检测到来自 npm v6 或之前的锁定文件时，它会自动更新，从  `node_modules`  树或（在空的  `node_modules`  树或非常旧的锁定文件格式的情况下）npm 注册表中获取缺失的信息。

### 文件格式 File Format

#### `name`

The name of the package this is a package-lock for. This will match what's in `package.json`.

​	这是package-lock的包名称。它与 `package.json` 中的名称相匹配。

#### `version`

The version of the package this is a package-lock for. This will match what's in `package.json`.

​	这是package-lock的包版本。它与 `package.json` 中的版本相匹配。

#### `lockfileVersion`

An integer version, starting at `1` with the version number of this document whose semantics were used when generating this `package-lock.json`.

​	一个整数版本，从 `1` 开始，表示生成此 `package-lock.json` 时使用的文档版本号。

Note that the file format changed significantly in npm v7 to track information that would have otherwise required looking in `node_modules` or the npm registry. Lockfiles generated by npm v7 will contain `lockfileVersion: 2`.

​	请注意，npm v7在文件格式上进行了重大更改，以跟踪否则需要查看 `node_modules` 或npm注册表的信息。由npm v7生成的锁定文件将包含 `lockfileVersion: 2` 。

- No version provided: an "ancient" shrinkwrap file from a version of npm prior to npm v5.
- 没有提供版本：来自npm v5之前版本的“古老”shrinkwrap文件。
- `1`: The lockfile version used by npm v5 and v6.
- `1` ：由npm v5和v6使用的锁定文件版本。
- `2`: The lockfile version used by npm v7 and v8. Backwards compatible to v1 lockfiles.
- `2` ：由npm v7和v8使用的锁定文件版本。向后兼容v1锁定文件。
- `3`: The lockfile version used by npm v9. Backwards compatible to npm v7.
- `3` ：由npm v9使用的锁定文件版本。向后兼容npm v7。

npm will always attempt to get whatever data it can out of a lockfile, even if it is not a version that it was designed to support.

​	npm始终尝试从锁定文件中获取任何可以获得的数据，即使它不是设计用于支持的版本。

#### `packages`

This is an object that maps package locations to an object containing the information about that package.

​	这是一个将包位置映射到包含该包信息的对象。

The root project is typically listed with a key of `""`, and all other packages are listed with their relative paths from the root project folder.

​	根项目通常使用 `""` 作为键进行列出，所有其他包都使用相对于根项目文件夹的路径进行列出。

Package descriptors have the following fields:

​	包描述符具有以下字段：

- version: The version found in `package.json`
- version：在 `package.json` 中找到的版本
- resolved: The place where the package was actually resolved from. In the case of packages fetched from the registry, this will be a url to a tarball. In the case of git dependencies, this will be the full git url with commit sha. In the case of link dependencies, this will be the location of the link target. `registry.npmjs.org` is a magic value meaning "the currently configured registry".
- resolved：实际解析包的位置。对于从注册表获取的包，这将是一个指向tarball的URL。对于git依赖项，这将是带有提交sha的完整git URL。对于链接依赖项，这将是链接目标的位置。 `registry.npmjs.org` 是一个特殊值，表示“当前配置的注册表”。
- integrity: A `sha512` or `sha1` [Standard Subresource Integrity](https://w3c.github.io/webappsec/specs/subresourceintegrity/) string for the artifact that was unpacked in this location.
- integrity：用于此位置解压缩的artifact的 `sha512` 或 `sha1`  [标准子资源完整性](https://w3c.github.io/webappsec/specs/subresourceintegrity/)字符串。
- link: A flag to indicate that this is a symbolic link. If this is present, no other fields are specified, since the link target will also be included in the lockfile.
- link：指示这是一个符号链接的标志。如果存在此标志，则不指定其他字段，因为链接目标也将包含在锁定文件中。
- dev, optional, devOptional: If the package is strictly part of the `devDependencies` tree, then `dev` will be true. If it is strictly part of the `optionalDependencies` tree, then `optional` will be set. If it is both a `dev` dependency *and* an `optional` dependency of a non-dev dependency, then `devOptional` will be set. (An `optional` dependency of a `dev` dependency will have both `dev` and `optional` set.)
- dev、optional、devOptional：如果包严格属于 `devDependencies` 树，则 `dev` 为true。如果它严格属于 `optionalDependencies` 树，则设置 `optional` 。如果它既是 `dev` 依赖项又是非 `dev` 依赖项的 `optional` 依赖项，则设置 `devOptional` 。（ `dev` 依赖项的 `optional` 依赖项将同时设置 `dev` 和 `optional` 。）
- inBundle: A flag to indicate that the package is a bundled dependency.
- inBundle：指示该包是一个捆绑的依赖项的标志。
- hasInstallScript: A flag to indicate that the package has a `preinstall`, `install`, or `postinstall` script.
- hasInstallScript：指示该包是否具有 `preinstall` 、 `install` 或 `postinstall` 脚本的标志。
- hasShrinkwrap: A flag to indicate that the package has an `npm-shrinkwrap.json` file.
- hasShrinkwrap：指示该包是否具有 `npm-shrinkwrap.json` 文件的标志。
- bin, license, engines, dependencies, optionalDependencies: fields from `package.json`
- bin、license、engines、dependencies、optionalDependencies：来自 `package.json` 的字段。

#### dependencies

Legacy data for supporting versions of npm that use `lockfileVersion: 1`. This is a mapping of package names to dependency objects. Because the object structure is strictly hierarchical, symbolic link dependencies are somewhat challenging to represent in some cases.

​	支持使用 `lockfileVersion: 1` 的npm版本的遗留数据。这是一个将包名称映射到依赖项对象的映射。由于对象结构严格层次化，因此在某些情况下，表示符号链接依赖项有一定的挑战性。

npm v7 ignores this section entirely if a `packages` section is present, but does keep it up to date in order to support switching between npm v6 and npm v7.

​	如果存在 `packages` 部分，npm v7将完全忽略此部分，但会保持其最新状态，以支持在npm v6和npm v7之间切换。

Dependency objects have the following fields:

​	依赖项对象具有以下字段：

- version: a specifier that varies depending on the nature of the package, and is usable in fetching a new copy of it.
- version：根据包的性质而变化的指定符，可用于获取其新副本。
  - bundled dependencies: Regardless of source, this is a version number that is purely for informational purposes.
  - 捆绑的依赖项：无论来源如何，这都是仅用于信息目的的版本号。
  - registry sources: This is a version number. (eg, `1.2.3`)
  - 注册表来源：这是一个版本号。（例如， `1.2.3` ）
  - git sources: This is a git specifier with resolved committish. (eg, `git+https://example.com/foo/bar#115311855adb0789a0466714ed48a1499ffea97e`)
  - git来源：这是一个带有已解析提交的git指定符。（例如， `git+https://example.com/foo/bar#115311855adb0789a0466714ed48a1499ffea97e` ）
  - http tarball sources: This is the URL of the tarball. (eg, `https://example.com/example-1.3.0.tgz`)
  - http tarball来源：这是tarball的URL。（例如， `https://example.com/example-1.3.0.tgz` ）
  - local tarball sources: This is the file URL of the tarball. (eg `file:///opt/storage/example-1.3.0.tgz`)
  - 本地tarball来源：这是tarball的文件URL。（例如， `file:///opt/storage/example-1.3.0.tgz` ）
  - local link sources: This is the file URL of the link. (eg `file:libs/our-module`)
  - 本地链接来源：这是链接的文件URL。（例如， `file:libs/our-module` ）
- integrity: A `sha512` or `sha1` [Standard Subresource Integrity](https://w3c.github.io/webappsec/specs/subresourceintegrity/) string for the artifact that was unpacked in this location. For git dependencies, this is the commit sha.
- integrity：用于此位置解压缩的artifact的 `sha512` 或 `sha1`  [标准子资源完整性](https://w3c.github.io/webappsec/specs/subresourceintegrity/)字符串。对于git依赖项，这是提交sha。
- resolved: For registry sources this is path of the tarball relative to the registry URL. If the tarball URL isn't on the same server as the registry URL then this is a complete URL. `registry.npmjs.org` is a magic value meaning "the currently configured registry".
- resolved：对于注册表来源，这是tarball相对于注册表URL的路径。如果tarball URL与注册表URL不在同一个服务器上，则这是一个完整的URL。 `registry.npmjs.org` 是一个特殊值，表示“当前配置的注册表”。
- bundled: If true, this is the bundled dependency and will be installed by the parent module. When installing, this module will be extracted from the parent module during the extract phase, not installed as a separate dependency.
- bundled：如果为true，则表示这是捆绑的依赖项，并将由父模块安装。在安装时，此模块将在提取阶段从父模块中提取，而不是作为单独的依赖项安装。
- dev: If true then this dependency is either a development dependency ONLY of the top level module or a transitive dependency of one. This is false for dependencies that are both a development dependency of the top level and a transitive dependency of a non-development dependency of the top level.
- dev：如果为true，则此依赖项只是顶级模块的开发依赖项，或者是一个的传递依赖项。对于既是顶级的开发依赖项又是非开发依赖项的传递依赖项，此值为false。
- optional: If true then this dependency is either an optional dependency ONLY of the top level module or a transitive dependency of one. This is false for dependencies that are both an optional dependency of the top level and a transitive dependency of a non-optional dependency of the top level.
- optional：如果为true，则此依赖项只是顶级模块的可选依赖项，或者是一个的传递依赖项。对于既是顶级的可选依赖项又是非可选依赖项的传递依赖项，此值为false。
- requires: This is a mapping of module name to version. This is a list of everything this module requires, regardless of where it will be installed. The version should match via normal matching rules a dependency either in our `dependencies` or in a level higher than us.
- requires：这是一个模块名称到版本的映射。这是我们需要的所有模块的列表，无论它们将在何处安装。版本应该通过正常匹配规则与我们的 `dependencies` 或高于我们的级别中的依赖项匹配。
- dependencies: The dependencies of this dependency, exactly as at the top level.
- dependencies：此依赖项的依赖项，与顶级相同。

### See also

- [npm shrinkwrap](https://docs.npmjs.com/cli/v10/commands/npm-shrinkwrap)
- [npm-shrinkwrap.json](https://docs.npmjs.com/cli/v10/configuring-npm/npm-shrinkwrap-json)
- [package.json](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)
- [npm install](https://docs.npmjs.com/cli/v10/commands/npm-install)
