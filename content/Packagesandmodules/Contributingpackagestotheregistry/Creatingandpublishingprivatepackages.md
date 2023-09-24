+++
title = "创建和发布私有包"
date = 2023-09-22T20:55:59+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/creating-and-publishing-private-packages](https://docs.npmjs.com/creating-and-publishing-private-packages)

# Creating and publishing private packages - 创建和发布私有包

To share your code with a limited set of users or teams, you can publish private user-scoped or organization-scoped packages to the npm registry.

​	要与一组有限的用户或团队共享代码，您可以将私有的用户范围或组织范围的包发布到 npm 注册表。

For more information on scopes and private packages, see "[About scopes](about-scopes)" and "[About private packages](about-private-packages)".

​	有关作用域和私有包的更多信息，请参阅“[关于作用域](about-scopes)”和“[关于私有包](about-private-packages)”。

**Note:** Before you can publish private user-scoped npm packages, you must [sign up](https://npmjs.com/signup) for a paid npm user account.

**注意：**在您可以发布私有的用户范围的 npm 包之前，您必须[注册](https://npmjs.com/signup)一个付费的 npm 用户账户。

Additionally, to publish private organization-scoped packages, you must [create an npm user account](https://npmjs.com/signup), then [create a paid npm organization](https://www.npmjs.com/signup?next=/org/create).

​	此外，要发布私有的组织范围的包，您必须[创建一个 npm 用户账户](https://npmjs.com/signup)，然后[创建一个付费的 npm 组织](https://www.npmjs.com/signup?next=/org/create)。

## 创建私有包 Creating a private package

1. If you are using npmrc to [manage accounts on multiple registries](configuring-your-registry-settings-as-an-npm-enterprise-user#using-npmrc-to-manage-multiple-profiles-for-different-registries), on the command line, switch to the appropriate profile:

2. 如果您使用 npmrc 来[管理多个注册表上的账户](configuring-your-registry-settings-as-an-npm-enterprise-user#using-npmrc-to-manage-multiple-profiles-for-different-registries)，请在命令行中切换到适当的配置文件：

   ```
   npmrc <profile-name>
   ```

3. On the command line, create a directory for your package:

4. 在命令行中，创建一个目录用于您的包：

   ```
   mkdir my-test-package
   ```

5. Navigate to the root directory of your package:

6. 导航到您的包的根目录：

   ```
   cd my-test-package
   ```

7. If you are using git to manage your package code, in the package root directory, run the following commands, replacing `git-remote-url` with the git remote URL for your package:

8. 如果您使用 git 来管理包代码，在包的根目录中运行以下命令，将  `git-remote-url`  替换为您的包的 git 远程 URL：

   ```
   git init
   git remote add origin git://git-remote-url
   ```

9. In the package root directory, run the `npm init` command and pass the scope to the `scope` flag:

10. 在包的根目录中，运行  `npm init`  命令，并通过  `scope`  标志传递作用域：

   - For an organization-scoped package, replace `my-org` with the name of your organization:

   - 对于组织范围的包，请将  `my-org`  替换为您的组织名称：

     ```
     npm init --scope=@my-org
     ```
     
   - For a user-scoped package, replace `my-username` with your username:

   - 对于用户范围的包，请将  `my-username`  替换为您的用户名：

     ```
     npm init --scope=@my-username
     ```

11. Respond to the prompts to generate a [`package.json`](https://docs.npmjs.com/about-package-json-and-package-lock-json-files) file. For help naming your package, see "[Package name guidelines](package-name-guidelines)".

12. 回答提示以生成 [ `package.json` ](https://docs.npmjs.com/about-package-json-and-package-lock-json-files) 文件。有关如何命名您的包的帮助，请参阅“[包名称指南](package-name-guidelines)”。

13. Create a [README file](about-package-readme-files) that explains what your package code is and how to use it.

14. 创建一个[README 文件](about-package-readme-files)，解释您的包代码是什么以及如何使用它。

15. In your preferred text editor, write the code for your package.

16. 使用您喜欢的文本编辑器，编写您的包的代码。

## 检查包内容是否包含敏感或不必要的信息 Reviewing package contents for sensitive or unnecessary information

Publishing sensitive information to the registry can harm your users, compromise your development infrastructure, be expensive to fix, and put you at risk of legal action. **We strongly recommend removing sensitive information, such as private keys, passwords, [personally identifiable information](https://en.wikipedia.org/wiki/Personally_identifiable_information) (PII), and credit card data before publishing your package to the registry.** Even if your package is private, sensitive information can be exposed if the package is made public or downloaded to a computer that can be accessed by more users than intended.

​	将敏感信息发布到注册表可能会损害您的用户，危害您的开发基础设施，修复起来可能很昂贵，并使您面临法律诉讼的风险。**我们强烈建议在将包发布到注册表之前，删除敏感信息，例如私钥、密码、[个人身份信息](https://en.wikipedia.org/wiki/Personally_identifiable_information)（PII）和信用卡数据。**即使您的包是私有的，如果该包被公开或下载到比预期更多的用户可以访问的计算机上，敏感信息也可能会被暴露。

For less sensitive information, such as testing data, use a `.npmignore` or `.gitignore` file to prevent publishing to the registry. For more information, see [this article](https://docs.npmjs.com/misc/developers#keeping-files-out-of-your-package).

​	对于不太敏感的信息，例如测试数据，请使用  `.npmignore`  或  `.gitignore`  文件防止将其发布到注册表。有关更多信息，请参阅[此文章](https://docs.npmjs.com/misc/developers#keeping-files-out-of-your-package)。

## 测试您的包 Testing your package

To reduce the chances of publishing bugs, we recommend testing your package before publishing it to the npm registry. To test your package, run `npm install` with the full path to your package directory:

​	为了减少发布错误的可能性，我们建议在将包发布到 npm 注册表之前进行测试。要测试您的包，请使用完整路径运行  `npm install`  命令，指定您的包目录：

```
npm install my-package
```

## 发布私有包 Publishing private packages

By default, scoped packages are published with private visibility.

​	默认情况下，作用域包以私有可见性进行发布。

1. On the command line, navigate to the root directory of your package.

2. 在命令行中，导航到包的根目录。

   ```
   cd /path/to/package
   ```

3. To publish your private package to the npm registry, run:

4. 要将私有包发布到 npm 注册表，请运行：

   ```
   npm publish
   ```

5. To see your private package page, visit https://npmjs.com/package/*package-name*, replacing* package-name* with the name of your package. Private packages will say `private` below the package name on the npm website.

6. 要查看您的私有包页面，请访问 https://npmjs.com/package/*package-name*，将 *package-name* 替换为您的包的名称。私有包在 npm 网站上的包名下方会显示  `private` 。

   ![Screenshot of a private npm Teams package](https://docs.npmjs.com/shared/organization-package-private.png)

For more information on the `publish` command, see the [CLI documentation](https://docs.npmjs.com/cli/publish).

​	有关  `publish`  命令的更多信息，请参阅[CLI 文档](https://docs.npmjs.com/cli/publish)。
