+++
title = "重命名组织"
date = 2023-09-22T21:02:16+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/renaming-an-organization](https://docs.npmjs.com/renaming-an-organization)

# Renaming an organization - 重命名组织

Organizations cannot be renamed from the website or command line interface.

​	无法从网站或命令行界面重命名组织。

To rename an organization, as an organization owner, you must manually migrate your existing organization members, teams, and packages to a new organization, then [contact npm Support](https://www.npmjs.com/support) to have the outdated packages unpublished and the previous organization deleted.

​	要重命名组织，作为组织所有者，您必须手动迁移现有组织成员、团队和软件包到一个新的组织，然后[联系npm支持](https://www.npmjs.com/support)以取消发布过时的软件包并删除以前的组织。

1. [Create a new organization](creating-an-organization) with the name you want. If your old organization is on a paid plan, you must choose a paid plan for the new organization.
2. [创建一个新的组织](creating-an-organization)，使用您想要的名称。如果您的旧组织是付费计划，您必须为新组织选择一个付费计划。
3. [Add the members](adding-members-to-your-organization) of your old organization to your new organization.
4. [将您旧组织的成员](adding-members-to-your-organization)添加到新组织中。
5. In your new organization, [create teams](creating-teams) to match teams in your old organization.
6. 在新组织中，[创建与旧组织中的团队相匹配的团队](creating-teams)。
7. Republish packages to the new organization by updating the package scope in its `package.json` file to match the new organization name and running `npm publish`.
8. 通过更新 `package.json` 文件中的软件包范围，使其与新组织名称匹配，并运行 `npm publish` ，将软件包重新发布到新组织。
9. In the new organization teams, [configure package access](managing-team-access-to-packages) to match team package access in your old organization.
10. 在新组织的团队中，[配置软件包访问权限](managing-team-access-to-packages)，以匹配旧组织中的团队软件包访问权限。
11. [Contact npm Support](https://www.npmjs.com/support) to have the outdated packages unpublished and the previous organization deleted.
12. [联系npm支持](https://www.npmjs.com/support)，以取消发布过时的软件包并删除以前的组织。
