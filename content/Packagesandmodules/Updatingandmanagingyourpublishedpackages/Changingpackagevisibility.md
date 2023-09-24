+++
title = "更改软件包可见性"
date = 2023-09-22T20:56:59+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/changing-package-visibility](https://docs.npmjs.com/changing-package-visibility)

# Changing package visibility - 更改软件包可见性

You can change the visibility of a scoped package from the website or command line.

​	您可以从网站或命令行界面更改作用域软件包的可见性。

You must be the owner of the user account or organization that owns the package in order to change package visibility.

​	要更改软件包的可见性，您必须是拥有该软件包的用户帐户或组织的所有者。

For more information about package visibility, see "[Package scope, access level, and visibility](package-scope-access-level-and-visibility)".

​	有关软件包可见性的更多信息，请参阅“[软件包作用域、访问级别和可见性](package-scope-access-level-and-visibility)”。

**Note:** You cannot change the visibility of an unscoped package. Only scoped packages with a paid subscription may be private.

**注意：**您无法更改非作用域软件包的可见性。只有具有付费订阅的作用域软件包可以是私有的。

## 将公共软件包更改为私有 Making a public package private

**Note:** Making a package private requires a paid user account or organization. To sign up for a paid user or organization, go to `https://www.npmjs.com/settings/account-name/billing`, replacing `account-name` with the name of your npm user account or organization.

**注意：**将软件包更改为私有需要付费的用户帐户或组织。要注册付费用户或组织，请转到 `https://www.npmjs.com/settings/account-name/billing` ，将 `account-name` 替换为您的npm用户帐户或组织的名称。

If you want to restrict access and visibility for a public package you own, you can make the package private. When you make a package private, its access will be updated immediately and it will be removed from the website within a few minutes of the change.

​	如果您想限制您拥有的公共软件包的访问和可见性，您可以将该软件包更改为私有。当您将软件包更改为私有时，它的访问权限将立即更新，并且在更改后的几分钟内将从网站中删除。

### 使用网站 Using the website

1. On the [npm website](https://npmjs.com), go to the package page.
2. 在[npm网站](https://npmjs.com)上，转到软件包页面。
3. On the package page, click **Settings**.
4. 在软件包页面上，点击**Settings**。
5. Under "Package Access", select "Is Package Private?"
6. 在“Package Access”下，选择“Is Package Private?”。
7. Click **Update package settings**.
8. 点击**Update package settings**。

### 使用命令行 Using the command line

To make a public package private on the command line, run the following command, replacing `<package-name>` with the name of your package:

​	要在命令行上将公共软件包更改为私有，运行以下命令，将 `<package-name>` 替换为您的软件包名称：

```
npm access restricted <package-name>
```

For more information, see the [`npm access`](https://docs.npmjs.com/cli-documentation/access) documentation.

​	有关更多信息，请参阅[ `npm access` ](https://docs.npmjs.com/cli-documentation/access)文档。

## 将私有软件包更改为公共 Making a private package public

Note: When you make a private package public, the package will be visible to and downloadable by all npm users.

注意：将私有软件包更改为公共后，所有npm用户都可以看到和下载该软件包。

### 使用网站 Using the website

1. On the npm website, go to the package page.
2. 在npm网站上，转到软件包页面。
3. On the package page, click **Settings**.
4. 在软件包页面上，点击**Settings**。
5. Under "Package Access", deselect "Is Package Private?"
6. 在“Package Access”下，取消选择“Is Package Private?”。
7. Click **Update package settings**.
8. 点击**Update package settings**。

### 使用命令行 Using the command line

To make a private package public on the command line, run the following command, replacing `<package-name>` with the name of your package:

​	要在命令行上将私有软件包更改为公共，运行以下命令，将 `<package-name>` 替换为您的软件包名称：

```
npm access public <package-name>
```

For more information, see the [`npm access` CLI documentation](https://docs.npmjs.com/cli/access).

​	有关更多信息，请参阅[ `npm access`  CLI文档](https://docs.npmjs.com/cli/access)。
