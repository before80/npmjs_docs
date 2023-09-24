+++
title = "创建和发布无作用域的公共软件包"
date = 2023-09-22T20:55:42+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/creating-and-publishing-unscoped-public-packages](https://docs.npmjs.com/creating-and-publishing-unscoped-public-packages)

# Creating and publishing unscoped public packages - 创建和发布无作用域的公共软件包

As an npm user, you can create unscoped packages to use in your own projects and publish them to the npm public registry for others to use in theirs. Unscoped packages are always public and are referred to by the package name only:

​	作为npm用户，您可以创建无作用域的软件包并将其发布到npm公共注册表，供其他人在其项目中使用。无作用域的软件包始终是公开的，并且只通过软件包名称进行引用：

```
package-name
```

For more information on package scope, access, and visibility, see "[Package scope, access level, and visibility](package-scope-access-level-and-visibility)".

​	有关软件包作用域、访问级别和可见性的更多信息，请参阅“[软件包作用域、访问级别和可见性](package-scope-access-level-and-visibility)”。

**Note:** Before you can publish public unscoped npm packages, you must [sign up](https://www.npmjs.com/signup) for an npm user account.

**注意：**在您可以发布公共的无作用域npm软件包之前，您必须先[注册](https://www.npmjs.com/signup)一个npm用户帐户。

## 创建无作用域的公共软件包 Creating an unscoped public package

1. On the command line, create a directory for your package:

2. 在命令行上，创建一个软件包的目录：

   ```
   mkdir my-test-package
   ```

3. Navigate to the root directory of your package:

4. 导航到软件包的根目录：

   ```
   cd my-test-package
   ```

5. If you are using git to manage your package code, in the package root directory, run the following commands, replacing `git-remote-url` with the git remote URL for your package:

6. 如果您使用git来管理软件包代码，请在软件包的根目录中运行以下命令，将 `git-remote-url` 替换为您的软件包的git远程URL：

   ```
   git init
   git remote add origin git://git-remote-url
   ```

7. In the package root directory, run the `npm init` command.

8. 在软件包的根目录中运行 `npm init` 命令。

9. Respond to the prompts to generate a [`package.json`](https://docs.npmjs.com/about-package-json-and-package-lock-json-files) file. For help naming your package, see "[Package name guidelines](package-name-guidelines)".

10. 回答提示以生成[ `package.json` ](https://docs.npmjs.com/about-package-json-and-package-lock-json-files)文件。有关如何命名软件包的帮助，请参阅“[软件包名称准则](package-name-guidelines)”。

11. Create a [README file](about-package-readme-files) that explains what your package code is and how to use it.

12. 创建一个[README文件](about-package-readme-files)，解释您的软件包代码是什么以及如何使用它。

13. In your preferred text editor, write the code for your package.

14. 在您喜欢的文本编辑器中，编写软件包的代码。

## 检查软件包内容是否包含敏感或不必要的信息 Reviewing package contents for sensitive or unnecessary information

Publishing sensitive information to the registry can harm your users, compromise your development infrastructure, be expensive to fix, and put you at risk of legal action. **We strongly recommend removing sensitive information, such as private keys, passwords, [personally identifiable information](https://en.wikipedia.org/wiki/Personally_identifiable_information) (PII), and credit card data before publishing your package to the registry.**

​	向注册表发布敏感信息可能会损害您的用户，危及您的开发基础设施，修复起来代价高昂，并使您面临法律诉讼的风险。**我们强烈建议在将软件包发布到注册表之前，删除敏感信息，例如私钥、密码、[个人身份信息](https://en.wikipedia.org/wiki/Personally_identifiable_information)（PII）和信用卡数据。**

For less sensitive information, such as testing data, use a `.npmignore` or `.gitignore` file to prevent publishing to the registry. For more information, see [this article](https://docs.npmjs.com/misc/developers#keeping-files-out-of-your-package).

​	对于不太敏感的信息，例如测试数据，请使用 `.npmignore` 或 `.gitignore` 文件防止发布到注册表。有关更多信息，请参阅[此文章](https://docs.npmjs.com/misc/developers#keeping-files-out-of-your-package)。

## 测试您的软件包 Testing your package

To reduce the chances of publishing bugs, we recommend testing your package before publishing it to the npm registry. To test your package, run `npm install` with the full path to your package directory:

​	为了减少发布错误的机会，我们建议在将软件包发布到npm注册表之前对其进行测试。要测试软件包，请使用软件包目录的完整路径运行 `npm install` 命令：

```
npm install path/to/my-package
```

## 发布无作用域的公共软件包 Publishing unscoped public packages

1. On the command line, navigate to the root directory of your package.

2. 在命令行上，导航到软件包的根目录。

   ```
   cd /path/to/package
   ```

3. To publish your public package to the npm registry, run:

4. 要将公共软件包发布到npm注册表，请运行：

   ```
   npm publish
   ```

   **Note:** If you use GitHub Actions to publish your packages, you can generate provenance information for each package you publish. For more information, see "[Generating provenance statements](https://docs.npmjs.com/generating-provenance-statements)."

   **注意：**如果您使用GitHub Actions来发布软件包，您可以为您发布的每个软件包生成可信性信息。有关更多信息，请参阅“[生成可信性声明](https://docs.npmjs.com/generating-provenance-statements)”。

5. To see your public package page, visit https://npmjs.com/package/*package-name*, replacing* package-name* with the name of your package. Public packages will say `public` below the package name on the npm website.

6. 要查看您的公共软件包页面，请访问https://npmjs.com/package/*package-name*，将*package-name*替换为您的软件包的名称。在npm网站上，公共软件包的软件包名称下方将显示 `public` 。

For more information on the `publish` command, see the [CLI documentation](https://docs.npmjs.com/cli/publish).

​	有关 `publish` 命令的更多信息，请参阅[CLI文档](https://docs.npmjs.com/cli/publish)。
