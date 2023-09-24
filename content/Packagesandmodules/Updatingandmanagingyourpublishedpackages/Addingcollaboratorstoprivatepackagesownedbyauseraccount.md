+++
title = "将协作者添加到用户帐户拥有的私有软件包中"
date = 2023-09-22T20:57:09+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/adding-collaborators-to-private-packages-owned-by-a-user-account](https://docs.npmjs.com/adding-collaborators-to-private-packages-owned-by-a-user-account)

# Adding collaborators to private packages owned by a user account - 将协作者添加到用户帐户拥有的私有软件包中

As an npm user with a paid user account, you can add another npm user with a paid account as a collaborator on a private package you own.

​	作为具有付费用户帐户的npm用户，您可以将另一个具有付费帐户的npm用户添加为您拥有的私有软件包的协作者。

**Note:** The user you want to add as a collaborator on your private package must have a paid user account. To sign up for a paid account, they can visit `https://www.npmjs.com/settings/username/billing`, replacing `username` with their npm username.

**注意：**您要将协作者添加到您的私有软件包中，该用户必须拥有付费用户帐户。要注册付费帐户，他们可以访问 `https://www.npmjs.com/settings/username/billing` ，将 `username` 替换为他们的npm用户名。

When you add a member to your package, they are sent an email inviting them to the package. The new member has to accept the invitation to gain access to the package.

​	当您将成员添加到软件包中时，他们将收到一封电子邮件邀请他们加入该软件包。新成员必须接受邀请才能获得对软件包的访问权限。

## 在Web界面上授予对私有用户软件包的访问权限 Granting access to a private user package on the web

1. On the [npm website](https://npmjs.com), go to the package to which you want to add a collaborator: `https://www.npmjs.com/package/<your-package-name>`
2. 在[npm网站](https://npmjs.com)上，转到要添加协作者的软件包： `https://www.npmjs.com/package/<your-package-name>` 
3. On the package page, under "Collaborators", click **+**.
4. 在软件包页面上，在“Collaborators”下，点击**+**。
5. Enter the npm username of the collaborator.
6. 输入协作者的npm用户名。
7. Click **Submit**.
8. 点击**Submit**。

## 通过命令行界面授予私有软件包访问权限 Granting private package access from the command line interface

To add a collaborator to a package on the command line, run the following command, replacing `<user>` with the npm username of your collaborator, and `<your-package-name>` with the name of the private package:

​	要在命令行中将协作者添加到软件包中，请运行以下命令，将 `<user>` 替换为您的协作者的npm用户名，将 `<your-package-name>` 替换为私有软件包的名称：

```
npm owner add <user> <your-package-name>
```

## 授予对私有组织软件包的访问权限 Granting access to private organization packages

To grant an npm user access to private organization packages, you must have an organization owner add them to your organization, then add them to a team that has access to the private package. For more information, see "[Adding members to your organization](adding-members-to-your-organization)".

​	要授予npm用户对私有组织软件包的访问权限，您必须让组织所有者将其添加到您的组织中，然后将其添加到具有对私有软件包访问权限的团队中。有关更多信息，请参阅“[向组织添加成员](adding-members-to-your-organization)”。
