+++
title = "组织"
date = 2023-09-22T21:24:30+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/cli/v10/using-npm/orgs](https://docs.npmjs.com/cli/v10/using-npm/orgs)

# orgs - 组织

Working with Teams & Orgs

与团队和组织合作

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

There are three levels of org users:

​	有三个级别的组织用户：

1. Super admin, controls billing & adding people to the org.
2. 超级管理员，负责管理账单和添加人员到组织。
3. Team admin, manages team membership & package access.
4. 团队管理员，管理团队成员和软件包访问权限。
5. Developer, works on packages they are given access to.
6. 开发者，负责处理他们被授权访问的软件包。

The super admin is the only person who can add users to the org because it impacts the monthly bill. The super admin will use the website to manage membership. Every org has a `developers` team that all users are automatically added to.

​	只有超级管理员可以将用户添加到组织中，因为这会影响每月的账单。超级管理员将使用网站来管理成员资格。每个组织都有一个名为  `developers`  的团队，所有用户都会自动添加到该团队中。

The team admin is the person who manages team creation, team membership, and package access for teams. The team admin grants package access to teams, not individuals.

​	团队管理员负责管理团队的创建、团队成员和团队的软件包访问权限。团队管理员向团队授予软件包访问权限，而不是个人。

The developer will be able to access packages based on the teams they are on. Access is either read-write or read-only.

​	开发者将能够根据他们所在的团队访问软件包。访问权限可以是读写或只读。

There are two main commands:

​	有两个主要的命令：

1. `npm team` see [npm team](https://docs.npmjs.com/cli/v10/commands/npm-team) for more details
2. `npm team`  详见 [npm team](https://docs.npmjs.com/cli/v10/commands/npm-team) 获取更多详细信息
3. `npm access` see [npm access](https://docs.npmjs.com/cli/v10/commands/npm-access) for more details
4. `npm access`  详见 [npm access](https://docs.npmjs.com/cli/v10/commands/npm-access) 获取更多详细信息

### 团队管理员创建团队 Team Admins create teams

- Check who you’ve added to your org:
- 检查您已添加到组织中的人员：

```bash
npm team ls <org>:developers
```

- Each org is automatically given a `developers` team, so you can see the whole list of team members in your org. This team automatically gets read-write access to all packages, but you can change that with the `access` command.
- 每个组织都会自动拥有一个  `developers`  团队，因此您可以查看组织中整个团队成员的列表。该团队会自动获得对所有软件包的读写访问权限，但您可以使用  `access`  命令进行更改。
- Create a new team:
- 创建一个新的团队：

```bash
npm team create <org:team>
```

- Add members to that team:
- 将成员添加到该团队：

```bash
npm team add <org:team> <user>
```

### 发布软件包和调整软件包访问权限 Publish a package and adjust package access

- In package directory, run
- 在软件包目录中运行

```bash
npm init --scope=<org>
```

to scope it for your org & publish as usual

将其限定为您的组织并像往常一样发布

- Grant access:
- 授予访问权限：

```bash
npm access grant <read-only|read-write> <org:team> [<package>]
```

- Revoke access:
- 撤销访问权限：

```bash
npm access revoke <org:team> [<package>]
```

### 监控软件包访问权限 Monitor your package access

- See what org packages a team member can access:
- 查看团队成员可以访问的组织软件包：

```bash
npm access ls-packages <org> <user>
```

- See packages available to a specific team:
- 查看特定团队可以访问的软件包：

```bash
npm access ls-packages <org:team>
```

- Check which teams are collaborating on a package:
- 检查哪些团队正在协作开发一个软件包：

```bash
npm access ls-collaborators <pkg>
```

### See also

- [npm team](https://docs.npmjs.com/cli/v10/commands/npm-team)
- [npm access](https://docs.npmjs.com/cli/v10/commands/npm-access)
- [npm scope](https://docs.npmjs.com/cli/v10/using-npm/scope)
