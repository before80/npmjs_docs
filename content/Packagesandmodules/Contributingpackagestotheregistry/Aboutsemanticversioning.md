+++
title = "关于语义化版本控制"
date = 2023-09-22T20:56:24+08:00
weight = 80
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/about-semantic-versioning](https://docs.npmjs.com/about-semantic-versioning)

# About semantic versioning - 关于语义化版本控制

To keep the JavaScript ecosystem healthy, reliable, and secure, every time you make significant updates to an npm package you own, we recommend publishing a new version of the package with an updated version number in the [`package.json` file](creating-a-package-json-file) that follows the [semantic versioning spec](http://semver.org/). Following the semantic versioning spec helps other developers who depend on your code understand the extent of changes in a given version, and adjust their own code if necessary.

​	为了保持 JavaScript 生态系统的健康、可靠和安全，每当您对自己拥有的 npm 包进行重大更新时，我们建议在 [ `package.json`  文件](creating-a-package-json-file)中发布一个带有更新版本号的新版本包，遵循[语义化版本规范](http://semver.org/)。遵循语义化版本规范有助于依赖于您代码的其他开发人员了解给定版本中的变化程度，并在必要时调整自己的代码。

Note: If you introduce a change that breaks a package dependency, we strongly recommend incrementing the version major number; see below for details.

注意：如果您引入了破坏包依赖关系的更改，我们强烈建议增加主版本号；详见下文。

## 增加已发布包的语义化版本号 Incrementing semantic versions in published packages

To help developers who rely on your code, we recommend starting your package version at `1.0.0` and incrementing as follows:

​	为了帮助依赖于您代码的开发人员，我们建议从  `1.0.0`  开始，并按照以下方式递增包版本：

| 代码状态             | 阶段     | 规则                                       | 示例版本 |
| -------------------- | -------- | ------------------------------------------ | -------- |
| 首次发布             | 新产品   | 从 1.0.0 开始                              | 1.0.0    |
| 向后兼容的错误修复   | 补丁发布 | 递增第三位数字                             | 1.0.1    |
| 向后兼容的新功能     | 次要发布 | 递增中间位数字，将最后一位重置为零         | 1.1.0    |
| 破坏向后兼容性的更改 | 主要发布 | 递增第一位数字，将中间位和最后一位重置为零 | 2.0.0    |

| Code status                               | Stage         | Rule                                                         | Example version |
| ----------------------------------------- | ------------- | ------------------------------------------------------------ | --------------- |
| First release                             | New product   | Start with 1.0.0                                             | 1.0.0           |
| Backward compatible bug fixes             | Patch release | Increment the third digit                                    | 1.0.1           |
| Backward compatible new features          | Minor release | Increment the middle digit and reset last digit to zero      | 1.1.0           |
| Changes that break backward compatibility | Major release | Increment the first digit and reset middle and last digits to zero | 2.0.0           |

## 使用语义化版本控制指定包可以接受的更新类型 Using semantic versioning to specify update types your package can accept

You can specify which update types your package can accept from dependencies in your package's `package.json` file.

​	您可以在包的  `package.json`  文件中指定包可以接受的依赖项的更新类型。

For example, to specify acceptable version ranges up to 1.0.4, use the following syntax:

​	例如，要指定可接受的版本范围为 1.0.4，使用以下语法：

- Patch releases: `1.0` or `1.0.x` or `~1.0.4`
- 补丁发布： `1.0`  或  `1.0.x`  或  `~1.0.4` 
- Minor releases: `1` or `1.x` or `^1.0.4`
- 次要发布： `1`  或  `1.x`  或  `^1.0.4` 
- Major releases: `*` or `x`
- 主要发布： `*`  或  `x` 

For more information on semantic versioning syntax, see the [npm semver calculator](https://semver.npmjs.com/).

​	有关语义化版本控制语法的更多信息，请参阅 [npm 语义化版本计算器](https://semver.npmjs.com/)。

### 示例 Example



```json
"dependencies": {
  "my_dep": "^1.0.0",
  "another_dep": "~2.2.0"
},
```

## 资源 Resources

<iframe src="https://www.youtube.com/embed/kK4Meix58R4" frameborder="0" allowfullscreen=""></iframe>
