+++
title = "关于软件包的README文件"
date = 2023-09-22T20:55:33+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/about-package-readme-files](https://docs.npmjs.com/about-package-readme-files)

# About package README files - 关于软件包的README文件

To help others find your packages on npm and have a good experience using your code in their projects, we recommend including a README file in your package directory. Your README file may include directions for installing, configuring, and using the code in your package, as well as any other information a user may find helpful. The README file will be shown on the package page.

​	为了帮助其他人在npm上找到您的软件包，并在他们的项目中良好地使用您的代码，我们建议在您的软件包目录中包含一个README文件。您的README文件可以包括有关安装、配置和使用软件包中的代码的说明，以及用户可能会发现有帮助的任何其他信息。README文件将显示在软件包页面上。

An npm package README file must be in the root-level directory of the package.

​	npm软件包的README文件必须位于软件包的根级目录中。

## 创建并添加README.md文件到软件包 Creating and adding a README.md file to a package

1. In a text editor, in your package root directory, create a file called `README.md`.
2. 在文本编辑器中，在软件包根目录中创建一个名为 `README.md` 的文件。
3. In the `README.md` file, add useful information about your package.
4. 在 `README.md` 文件中添加有关您的软件包的有用信息。
5. Save the `README.md` file.
6. 保存 `README.md` 文件。

**Note:** The file extension `.md` indicates a Markdown file. For more information about Markdown, see the GitHub Guide "[Mastering Markdown](https://guides.github.com/features/mastering-markdown/#what)".

**注意：**文件扩展名 `.md` 表示Markdown文件。有关Markdown的更多信息，请参阅GitHub指南“[掌握Markdown](https://guides.github.com/features/mastering-markdown/#what)”。

## 更新现有软件包的README文件 Updating an existing package README file

The README file will only be updated on the package page when you publish a new version of your package. To update your README file:

​	只有在发布软件包的新版本时，README文件才会在软件包页面上更新。要更新您的README文件：

1. In a text editor, update the contents of the `README.md` file.

2. 在文本编辑器中，更新 `README.md` 文件的内容。

3. Save the `README.md` file.

4. 保存 `README.md` 文件。

5. On the command line, in the package root directory, run the following commands:

6. 在命令行中，进入软件包的根目录，运行以下命令：

   ```
   npm version patch
   npm publish
   ```
