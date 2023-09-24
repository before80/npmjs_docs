+++
title = "在项目中使用npm软件包"
date = 2023-09-22T20:58:43+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/using-npm-packages-in-your-projects](https://docs.npmjs.com/using-npm-packages-in-your-projects)

# Using npm packages in your projects - 在项目中使用npm软件包

Once you have [installed a package](downloading-and-installing-packages) in `node_modules`, you can use it in your code.

​	一旦您在 `node_modules` 中[安装了一个软件包](downloading-and-installing-packages)，您就可以在代码中使用它。

## 在项目中使用无作用域的软件包 Using unscoped packages in your projects

### Node.js模块 Node.js module

If you are creating a Node.js module, you can use a package in your module by passing it as an argument to the `require` function.

​	如果您正在创建一个Node.js模块，可以通过将软件包作为参数传递给 `require` 函数来在模块中使用软件包。

```javascript
var lodash = require('lodash');

var output = lodash.without([1, 2, 3], 1);
console.log(output);
```

### package.json文件 package.json file

In `package.json`, list the package under dependencies. You can optionally include a [semantic version](about-semantic-versioning).

​	在 `package.json` 中，将软件包列在依赖项下。您可以选择包含一个[语义版本](about-semantic-versioning)。

```json
{
  "dependencies": {
    "package_name": "^1.0.0"
  }
}
```

## 在项目中使用作用域的软件包 Using scoped packages in your projects

To use a scoped package, simply include the scope wherever you use the package name.

​	要使用作用域软件包，只需在使用软件包名称的任何位置包含作用域。

### Node.js模块 Node.js module

```js
var projectName = require("@scope/package-name")
```

### package.json文件 package.json file

In `package.json`:

​	在 `package.json` 中：

```json
{
  "dependencies": {
    "@scope/package_name": "^1.0.0"
  }
}
```

## 解决“找不到模块”错误 Resolving "Cannot find module" errors

If you have not properly installed a package, you will receive an error when you try to use it in your code. For example, if you reference the `lodash` package without installing it, you would see the following error:

​	如果您没有正确安装一个软件包，在尝试在代码中使用它时，您将收到一个错误。例如，如果您在没有安装lodash的情况下引用它，您将看到以下错误：

```
module.js:340
    throw err;
          ^
Error: Cannot find module 'lodash'
```

- For scoped packages, run `npm install <@scope/package_name>`
- 对于作用域软件包，请运行 `npm install <@scope/package_name>` 
- For unscoped packages, run `npm install <package_name>`
- 对于无作用域的软件包，请运行 `npm install <package_name>`
