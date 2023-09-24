+++
title = "作用域"
date = 2023-09-22T21:23:57+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/cli/v10/using-npm/scope](https://docs.npmjs.com/cli/v10/using-npm/scope)

# scope - 作用域

Scoped packages

作用域包

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

All npm packages have a name. Some package names also have a scope. A scope follows the usual rules for package names (URL-safe characters, no leading dots or underscores). When used in package names, scopes are preceded by an `@` symbol and followed by a slash, e.g.

​	所有npm包都有一个名称。一些软件包名称还具有作用域。作用域遵循软件包名称的常规规则（URL安全字符，不带前导点或下划线）。在软件包名称中使用作用域时，作用域前面有一个 `@` 符号，后面跟着一个斜杠，例如

```bash
@somescope/somepackagename
```

Scopes are a way of grouping related packages together, and also affect a few things about the way npm treats the package.

​	作用域是将相关软件包分组的一种方式，并且还会影响npm处理软件包的几个方面。

Each npm user/organization has their own scope, and only you can add packages in your scope. This means you don't have to worry about someone taking your package name ahead of you. Thus it is also a good way to signal official packages for organizations.

​	每个npm用户/组织都有自己的作用域，只有您可以在自己的作用域中添加软件包。这意味着您无需担心其他人在您之前使用您的软件包名称。因此，这也是为组织提供官方软件包的好方法。

Scoped packages can be published and installed as of `npm@2` and are supported by the primary npm registry. Unscoped packages can depend on scoped packages and vice versa. The npm client is backwards-compatible with unscoped registries, so it can be used to work with scoped and unscoped registries at the same time.

​	从 `npm@2` 开始，可以发布和安装作用域软件包，并且由主要的npm注册表支持。非作用域软件包可以依赖于作用域软件包，反之亦然。npm客户端与非作用域注册表兼容，因此可以同时使用作用域和非作用域注册表。

### 安装作用域软件包 Installing scoped packages

Scoped packages are installed to a sub-folder of the regular installation folder, e.g. if your other packages are installed in `node_modules/packagename`, scoped modules will be installed in `node_modules/@myorg/packagename`. The scope folder (`@myorg`) is simply the name of the scope preceded by an `@` symbol, and can contain any number of scoped packages.

​	作用域软件包安装到常规安装文件夹的子文件夹中，例如，如果您的其他软件包安装在 `node_modules/packagename` 中，则作用域模块将安装在 `node_modules/@myorg/packagename` 中。作用域文件夹（ `@myorg` ）只是作用域名称前面带有 `@` 符号的名称，并且可以包含任意数量的作用域软件包。

A scoped package is installed by referencing it by name, preceded by an `@` symbol, in `npm install`:

​	通过在 `npm install` 中引用名称之前加上 `@` 符号来安装作用域软件包：

```bash
npm install @myorg/mypackage
```

Or in `package.json`:

​	或者在 `package.json` 中：

```json
"dependencies": {
  "@myorg/mypackage": "^1.3.0"
}
```

Note that if the `@` symbol is omitted, in either case, npm will instead attempt to install from GitHub; see [`npm install`](https://docs.npmjs.com/cli/v10/commands/npm-install).

​	请注意，如果在任一情况下省略了 `@` 符号，npm将尝试从GitHub安装；参见[ `npm install` ](https://docs.npmjs.com/cli/v10/commands/npm-install)。

### 引用作用域软件包 Requiring scoped packages

Because scoped packages are installed into a scope folder, you have to include the name of the scope when requiring them in your code, e.g.

​	由于作用域软件包安装到作用域文件夹中，因此在代码中引用它们时必须包含作用域的名称，例如

```javascript
require('@myorg/mypackage')
```

There is nothing special about the way Node treats scope folders. This simply requires the `mypackage` module in the folder named `@myorg`.

​	Node处理作用域文件夹没有特殊之处。这只是在名为 `@myorg` 的文件夹中需要 `mypackage` 模块。

### 发布作用域软件包 Publishing scoped packages

Scoped packages can be published from the CLI as of `npm@2` and can be published to any registry that supports them, including the primary npm registry.

​	从 `npm@2` 开始，可以从CLI发布作用域软件包，并且可以发布到支持它们的任何注册表，包括主要的npm注册表。

(As of 2015-04-19, and with npm 2.0 or better, the primary npm registry **does** support scoped packages.)

（截至2015-04-19，并且使用npm 2.0或更高版本，主要的npm注册表**支持**作用域软件包。）

If you wish, you may associate a scope with a registry; see below.

​	如果希望，可以将作用域与注册表关联；请参阅下文。

#### 将公共作用域软件包发布到主要的npm注册表 Publishing public scoped packages to the primary npm registry

Publishing to a scope, you have two options:

​	在作用域上发布时，有两个选项：

- Publishing to your user scope (example: `@username/module`)
- 发布到用户作用域（例如： `@username/module` ）
- Publishing to an organization scope (example: `@org/module`)
- 发布到组织作用域（例如： `@org/module` ）

If publishing a public module to an organization scope, you must first either create an organization with the name of the scope that you'd like to publish to or be added to an existing organization with the appropriate permissions. For example, if you'd like to publish to `@org`, you would need to create the `org` organization on npmjs.com prior to trying to publish.

​	如果要将公共模块发布到组织作用域，请首先创建一个具有要发布到的作用域名称的组织，或者被添加到具有适当权限的现有组织中。例如，如果您要发布到 `@org` ，则需要在发布之前在npmjs.com上创建名为 `org` 的组织。

Scoped packages are not public by default. You will need to specify `--access public` with the initial `npm publish` command. This will publish the package and set access to `public` as if you had run `npm access public` after publishing. You do not need to do this when publishing new versions of an existing scoped package.

​	作用域软件包默认不是公共的。您需要在初始的 `npm publish` 命令中指定 `--access public` 。这将发布软件包并将访问权限设置为 `public` ，就好像在发布后运行了 `npm access public` 一样。在发布现有作用域软件包的新版本时，您不需要这样做。

#### 将私有作用域软件包发布到npm注册表 Publishing private scoped packages to the npm registry

To publish a private scoped package to the npm registry, you must have an [npm Private Modules](https://docs.npmjs.com/private-modules/intro) account.

​	要将私有作用域软件包发布到npm注册表，您必须拥有[npm私有模块](https://docs.npmjs.com/private-modules/intro)帐户。

You can then publish the module with `npm publish` or `npm publish --access restricted`, and it will be present in the npm registry, with restricted access. You can then change the access permissions, if desired, with `npm access` or on the npmjs.com website.

​	然后，您可以使用 `npm publish` 或 `npm publish --access restricted` 发布模块，它将存在于npm注册表中，并具有受限制的访问权限。然后，如果需要，可以使用 `npm access` 或npmjs.com网站更改访问权限。

### 将作用域与注册表关联 Associating a scope with a registry

Scopes can be associated with a separate registry. This allows you to seamlessly use a mix of packages from the primary npm registry and one or more private registries, such as [GitHub Packages](https://github.com/features/packages) or the open source [Verdaccio](https://verdaccio.org) project.

​	作用域可以与单独的注册表关联。这使您可以无缝地使用来自主要npm注册表和一个或多个私有注册表（例如[GitHub Packages](https://github.com/features/packages)或开源项目[Verdaccio](https://verdaccio.org)）的软件包混合使用。

You can associate a scope with a registry at login, e.g.

​	可以在登录时将作用域与注册表关联，例如

```bash
npm login --registry=http://reg.example.com --scope=@myco
```

Scopes have a many-to-one relationship with registries: one registry can host multiple scopes, but a scope only ever points to one registry.

​	作用域与注册表具有多对一的关系：一个注册表可以托管多个作用域，但一个作用域始终只指向一个注册表。

You can also associate a scope with a registry using `npm config`:

​	也可以使用 `npm config` 将作用域与注册表关联：

```bash
npm config set @myco:registry http://reg.example.com
```

Once a scope is associated with a registry, any `npm install` for a package with that scope will request packages from that registry instead. Any `npm publish` for a package name that contains the scope will be published to that registry instead.

​	一旦作用域与注册表关联，任何具有该作用域的软件包的 `npm install` 都将从该注册表请求软件包。任何包含作用域的软件包名称的 `npm publish` 都将发布到该注册表。

### See also

- [npm install](https://docs.npmjs.com/cli/v10/commands/npm-install)
- [npm publish](https://docs.npmjs.com/cli/v10/commands/npm-publish)
- [npm access](https://docs.npmjs.com/cli/v10/commands/npm-access)
- [npm registry](https://docs.npmjs.com/cli/v10/using-npm/registry)
