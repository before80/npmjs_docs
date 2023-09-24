+++
title = "在CI/CD工作流中使用私有软件包"
date = 2023-09-22T21:01:12+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/using-private-packages-in-a-ci-cd-workflow](https://docs.npmjs.com/using-private-packages-in-a-ci-cd-workflow)

# Using private packages in a CI/CD workflow - 在CI/CD工作流中使用私有软件包

You can use access tokens to test private npm packages with continuous integration (CI) systems, or deploy them using continuous deployment (CD) systems.

​	您可以使用访问令牌来在持续集成（CI）系统中测试私有的npm软件包，或者在持续部署（CD）系统中部署它们。

## 创建一个新的访问令牌 Create a new access token

Create a new access token that will be used only to access npm packages from a CI/CD server.

​	创建一个新的访问令牌，仅用于从CI/CD服务器访问npm软件包。

### 持续集成 Continuous integration

When generating an access token for use in a continuous integration environment, we recommend using a granular access token with limited access to provide greater security.

​	在为持续集成环境生成访问令牌时，我们建议使用具有有限访问权限的细粒度访问令牌，以提供更高的安全性。

If you use a legacy token instead, by default, `npm token create` will generate a token with both read and write permissions. We recommend creating a read-only token:

​	如果您使用的是旧版令牌，那么默认情况下， `npm token create` 将生成一个具有读写权限的令牌。我们建议创建一个只读令牌：

```
npm token create --read-only
```

For more information on creating access tokens, including CIDR-whitelisted tokens, see "[Creating an access token](creating-and-viewing-access-tokens)".

​	有关创建访问令牌的更多信息，包括CIDR白名单令牌，请参阅“[创建访问令牌](creating-and-viewing-access-tokens)”。

### 持续部署 Continuous deployment

Since continuous deployment environments usually involve the creation of a deploy artifact, you may wish to create an [automation token](creating-and-viewing-access-tokens) on the website. This will allow you to publish even if you have two-factor authentication enabled on your account.

​	由于持续部署环境通常涉及创建部署构件，因此您可能希望在网站上创建一个[自动化令牌](creating-and-viewing-access-tokens)。这将允许您发布，即使您的账户启用了双因素身份验证。

### 交互式工作流程 Interactive workflows

If your workflow produces a package, but you publish it manually after validation, then you will want to create a token with read and write permissions, which are granted with the standard token creation command:

​	如果您的工作流程生成一个软件包，但在验证后手动发布它，那么您将需要创建一个具有读写权限的令牌，这可以通过标准的令牌创建命令来授予：

```
npm token create
```

### CIDR白名单 CIDR whitelists

For increased security, you may use a CIDR-whitelisted token that can only be used from a certain IP address range. You can use a CIDR whitelist with a read and publish token or a read-only token:

​	为了增加安全性，您可以使用CIDR白名单令牌，该令牌只能从特定的IP地址范围中使用。您可以在具有读和发布权限的令牌或只读令牌上使用CIDR白名单：

```
npm token create --cidr=[list]
npm token create --read-only --cidr=[list]
```

Example:

示例：

```
npm token create --cidr=192.0.2.0/24
```

For more information, see "[Creating and viewing authentication tokens](creating-and-viewing-access-tokens)".

​	有关详细信息，请参阅“[创建和查看身份验证令牌](creating-and-viewing-access-tokens)”。

## 将令牌设置为CI/CD服务器上的环境变量 Set the token as an environment variable on the CI/CD server

Set your token as an environment variable, or a secret, in your CI/CD server.

​	将令牌设置为CI/CD服务器上的环境变量或密钥。

For example, in GitHub Actions, you would [add your token as a secret](https://docs.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets). Then you can make the secret available to workflows.

​	例如，在GitHub Actions中，您将[将令牌添加为密钥](https://docs.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets)。然后，您可以将该密钥作为环境变量提供给工作流程。

If you named the secret `NPM_TOKEN`, then you would want to create an environment variable named `NPM_TOKEN` from that secret.

​	如果您将密钥命名为 `NPM_TOKEN` ，那么您将希望从该密钥创建一个名为 `NPM_TOKEN` 的环境变量。

```
steps:
  - run: |
      npm install
  - env:
      NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
```

Consult your CI/CD server's documentation for more details.

​	有关更多详细信息，请参阅您的CI/CD服务器的文档。

## 创建并检查项目特定的.npmrc文件 Create and check in a project-specific .npmrc file

Use a project-specific `.npmrc` file with a variable for your token to securely authenticate your CI/CD server with npm.

​	使用项目特定的 `.npmrc` 文件，并使用令牌变量来安全地验证CI/CD服务器与npm的连接。

1. In the root directory of your project, create a custom `.npmrc` file with the following contents:

2. 在项目的根目录中，创建一个包含以下内容的自定义 `.npmrc` 文件：

   ```
   //registry.npmjs.org/:_authToken=${NPM_TOKEN}
   ```

   **Note:** that you are specifying a literal value of `${NPM_TOKEN}`. The npm cli will replace this value with the contents of the `NPM_TOKEN` environment variable. Do **not** put a token in this file.

   **注意：**您正在指定 `${NPM_TOKEN}` 的字面值。npm cli将使用 `NPM_TOKEN` 环境变量的内容替换此值。**不要**将令牌放在此文件中。

3. Check in the `.npmrc` file.

4. 将 `.npmrc` 文件提交到代码库中。

## 保护您的令牌安全 Securing your token

Your token may have permission to read private packages, publish new packages on your behalf, or change user or package settings. Protect your token.

​	您的令牌可能具有读取私有软件包、代表您发布新软件包或更改用户或软件包设置的权限。请保护您的令牌安全。

Do not add your token to version control or store it insecurely. Store it in a password manager, your cloud provider's secure storage, or your CI/CD provider's secure storage.

​	不要将您的令牌添加到版本控制或以不安全的方式存储。将其存储在密码管理器、云提供商的安全存储中，或者CI/CD提供商的安全存储中。

When possible, use granular access tokens with the minimum permissions necessary, and set short expiration dates for your tokens. For more information, see "[About access tokens](about-access-tokens)."

​	在可能的情况下，使用具有最低权限的细粒度访问令牌，并为令牌设置较短的过期日期。有关更多信息，请参阅“[访问令牌概述](about-access-tokens)”部分。
