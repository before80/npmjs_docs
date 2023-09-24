+++
title = "配置您的npm客户端与组织设置"
date = 2023-09-22T21:05:31+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/configuring-your-npm-client-with-your-organization-settings](https://docs.npmjs.com/configuring-your-npm-client-with-your-organization-settings)

# Configuring your npm client with your organization settings - 配置您的npm客户端与组织设置

As an organization member, you can configure your npm client to:

​	作为组织成员，您可以配置您的npm客户端来：

- make a single package or all new packages you create locally use your organization's scope
- 让您本地创建的单个软件包或所有新软件包使用您的组织范围。
- make a single package or all new packages you create locally have default public visibility
- 让您本地创建的单个软件包或所有新软件包具有默认的公开可见性。

Before configuring your npm client, you must [install npm](downloading-and-installing-node-js-and-npm).

​	在配置您的npm客户端之前，您必须[安装npm](downloading-and-installing-node-js-and-npm)。

## 配置您的npm客户端使用您的组织范围 Configuring your npm client to use your organization's scope

If you will be publishing packages with your organization's scope often, you can add your organization's scope to your global `.npmrc` configuration file.

​	如果您经常使用您的组织范围发布软件包，您可以将您的组织范围添加到全局的 `.npmrc` 配置文件中。

### 为所有新软件包设置您的组织范围 Setting your organization scope for all new packages

**Note:** Setting the organization scope using the steps below will only set the scope for new packages; for existing packages, you will need to update the `name` field in `package.json`.

**注意：** 使用下面的步骤设置组织范围只会对新软件包生效；对于现有软件包，您需要在 `package.json` 文件中更新 `name` 字段。

On the command line, run the following command, replacing <org-name> with the name of your organization:

​	在命令行中运行以下命令，将 `<org-name>` 替换为您的组织名称：

```
npm config set scope <org-name> --global
```

For packages you do not want to publish with your organization's scope, you must manually edit the package's `package.json` to remove the organization scope from the `name` field.

​	对于您不想使用组织范围发布的软件包，您必须手动编辑软件包的 `package.json` ，将组织范围从 `name` 字段中移除。

### 为单个软件包设置您的组织范围 Setting your organization scope for a single package

1. On the command line, navigate to the package directory.

2. 在命令行中，进入软件包目录。

   ```
   cd /path/to/package
   ```

3. Run the following command, replacing <org-name> with the name of your organization:

4. 运行以下命令，将 `<org-name>` 替换为您的组织名称：

   ```
   npm config set scope <org-name>
   ```

## 将默认软件包可见性更改为公开 Changing default package visibility to public

By default, publishing a scoped package with `npm publish` will publish the package as private. If you are a member of an organization on the free organization plan, or are on the paid organization plan but want to publish a scoped package as public, you must pass the `--access public` flag:

​	默认情况下，使用 `npm publish` 发布带有范围的软件包将以私有方式发布。如果您是免费组织计划的成员，或者是付费组织计划的成员但希望将带有范围的软件包发布为公开的，您必须传递 `--access public` 标志：

```
npm publish --access public
```

### 为单个软件包设置软件包可见性为公开 Setting package visibility to public for a single package

You can set a single package to pass `--access public `to every `npm publish` command that you issue for that package.

​	您可以将单个软件包设置为在每次发布该软件包时都传递 `--access public` 。

1. On the command line, navigate to the package directory.

2. 在命令行中，进入软件包目录。

   ```
   cd /path/to/package
   ```

3. Run the following command:

4. 运行以下命令：

   ```
   npm config set access public
   ```

### 为所有软件包设置软件包可见性为公开 Setting package visibility to public for all packages

You can set all packages to pass `--access public `to every `npm publish` command that you issue for that package.

​	您可以将所有软件包设置为在每次发布该软件包时都传递 `--access public` 。

**Warning:** Setting packages access to `public` in your global `.npmrc` will affect all packages you create, including packages in your personal account scope, as well as packages scoped to your organization.

**警告：** 在全局的 `.npmrc` 中将软件包访问设置为 `public` 将影响您创建的所有软件包，包括您个人账户范围内的软件包以及您组织范围内的软件包。

On the command line, run the following command:

​	在命令行中运行以下命令：

```
npm config set access public --global
```
