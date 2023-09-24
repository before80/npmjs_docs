+++
title = "注册表"
date = 2023-09-22T21:23:12+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/cli/v10/using-npm/registry](https://docs.npmjs.com/cli/v10/using-npm/registry)

# registry - 注册表

The JavaScript Package Registry

​	JavaScript包注册表

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

To resolve packages by name and version, npm talks to a registry website that implements the CommonJS Package Registry specification for reading package info.

​	为了按名称和版本解析软件包，npm与实现CommonJS Package Registry规范的注册表网站进行通信以读取软件包信息。

npm is configured to use the **npm public registry** at https://registry.npmjs.org by default. Use of the npm public registry is subject to terms of use available at https://docs.npmjs.com/policies/terms.

​	npm默认配置为使用**npm公共注册表**，网址为https://registry.npmjs.org。使用npm公共注册表受https://docs.npmjs.com/policies/terms中提供的使用条款的约束。

You can configure npm to use any compatible registry you like, and even run your own registry. Use of someone else's registry may be governed by their terms of use.

​	您可以配置npm使用任何兼容的注册表，并且甚至可以运行自己的注册表。使用他人的注册表可能受其使用条款的约束。

npm's package registry implementation supports several write APIs as well, to allow for publishing packages and managing user account information.

​	npm的软件包注册表实现还支持几个写API，以便发布软件包和管理用户帐户信息。

The npm public registry is powered by a CouchDB database, of which there is a public mirror at https://skimdb.npmjs.com/registry.

​	npm的公共注册表由CouchDB数据库驱动，其中有一个公共镜像位于https://skimdb.npmjs.com/registry。

The registry URL used is determined by the scope of the package (see [`scope`](https://docs.npmjs.com/cli/v10/using-npm/scope). If no scope is specified, the default registry is used, which is supplied by the [`registry` config](https://docs.npmjs.com/cli/v10/using-npm/config#registry) parameter. See [`npm config`](https://docs.npmjs.com/cli/v10/commands/npm-config), [`npmrc`](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc), and [`config`](https://docs.npmjs.com/cli/v10/using-npm/config) for more on managing npm's configuration. Authentication configuration such as auth tokens and certificates are configured specifically scoped to an individual registry. See [Auth Related Configuration](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc#auth-related-configuration)

​	使用的注册表URL由软件包的范围确定（参见[ `scope` ](https://docs.npmjs.com/cli/v10/using-npm/scope)）。如果未指定范围，则使用默认注册表，该注册表由[ `registry`  config](https://docs.npmjs.com/cli/v10/using-npm/config#registry)参数提供。有关管理npm配置的更多信息，请参阅[ `npm config` ](https://docs.npmjs.com/cli/v10/commands/npm-config)，[ `npmrc` ](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc)和[ `config` ](https://docs.npmjs.com/cli/v10/using-npm/config)。身份验证配置（如身份验证令牌和证书）是针对单个注册表进行配置的。请参阅[与身份验证相关的配置](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc#auth-related-configuration)。

When the default registry is used in a package-lock or shrinkwrap it has the special meaning of "the currently configured registry". If you create a lock file while using the default registry you can switch to another registry and npm will install packages from the new registry, but if you create a lock file while using a custom registry packages will be installed from that registry even after you change to another registry.

​	当在package-lock或shrinkwrap中使用默认注册表时，它具有“当前配置的注册表”的特殊含义。如果您在使用默认注册表时创建一个锁定文件，您可以切换到另一个注册表，npm将从新注册表安装软件包，但是如果您在使用自定义注册表时创建一个锁定文件，即使在切换到另一个注册表后，软件包也将从该注册表安装。

### npm是否会将有关我的任何信息发送回注册表？ Does npm send any information about me back to the registry?

Yes.

是的。

When making requests of the registry npm adds two headers with information about your environment:

​	在向注册表发出请求时，npm会添加两个包含有关您的环境信息的标头：

- `Npm-Scope` – If your project is scoped, this header will contain its scope. In the future npm hopes to build registry features that use this information to allow you to customize your experience for your organization.
- `Npm-Scope`  - 如果您的项目已经有范围，则此标头将包含其范围。将来，npm希望构建使用此信息的注册表功能，以便您可以根据您的组织自定义您的体验。
- `Npm-In-CI` – Set to "true" if npm believes this install is running in a continuous integration environment, "false" otherwise. This is detected by looking for the following environment variables: `CI`, `TDDIUM`, `JENKINS_URL`, `bamboo.buildKey`. If you'd like to learn more you may find the [original PR](https://github.com/npm/npm-registry-client/pull/129) interesting. This is used to gather better metrics on how npm is used by humans, versus build farms.
- `Npm-In-CI`  - 如果npm认为此安装是在持续集成环境中运行的，则设置为“true”，否则设置为“false”。这是通过查找以下环境变量来检测的： `CI` ， `TDDIUM` ， `JENKINS_URL` ， `bamboo.buildKey` 。如果您想了解更多信息，可以查看[原始PR](https://github.com/npm/npm-registry-client/pull/129)。这用于更好地收集关于npm如何被人类和构建环境使用的指标。

The npm registry does not try to correlate the information in these headers with any authenticated accounts that may be used in the same requests.

​	npm注册表不会尝试将这些标头中的信息与可能在同一请求中使用的任何经过身份验证的帐户相关联。

### 如何防止我的软件包在官方注册表中发布？ How can I prevent my package from being published in the official registry?

Set `"private": true` in your `package.json` to prevent it from being published at all, or `"publishConfig":{"registry":"http://my-internal-registry.local"}` to force it to be published only to your internal/private registry.

​	在您的 `package.json` 中设置 `"private": true` 可以防止其被发布，或者设置 `"publishConfig":{"registry":"http://my-internal-registry.local"}` 将其强制发布到您的内部/私有注册表。

See [`package.json`](https://docs.npmjs.com/cli/v10/configuring-npm/package-json) for more info on what goes in the package.json file.

​	有关在package.json文件中放入什么的更多信息，请参阅[ `package.json` ](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)。

### 我在哪里可以找到我的（和其他人的）已发布软件包？ Where can I find my (and others') published packages?

https://www.npmjs.com/

### See also

- [npm config](https://docs.npmjs.com/cli/v10/commands/npm-config)
- [config](https://docs.npmjs.com/cli/v10/using-npm/config)
- [npmrc](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc)
- [npm developers](https://docs.npmjs.com/cli/v10/using-npm/developers)
