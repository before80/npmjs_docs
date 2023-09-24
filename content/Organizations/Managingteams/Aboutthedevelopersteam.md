+++
title = "关于开发者团队"
date = 2023-09-22T21:04:26+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/about-developers-team](https://docs.npmjs.com/about-developers-team)

# About the developers team - 关于开发者团队

The "**developers**" team is automatically created when you create an organization. By default, the developers team has read/write access to all new packages created under the organization's scope.

​	在创建组织时，将自动创建"开发者"团队。默认情况下，开发者团队对在组织范围内创建的所有新软件包具有读写访问权限。

- Members added to the organization, including the organization owner, are automatically added to the **developers** team
- 添加到组织的成员（包括组织所有者）将自动添加到"开发者"团队中。
- The [`maintainers` field](https://docs.npmjs.com/files/package.json#people-fields-author-contributors) in the [`package.json`](https://docs.npmjs.com/files/package.json) of any newly created packages under the organization scope is automatically populated with the members of the current **developers** team
- 在组织范围内创建的任何新软件包的[ `package.json` ](https://docs.npmjs.com/files/package.json)中的[ `maintainers` 字段](https://docs.npmjs.com/files/package.json#people-fields-author-contributors)将自动填充为当前"开发者"团队的成员。

If you create a new package under your organization's scope and you do not want members of the **developers** team to have read/write access to that package, an owner or admin can remove the **developers** team's access to that package. For more information, see "[Managing team access to organization packages](managing-team-access-to-org-packages)".

​	如果您在组织范围内创建了一个新软件包，并且不希望"开发者"团队的成员对该软件包具有读写访问权限，所有者或管理员可以取消"开发者"团队对该软件包的访问权限。有关更多信息，请参阅"[管理团队对组织软件包的访问权限]()"。

If an owner adds a new member to an organization and **does not** want that member to be on the **developers** team, an owner can remove them.

​	如果所有者向组织添加了新成员，并且**不希望**该成员加入"开发者"团队，所有者可以将其移除。

**Note:** The **developers** team can no longer be removed from an organization for the following reasons:

**注意：** 由于以下原因，无法再从组织中删除"开发者"团队：

- It is the source of truth for all users, packages, and default permissions in an organization.
- 它是组织中所有用户、软件包和默认权限的真实来源。
- When you want to restrict write access, it is almost always better to set the default permissions to read-only and create separate teams for managing write permissions.
- 当您想要限制写访问权限时，通常最好将默认权限设置为只读，并创建单独的团队来管理写访问权限。
