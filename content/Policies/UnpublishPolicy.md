+++
title = "取消发布政策"
date = 2023-09-22T21:07:31+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/policies/unpublish](https://docs.npmjs.com/policies/unpublish)

# npm Unpublish Policy - npm取消发布政策

This document describes your options when looking to unpublish a package published to the public registry.

​	本文档描述了在公共注册表中发布的软件包取消发布时的选项。

Registry data is immutable, meaning once published, a package cannot change. We do this for reasons of security and stability of the users who depend on those packages. So if you've ever published a package called "bob" at version 1.1.0, no other package can ever be published with that name at that version. This is true even if that package is unpublished.

​	注册表数据是不可变的，这意味着一旦发布了一个软件包，就无法更改。我们之所以这样做，是为了保护依赖这些软件包的用户的安全和稳定性。因此，如果您曾经发布过一个名为"bob"、版本号为1.1.0的软件包，那么在该版本中将永远无法发布其他软件包。即使该软件包被取消发布，这一点也是正确的。

However, because accidents happen, we allow you to unpublish packages in the situations described below. Otherwise, you can always deprecate a package.

​	然而，由于意外情况的发生，我们允许您在以下情况下取消发布软件包。否则，您可以始终将软件包标记为过时。

## 发布时间少于72小时的软件包 Packages published less than 72 hours ago

For newly created packages, as long as no other packages in the npm Public Registry depend on your package, you can unpublish anytime within the first 72 hours after publishing.

​	对于新创建的软件包，只要npm公共注册表中没有其他软件包依赖于您的软件包，您可以在首次发布后的72小时内随时取消发布。

## 发布时间超过72小时的软件包 Packages published more than 72 hours ago

Regardless of how long ago a package was published, you can unpublish a package that:

​	无论软件包发布了多长时间，您都可以取消发布满足以下条件的软件包：

- no other packages in the npm Public Registry depend on
- npm公共注册表中没有其他软件包依赖于该软件包
- had less than 300 downloads over the last week
- 上周下载量少于300次
- has a single owner/maintainer
- 有单一所有者/维护者

## 如何取消发布 How to unpublish

To unpublish a single package version, run `npm unpublish <package_name>@<version>`.

​	要取消发布单个软件包版本，请运行 `npm unpublish <package_name>@<version>` 。

If all the versions of a package can be unpublished, you can unpublish all versions at once by running `npm unpublish <package_name> --force`.

​	如果可以取消发布软件包的所有版本，您可以通过运行 `npm unpublish <package_name> --force` 一次取消发布所有版本。

## 注意事项： Considerations:

- Once `package@version` has been used, you can never use it again. You must publish a new version even if you unpublished the old one.
- 一旦使用了 `package@version` ，您将永远无法再次使用它。即使您取消发布了旧版本，您也必须发布一个新版本。
- Once you have unpublished a package, you will not be able to undo the unpublish.
- 一旦您取消发布了一个软件包，您将无法撤消取消发布。
- If you entirely unpublish all versions of a package, you may not publish any new versions of that package until 24 hours have passed.
- 如果您完全取消发布了一个软件包的所有版本，在24小时内您将无法发布该软件包的任何新版本。

## 如果您的软件包不符合取消发布的条件该怎么办？ What to do if your package does not meet the unpublish criteria?

If your package does not meet the unpublish policy criteria, we recommend [deprecating](https://docs.npmjs.com/cli/deprecate) the package. This allows the package to be downloaded but publishes a clear warning message (that you get to write) every time the package is downloaded, and on the package's npmjs.com page. Users will know that you do not recommend they use the package, but if they are depending on it their builds will not break. We consider this a good compromise between reliability and author control.

​	如果您的软件包不符合取消发布政策的条件，我们建议您将软件包标记为[过时](https://docs.npmjs.com/cli/deprecate)。这将允许用户下载软件包，但每次下载软件包时都会显示一个明确的警告消息（由您编写），并显示在软件包的npmjs.com页面上。用户将知道您不建议他们使用该软件包，但如果他们依赖该软件包，他们的构建不会中断。我们认为这是可靠性和作者控制之间的一个很好的折衷方案。

This can be achieved by using one of the following from your command line:

​	您可以使用以下命令之一在命令行中实现：

- `npm deprecate <package> "<message>"` to deprecate the entire package
- `npm deprecate <package> "<message>"` 将整个软件包标记为过时
- `npm deprecate <package>@<version> "<message>"` to deprecate a specific version
- `npm deprecate <package>@<version> "<message>"` 将特定版本标记为过时

If the entire package is deprecated, the package name will be dropped from our search results.

​	如果整个软件包被标记为过时，该软件包名称将从我们的搜索结果中删除。

## 关于我们的取消发布政策的更多信息 More on our unpublish policy

This document is additive to the [unpublish procedures](https://docs.npmjs.com/unpublishing-packages-from-the-registry), the CLI commands [unpublish documentation](https://docs.npmjs.com/cli/unpublish) and the ["Changes to npm Unpublish Policy - January 2020"](https://blog.npmjs.org/post/190553543620/changes-to-npmunpublish-policy-january-2020) blog post.

​	本文档是对[取消发布程序](https://docs.npmjs.com/unpublishing-packages-from-the-registry)、CLI命令[取消发布文档](https://docs.npmjs.com/cli/unpublish)和["2020年1月npm取消发布政策变更"](https://blog.npmjs.org/post/190553543620/changes-to-npmunpublish-policy-january-2020)博文的补充。

## 问题？ Issues?

If for some reason your package meets the unpublish policy criteria but the unpublish command fails, or if you need assistance with the deprecate process, please [reach out to our support team](https://npmjs.com/support) where we'll be happy to assist.

​	如果由于某种原因您的软件包符合取消发布政策的条件，但取消发布命令失败，或者如果您需要在过时过程中获得帮助，请[联系我们的支持团队](https://npmjs.com/support)，我们将乐意提供帮助。

If you believe a package violates npm's terms or policies, such as our terms of use, [reach out to our support team](https://www.npmjs.com/support). If a package infringes your copyright, [refer to npm's DMCA takedown policy](https://docs.npmjs.com/policies/dmca). If you believe a package violates your privacy rights, [contact our privacy team](https://docs.npmjs.com/policies/privacy#contact) as soon as possible.

​	如果您认为某个软件包违反了npm的条款或政策，例如我们的使用条款，请[联系我们的支持团队](https://www.npmjs.com/support)。如果某个软件包侵犯了您的版权，请参考npm的[DMCA下架政策](https://docs.npmjs.com/policies/dmca)。如果您认为某个软件包侵犯了您的隐私权，请尽快[联系我们的隐私团队](https://docs.npmjs.com/policies/privacy#contact)。

## 变更 Changes

This is a living document and may be updated from time to time. Please refer to the [git history for this document](https://github.com/npm/documentation/blob/main/content/policies/unpublish.mdx) to view the changes.

​	本文档是一个活动文档，可能会不时更新。请参考[此文档的git历史记录](https://github.com/npm/documentation/blob/main/content/policies/unpublish.mdx)查看更改。

## 许可证 License

Copyright (C) npm, Inc., All rights reserved

版权所有（C）npm, Inc.，保留所有权利

This document may be reused under a [Creative Commons Attribution-ShareAlike License](https://creativecommons.org/licenses/by-sa/4.0/).

​	本文档可在[知识共享署名-相同方式共享许可协议](https://creativecommons.org/licenses/by-sa/4.0/)下重新使用。
