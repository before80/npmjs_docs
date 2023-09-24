+++
title = "更新已发布软件包的版本号"
date = 2023-09-22T20:57:18+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/updating-your-published-package-version-number](https://docs.npmjs.com/updating-your-published-package-version-number)

# Updating your published package version number - 更新已发布软件包的版本号

When you make significant changes to a published package, we recommend updating the version number to communicate the extent of the changes to others who rely on your code.

​	当您对已发布的软件包进行重大更改时，我们建议更新版本号，以向依赖您代码的其他人传达更改的程度。

**Note:** If you have linked a git repository to a package, updating the package version number will also add a tag with the updated release number to the linked git repository.

**注意：**如果您将git仓库链接到软件包，更新软件包版本号还将向链接的git仓库添加一个带有更新的发布号的标签。

1. To change the version number in `package.json`, on the command line, in the package root directory, run the following command, replacing `<update_type>` with one of the [semantic versioning](about-semantic-versioning) release types (patch, major, or minor):

2. 要在 `package.json` 中更改版本号，请在命令行上，在软件包根目录中运行以下命令，将 `<update_type>` 替换为[语义化版本](about-semantic-versioning)发布类型之一（补丁、主要或次要）：

   ```
   npm version <update_type>
   ```

3. Run `npm publish`.

4. 运行 `npm publish` 。

5. Go to your package page (`https://npmjs.com/package/<package>`) to check that the package version has been updated.

6. 转到您的软件包页面（ `https://npmjs.com/package/<package>` ）检查软件包版本是否已更新。

For more information on `npm version`, see the [CLI documentation](https://docs.npmjs.com/cli/version).

​	有关 `npm version` 的更多信息，请参阅[CLI文档](https://docs.npmjs.com/cli/version)。
