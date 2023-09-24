+++
title = "创建 Node.js 模块"
date = 2023-09-22T20:55:24+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/creating-node-js-modules](https://docs.npmjs.com/creating-node-js-modules)

# Creating Node.js modules - 创建 Node.js 模块

Node.js modules are a type of [package](about-packages-and-modules) that can be published to npm.

​	Node.js 模块是一种可以发布到 npm 的[包](about-packages-and-modules)。

## 创建  `package.json`  文件 Create a `package.json` file

1. To create a `package.json` file, on the command line, in the root directory of your Node.js module, run `npm init`:

2. 要创建一个`package.json`文件，请在命令行中，在您的 Node.js 模块的根目录中运行`npm init`命令：
   - For [scoped modules](about-scopes), run `npm init --scope=@scope-name`
   - 对于[作用域模块](about-scopes)，运行  `npm init --scope=@scope-name` 
   - For [unscoped modules](creating-and-publishing-unscoped-public-packages), run `npm init`
   - 对于[非作用域模块](creating-and-publishing-unscoped-public-packages)，运行  `npm init` 

3. Provide responses for the required fields (`name`and `version`), as well as the `main` field:

4. 为所需字段（`name`和`version`）以及`main`字段提供响应：
   - `name`: The name of your module.
   - `name` ：您的模块的名称。
   - `version`: The initial module version. We recommend following [semantic versioning guidelines](about-semantic-versioning) and starting with `1.0.0`.
   - `version` ：初始模块版本。我们建议遵循[语义化版本指南](about-semantic-versioning)，并从  `1.0.0`  开始。


For more information on `package.json` files, see "[Creating a package.json file](creating-a-package-json-file)".

​	有关  `package.json`  文件的更多信息，请参阅“[创建 package.json 文件](creating-a-package-json-file)”。

## 创建在其他应用程序中加载您的模块时将被加载的文件 Create the file that will be loaded when your module is required by another application

In the file, add a function as a property of the `exports` object. This will make the function available to other code:

​	在该文件中，将一个函数作为  `exports`  对象的属性添加进去。这将使该函数对其他代码可用：

```
exports.printMsg = function() {
  console.log("This is a message from the demo package");
}
```

## 测试您的模块 Test your module

1. Publish your package to npm:

2. 将您的包发布到 npm：

   - For [private packages](creating-and-publishing-private-packages#publishing-private-packages) and [unscoped packages](creating-and-publishing-unscoped-public-packages#publishing-unscoped-public-packages), use `npm publish`.
   - 对于[私有包](creating-and-publishing-private-packages#publishing-private-packages)和[非作用域公共包](creating-and-publishing-unscoped-public-packages#publishing-unscoped-public-packages)，使用  `npm publish` 。
   - For [scoped public packages](creating-and-publishing-scoped-public-packages#publishing-scoped-public-packages), use `npm publish --access public`
   - 对于[作用域公共包](creating-and-publishing-scoped-public-packages#publishing-scoped-public-packages)，使用  `npm publish --access public` 。

3. On the command line, create a new test directory outside of your project directory.

4. 在命令行中，在项目目录之外创建一个新的测试目录。

   ```
   mkdir test-directory
   ```

5. Switch to the new directory:

6. 切换到新目录：

   ```
   cd /path/to/test-directory
   ```

7. In the test directory, install your module:

8. 在测试目录中，安装您的模块：

   ```
   npm install <your-module-name>
   ```

9. In the test directory, create a `test.js` file which requires your module and calls your module as a method.

10. 在测试目录中，创建一个  `test.js`  文件，该文件要求您的模块，并将您的模块作为方法进行调用。

11. On the command line, run `node test.js`. The message sent to the console.log should appear.

12. 在命令行中，运行  `node test.js` 。控制台打印的消息应该会显示出来。

## 资源 Resources

<iframe src="https://www.youtube.com/embed/3I78ELjTzlQ" frameborder="0" allowfullscreen=""></iframe>
