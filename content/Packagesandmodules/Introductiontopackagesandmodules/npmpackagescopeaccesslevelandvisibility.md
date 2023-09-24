+++
title = "npm 包的作用域、访问级别和可见性"
date = 2023-09-22T20:55:03+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/package-scope-access-level-and-visibility](https://docs.npmjs.com/package-scope-access-level-and-visibility)

# npm package scope, access level, and visibility - npm 包的作用域、访问级别和可见性

Visibility of npm packages depends on the scope (namespace) in which the package is contained, and the access level (private or public) set for the package.

​	npm 包的可见性取决于包所在的作用域（命名空间）以及为包设置的访问级别（私有或公共）。

Note: To create organization-scoped packages, you must first create an organization. For more information, see "[Creating an organization](https://docs.npmjs.com/creating-an-organization)".

注意：要创建组织作用域的包，您必须首先创建一个组织。有关更多信息，请参见 "[创建组织](https://docs.npmjs.com/creating-an-organization)"。

## 公共注册表 Public registry

| 作用域   | 访问级别 | 可以查看和下载的用户                   | 可以写入（发布）的用户                   |
| -------- | -------- | -------------------------------------- | ---------------------------------------- |
| 组织     | 私有     | 组织中具有对包的读访问权限的团队成员   | 组织中具有对包的读写访问权限的团队成员   |
| 组织     | 公共     | 所有人                                 | 组织中具有对包的读写访问权限的团队成员   |
| 用户     | 私有     | 包的所有者和被授予包的读访问权限的用户 | 包的所有者和被授予包的读写访问权限的用户 |
| 用户     | 公共     | 所有人                                 | 包的所有者和被授予包的读写访问权限的用户 |
| 无作用域 | 公共     | 所有人                                 | 包的所有者和被授予包的读写访问权限的用户 |

| Scope    | Access level | Can view and download                                        | Can write (publish)                                          |
| -------- | ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Org      | Private      | Members of a team in the organization with read access to the package | Members of a team in the organization with read and write access to the package |
| Org      | Public       | Everyone                                                     | Members of a team in the organization with read and write access to the package |
| User     | Private      | The package owner and users who have been granted read access to the package | The package owner and users who have been granted read and write access to the package |
| User     | Public       | Everyone                                                     | The package owner and users who have been granted read and write access to the package |
| Unscoped | Public       | Everyone                                                     | The package owner and users who have been granted read and write access to the package |

Note: Only user accounts can create and manage unscoped packages. Organizations can only manage scoped packages.

注意：只有用户账户可以创建和管理无作用域的包。组织只能管理有作用域的包。
