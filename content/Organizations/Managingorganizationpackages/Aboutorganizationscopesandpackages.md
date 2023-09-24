+++
title = "关于组织范围和软件包"
date = 2023-09-22T21:05:22+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/about-organization-scopes-and-packages](https://docs.npmjs.com/about-organization-scopes-and-packages)

# About organization scopes and packages - 关于组织范围和软件包

Every organization is granted an organization scope, a unique namespace for packages owned by the organization that matches the organization name. For example, an organization named "wombat" would have the scope `@wombat`.

​	每个组织都被授予一个组织范围，即与组织名称匹配的由组织拥有的软件包的唯一命名空间。例如，一个名为"wombat"的组织将具有范围 `@wombat` 。

You can use scopes to:

​	您可以使用范围来：

- Maintain a fork of a package: `@wombat/request`.
- 维护软件包的分支： `@wombat/request` 。
- Avoid name disputes with popular names: `@wombat/web`.
- 避免与流行名称的命名冲突： `@wombat/web` 。
- Easily find packages in the same namespace
- 方便地在同一命名空间中查找软件包。

Packages in a scope must follow the same [naming guidelines](https://docs.npmjs.com/files/package.json#name) as unscoped packages.

​	范围内的软件包必须遵循与无作用域软件包相同的[命名准则](https://docs.npmjs.com/files/package.json#name)。

## 管理无作用域软件包 Managing unscoped packages

While you are granted a scope by default when you create an organization, you can also use organizations to manage unscoped packages, or packages under a different scope (such as a user scope).

​	虽然创建组织时默认会授予一个范围，但您也可以使用组织来管理无作用域软件包，或者具有不同范围（如用户范围）的软件包。
