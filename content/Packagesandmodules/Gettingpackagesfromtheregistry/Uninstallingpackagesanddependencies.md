+++
title = "卸载包和依赖项"
date = 2023-09-22T20:59:01+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/uninstalling-packages-and-dependencies](https://docs.npmjs.com/uninstalling-packages-and-dependencies)

# Uninstalling packages and dependencies - 卸载包和依赖项

If you no longer need to use a package in your code, we recommend uninstalling it and removing it from your project's dependencies.

​	如果您不再需要在代码中使用某个包，我们建议卸载它并从项目的依赖项中删除它。

## 卸载本地包 Uninstalling local packages

### 从 node_modules 目录中删除本地包 Removing a local package from your node_modules directory

To remove a package from your node_modules directory, on the command line, use the [`uninstall` command](https://docs.npmjs.com/cli/uninstall). Include the scope if the package is scoped.

​	要从 node_modules 目录中删除包，请在命令行中使用 [ `uninstall`  命令](https://docs.npmjs.com/cli/uninstall)。如果包是作用域包，请包含作用域。

This uninstalls a package, completely removing everything npm installed on its behalf.

​	这将卸载一个包，完全删除 npm 为其安装的所有内容。

It also removes the package from the dependencies, devDependencies, optionalDependencies, and peerDependencies objects in your package.json.

​	它还会从 package.json 中的 dependencies、devDependencies、optionalDependencies 和 peerDependencies 对象中删除该包。

Further, if you have an npm-shrinkwrap.json or package-lock.json, npm will update those files as well.

​	此外，如果您有一个 npm-shrinkwrap.json 或 package-lock.json 文件，npm 也会更新这些文件。

#### 非作用域包 Unscoped package

```
npm uninstall <package_name>
```

#### 作用域包 Scoped package

```
npm uninstall <@scope/package_name>
```

### 示例 Example

```
npm uninstall lodash
```

### 卸载本地包而不从 package.json 中删除它 Removing a local package without removing it from package.json

Using the `--no-save` will tell npm not to remove the package from your `package.json`, `npm-shrinkwrap.json`, or `package-lock.json` files.

​	使用  `--no-save`  选项将告诉 npm 不要从您的  `package.json` 、 `npm-shrinkwrap.json`  或  `package-lock.json`  文件中删除该包。

### 示例 Example

```
npm uninstall --no-save lodash
```

`--save` or `-S` will tell npm to remove the package from your `package.json`, `npm-shrinkwrap.json`, and `package-lock.json` files. **This is the default**, but you may need to use this if you have for instance `save=false` in your `.npmrc` file.

​	`--save`  或  `-S`  选项将告诉 npm 从您的  `package.json` 、 `npm-shrinkwrap.json`  和  `package-lock.json`  文件中删除该包。**这是默认行为**，但如果您在  `.npmrc`  文件中例如设置了  `save=false` ，则可能需要使用此选项。

### 确认本地包卸载 Confirming local package uninstallation

To confirm that `npm uninstall` worked correctly, check that the `node_modules` directory no longer contains a directory for the uninstalled package(s).

​	要确认  `npm uninstall`  是否正常工作，请检查  `node_modules`  目录是否不再包含已卸载包的目录。

- Unix system (such as OSX): `ls node_modules`
- Unix 系统（如 OSX）： `ls node_modules` 
- Windows systems: `dir node_modules`
- Windows 系统： `dir node_modules` 

## 卸载全局包 Uninstalling global packages

To uninstall an unscoped global package, on the command line, use the `uninstall` command with the `-g` flag. Include the scope if the package is scoped.

​	要卸载非作用域全局包，请在命令行中使用  `uninstall`  命令和  `-g`  标志。如果包是作用域包，请包含作用域。

### 非作用域包 Unscoped package

```
npm uninstall -g <package_name>
```

### 作用域包 Scoped package

```
npm uninstall -g <@scope/package_name>
```

### 示例 Example

For example, to uninstall a package called `jshint`, run:

​	例如，要卸载名为  `jshint`  的包，请运行：

```
npm uninstall -g jshint
```

## 资源 Resources

### 卸载本地包 Uninstalling local packages

<iframe src="https://www.youtube.com/embed/Z-BpYj6cSoQ" frameborder="0" allowfullscreen=""></iframe>

### 卸载全局包 Uninstalling global packages

<iframe src="https://www.youtube.com/embed/XbvjZxUZJGg" frameborder="0" allowfullscreen=""></iframe>
