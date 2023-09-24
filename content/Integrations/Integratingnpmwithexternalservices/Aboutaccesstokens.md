+++
title = "有关访问令牌的信息"
date = 2023-09-22T21:00:39+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/about-access-tokens](https://docs.npmjs.com/about-access-tokens)

# About access tokens - 有关访问令牌的信息

**Note:** You must be using npm version 5.5.1 or greater to use access tokens.

**注意：**您必须使用npm版本5.5.1或更高版本才能使用访问令牌。

An access token is an alternative to using your username and password for authenticating to npm when using the API or the npm command-line interface (CLI). An access token is a hexadecimal string that you can use to authenticate, and which gives you the right to install and/or publish your modules.

​	访问令牌是在使用API或npm命令行界面（CLI）时，用于进行npm身份验证的用户名和密码的替代方法。访问令牌是一个十六进制字符串，您可以用它进行身份验证，并且有权安装和/或发布您的模块。

There are two types of access tokens available:

- [Legacy tokens](#about-legacy-tokens)
- [传统令牌](#关于传统令牌)
- [Granular access tokens](#about-granular-access-tokens)
- [细粒度访问令牌](#关于细粒度访问令牌)

You can create access tokens to give other tools (such as continuous integration testing environments) access to your npm packages. For example, GitHub Actions provides the ability to store [secrets](https://docs.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets), such as access tokens, that you can then use to authenticate. When your workflow runs, it will be able to complete npm tasks as you, including installing private packages you can access.

​	您可以创建访问令牌，以便让其他工具（例如持续集成测试环境）访问您的npm软件包。例如，GitHub Actions提供了存储[secrets](https://docs.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets)（例如访问令牌）的功能，您可以使用这些secrets进行身份验证。当您的工作流运行时，它将能够以您的身份完成npm任务，包括安装您可以访问的私有软件包。

You can work with tokens from the web or the CLI, whichever is easiest. What you do in each environment will be reflected in the other environment.

​	您可以从Web或CLI中使用令牌，以便选择最简单的方式。您在每个环境中所做的操作将在另一个环境中反映出来。

npm token commands let you:

​	npm令牌命令可以让您：

- View tokens for easier tracking and management
- 查看令牌以便于跟踪和管理
- Create new legacy tokens
- 创建新的传统令牌
- Limit access according to IP address ranges (CIDR)
- 根据IP地址范围（CIDR）限制访问
- Delete/revoke tokens
- 删除/撤销令牌

For more information on creating and viewing access tokens on the web and CLI, see "[Creating and viewing access tokens](creating-and-viewing-access-tokens)".

​	有关在Web和CLI上创建和查看访问令牌的更多信息，请参阅“[创建和查看访问令牌](creating-and-viewing-access-tokens)”。

## 关于传统令牌 About legacy tokens

Legacy tokens are created with the same permissions as the user who created them. The npm CLI automatically generates and uses a publish token when you run `npm login`.

​	传统令牌与创建它们的用户具有相同的权限。当您运行 `npm login` 时，npm CLI会自动生成并使用发布令牌。

There are three different types of legacy tokens:

​	传统令牌有三种不同类型：

- **Read-only**: You can use these tokens to download packages from the registry. These tokens are best for automation and workflows where you are installing packages. For greater security, we recommend using [granular access tokens](#about-granular-access-tokens) instead.
- **只读**：您可以使用这些令牌从注册表中下载软件包。这些令牌最适合自动化和工作流，您可以使用它们来安装软件包。为了提高安全性，我们建议改用[细粒度访问令牌](#关于细粒度访问令牌)。
- **Automation**: You can use these tokens to download packages and install new ones. These tokens are best for automation workflows where you are publishing new packages. Automation tokens do not 2FA for executing operations on npm and are suitable for CI/CD workflows. For greater security, we recommend using [granular access tokens](#about-granular-access-tokens) instead.
- **自动化**：您可以使用这些令牌下载软件包并安装新软件包。这些令牌最适合自动化工作流，您可以使用它们来发布新软件包。自动化令牌不需要执行npm操作的2FA，并适用于CI / CD工作流程。为了提高安全性，我们建议改用[细粒度访问令牌](#关于细粒度访问令牌)。
- **Publish**: You can use these tokens to download packages, install packages, and update user and package settings. We recommend using them for interactive workflows such as a CLI. If 2FA is enabled on your account, publish tokens will require 2FA to execute sensitive operations on npm.
- **发布**：您可以使用这些令牌下载软件包、安装软件包和更新用户和软件包设置。我们建议将其用于交互式工作流程，例如CLI。如果您的帐户启用了2FA，则发布令牌将需要2FA才能执行敏感的npm操作。

Legacy tokens do not have an expiration date. It is important to be aware of your tokens and keep them protected for account security. For more information, see "[Securing your token](using-private-packages-in-a-ci-cd-workflow#securing-your-token)."

​	传统令牌没有过期日期。了解您的令牌并保护它们对于帐户安全非常重要。有关更多信息，请参见“[保护您的令牌](using-private-packages-in-a-ci-cd-workflow#securing-your-token)”。

## 关于细粒度访问令牌 About granular access tokens

Granular access tokens allow you to restrict access provided to the token based on what you want to use the token for. With granular access tokens, you can:

​	细粒度访问令牌允许您根据使用令牌的目的限制令牌的访问权限。使用细粒度访问令牌，您可以：

- Restrict which packages and scopes a token has access to
- 限制令牌对软件包和作用域的访问权限
- Grant tokens access to specific organizations
- 授予令牌对特定组织的访问权限
- Set a token expiration date
- 设置令牌的过期日期
- Limit token access based on IP address ranges
- 基于IP地址范围限制令牌访问权限
- Select between **read-only** or **read and write** access
- 选择**只读**或**读写**访问权限之间的区别

You can create up to 1000 granular access tokens on your npm account. You can set how long your token is valid for, at least one day in the future. Each token can access up to 50 organizations, and up to either 50 packages, 50 scopes, or a combination of 50 packages and scopes. Access tokens are tied to users’ permission; hence it cannot have more permission than the user at any point in time. If a user has their access revoked from a package or an org., their granular access token also will have its access revoked from those packages or org.

​	您可以在npm帐户上创建多达1000个细粒度访问令牌。您可以设置令牌的有效期，至少为未来的一天。每个令牌最多可以访问50个组织，以及最多50个软件包、50个作用域或50个软件包和作用域的组合。访问令牌与用户的权限相关联，因此在任何时候它都不能拥有比用户更多的权限。如果用户被从软件包或组织中撤销访问权限，他们的细粒度访问令牌也将从这些软件包或组织中撤销访问权限。当您将令牌授予组织时，令牌只能用于管理组织设置和与组织相关的团队或用户，而不能用于发布由组织管理的软件包。

When you give a token access to an organization, the token can only be used for managing organization settings and teams or users associated with the organization. It does not give the token the right to publish packages managed by the organization.

​	当您授予令牌对组织的访问权限时，该令牌只能用于管理组织设置以及与组织相关的团队或用户。它不会赋予令牌发布由组织管理的软件包的权限。
