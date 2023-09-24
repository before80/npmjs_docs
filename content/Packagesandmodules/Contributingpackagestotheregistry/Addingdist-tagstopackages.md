+++
title = "添加分发标签到包"
date = 2023-09-22T20:56:36+08:00
weight = 90
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/adding-dist-tags-to-packages](https://docs.npmjs.com/adding-dist-tags-to-packages)

# Adding dist-tags to packages - 添加分发标签到包

Distribution tags (dist-tags) are human-readable labels that you can use to organize and label different versions of packages you publish. dist-tags supplement [semantic versioning](about-semantic-versioning). In addition to being more human-readable than semantic version numbering, tags allow publishers to distribute their packages more effectively.

​	分发标签（dist-tags）是可读性强的标签，您可以使用它们来组织和标记您发布的不同版本的包。分发标签是对[语义化版本](about-semantic-versioning)的补充。除了比语义化版本号更易读之外，标签还允许发布者更有效地分发他们的包。

For more information, see the [`dist-tag` CLI documentation](https://docs.npmjs.com/cli/dist-tag).

​	有关更多信息，请参阅[ `dist-tag`  CLI 文档](https://docs.npmjs.com/cli/dist-tag)。

**Note:** Since dist-tags share a namespace with semantic versions, avoid dist-tags that conflict with existing version numbers. We recommend avoiding dist-tags that start with a number or the letter "v".

**注意：**由于分发标签与语义化版本共享命名空间，请避免与现有版本号冲突的分发标签。我们建议避免使用以数字或字母“v”开头的分发标签。

## 使用分发标签发布包 Publishing a package with a dist-tag

By default, running `npm publish` will tag your package with the `latest` dist-tag. To use another dist-tag, use the `--tag` flag when publishing.

​	默认情况下，运行  `npm publish`  命令会使用  `latest`  分发标签来标记您的包。要使用其他分发标签，在发布时使用  `--tag`  标志。

1. On the command line, navigate to the root directory of your package.

2. 在命令行中，导航到包的根目录。

   ```
   cd /path/to/package
   ```

3. Run the following command, replacing `<tag>` with the tag you want to use:

4. 运行以下命令，将  `<tag>`  替换为您要使用的标签：

   ```
   npm publish --tag <tag>
   ```

### 示例 Example

To publish a package with the "beta" dist-tag, on the command line, run the following command in the root directory of your package:

​	要使用“beta”分发标签发布一个包，在命令行中，在包的根目录中运行以下命令：

```
npm publish --tag beta
```

## 为特定版本的包添加分发标签 Adding a dist-tag to a specific version of your package

1. On the command line, navigate to the root directory of your package.

2. 在命令行中，导航到包的根目录。

   ```
   cd /path/to/package
   ```

3. Run the following command, replacing `<package_name>` with the name of your package, `<version>` with your package version number, and `<tag>` with the distribution tag:

4. 运行以下命令，将  `<package_name>`  替换为您的包的名称，将  `<version>`  替换为您的包的版本号，将  `<tag>`  替换为分发标签：

   ```
   npm dist-tag add <package-name>@<version> [<tag>]
   ```

### 示例 Example

To add the "stable" tag to the 1.4.0 version of the "example-package" package, you would run the following command:

​	要将“stable”标签添加到版本为 1.4.0 的“example-package”包，您需要运行以下命令：

```
npm dist-tag add example-package@1.4.0 stable
```
