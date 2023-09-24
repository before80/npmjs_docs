+++
title = "关于私有软件包"
date = 2023-09-22T20:54:53+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/about-private-packages](https://docs.npmjs.com/about-private-packages)

# About private packages - 关于私有软件包

To use private packages, you must

​	要使用私有软件包，您必须：

- be using npm version 2.7.0 or greater. To upgrade, on the command line, run

- 使用npm版本2.7.0或更高版本。要升级，请在命令行上运行

  ```highlighter-rouge
  npm install npm@latest -g
  ```
  
- have a [paid user or organization account](https://www.npmjs.com/pricing)

- 拥有[付费用户或组织帐户](https://www.npmjs.com/pricing)

With npm private packages, you can use the npm registry to host code that is only visible to you and chosen collaborators, allowing you to manage and use private code alongside public code in your projects.

​	使用npm私有软件包，您可以使用npm注册表来托管只对您和选择的协作者可见的代码，使您能够在项目中管理和使用私有代码以及公共代码。

Private packages always have a scope, and scoped packages are private by default.

​	私有软件包始终具有作用域，并且具有作用域的软件包默认为私有。

- **User-scoped private packages** can only be accessed by you and collaborators to whom you have granted read or read/write access. For more information, see "[Adding collaborators to private packages owned by a user account](adding-collaborators-to-private-packages-owned-by-a-user-account)".
- **用户作用域的私有软件包**只能由您和您授予读取或读取/写入访问权限的协作者访问。有关更多信息，请参阅“[向用户帐户拥有的私有软件包添加协作者](adding-collaborators-to-private-packages-owned-by-a-user-account)”。
- **Organization-scoped private packages** can only be accessed by teams that have been granted read or read/write access. For more information, see "[Managing team access to organization packages](managing-team-access-to-organization-packages)".
- **组织作用域的私有软件包**只能由被授予读取或读取/写入访问权限的团队访问。有关更多信息，请参阅“[管理团队对组织软件包的访问权限](managing-team-access-to-organization-packages)”。

## 下一步 Next steps

- "[Creating and publishing private packages](creating-and-publishing-private-packages)"
- 创建和发布私有软件包
- "[Using npm packages in your projects](using-npm-packages-in-your-projects)"
- 在您的项目中使用npm软件包

## Resources

<iframe src="https://www.youtube.com/embed/O6JoXGnHK_Y" frameborder="0" allowfullscreen=""></iframe>
