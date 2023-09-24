+++
title = "包名争议"
date = 2023-09-22T21:06:57+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/policies/disputes](https://docs.npmjs.com/policies/disputes)

# Dispute Resolution - 争议解决

This document describes the steps that you should take to resolve naming disputes with other npm publishers. It also describes the steps you should take if you think a name [infringes your trademark](#trademarks).

​	本文档描述了您应采取的步骤来解决与其他npm发布者的命名争议。它还描述了如果您认为某个名称侵犯了您的商标，您应采取的步骤。

This document is additive to the guidelines in the [npm Code of Conduct](https://docs.npmjs.com/policies/conduct) and [npm Open-Source terms](https://docs.npmjs.com/policies/open-source-terms). Nothing in this document should be interpreted to contradict any aspect of the npm Code of Conduct or Open-Source Terms.

​	本文档是对[npm行为准则](https://docs.npmjs.com/policies/conduct)和[npm开源条款](https://docs.npmjs.com/policies/open-source-terms)的补充。本文档中的任何内容都不应被解释为与npm行为准则或开源条款的任何方面相矛盾。

## 简而言之 tl;dr

1. Open a support ticket at https://support.github.com/contact/npm-name-disputes.
2. 在https://support.github.com/contact/npm-name-disputes上开启一个支持工单。
3. Fill out the form with as much detail as possible.
4. 填写表单并提供尽可能详细的信息。
5. Support will address your request. Please note submitting a report does not guarantee the transfer of a package, org, or username.
6. 支持团队将处理您的请求。请注意，提交报告并不保证包、组织或用户名的转移。

## 何时使用此流程 When to use this process

This process is an excellent way to:

​	此流程是解决以下问题的绝佳方式：

- Request a name that you believe is currently misleading or could be confused with a name used by your company or open source project
- 请求您认为当前具有误导性或可能与您的公司或开源项目使用的名称混淆的名称
- Request a name related to your company or open source project that cannot be claimed via account recovery
- 请求与您的公司或开源项目相关的名称，无法通过账户恢复来声明

This process does not apply if the package violates our [Terms of Use](https://docs.npmjs.com/policies/open-source-terms), in particular our [Acceptable Use](https://docs.npmjs.com/policies/open-source-terms#acceptable-use) and [Acceptable Content](https://docs.npmjs.com/policies/open-source-terms#acceptable-content) rules, or our [Code of Conduct](https://docs.npmjs.com/policies/conduct). Those documents refer to this one to resolve cases of "squatting"; see below.

​	如果软件包违反了我们的[使用条款](https://docs.npmjs.com/policies/open-source-terms)，特别是我们的[可接受使用](https://docs.npmjs.com/policies/open-source-terms#acceptable-use)和[可接受内容](https://docs.npmjs.com/policies/open-source-terms#acceptable-content)规则，或我们的[行为准则](https://docs.npmjs.com/policies/conduct)，则不适用此流程。这些文件提到了本文档以解决“抢注”案例；请参见下文。

If you see bad behavior or content you believe is unacceptable, refer to the Code of Conduct for guidelines on [reporting violations](https://docs.npmjs.com/policies/conduct#reporting-violations-of-this-code-of-conduct). **You are never expected to resolve abusive behavior on your own.** **We are here to help.**

​	如果您发现不良行为或您认为不可接受的内容，请参考行为准则，了解有关[报告违规行为](https://docs.npmjs.com/policies/conduct#reporting-violations-of-this-code-of-conduct)的准则。**您无需自行解决滥用行为。** **我们将提供帮助。**

## 不适用此流程的情况 When not to use this process

This process is not available for dispute requests due to lack of activity related to a specific name.

​	由于与特定名称相关的活动不足，此流程不适用于争议请求。

Please also note there are cases where a party may have claim to a specific name, but giving that name to the requesting party would pose a supply-chain risk to the npm ecosystem. In such cases, requests may be denied independent of the validity of the claim.

​	还请注意，存在某些情况，其中一方可能对特定名称拥有主张权，但将该名称提供给请求方可能对npm生态系统构成供应链风险。在这种情况下，无论主张的有效性如何，请求可能会被拒绝。

## 商标 Trademarks

npm processes Trademark claims under GitHub's [Trademark Policy](https://docs.github.com/site-policy/content-removal-policies/github-trademark-policy).

​	npm根据GitHub的[商标政策](https://docs.github.com/site-policy/content-removal-policies/github-trademark-policy)处理商标权利主张。

If you think another npm publisher is infringing your trademark, such as by using a confusingly similar package, org, or user account name, please submit a Trademark Policy Violation Report via our [form](https://support.github.com/contact/trademark-policy).

​	如果您认为另一个npm发布者侵犯了您的商标，例如通过使用与您的商标相似的令人困惑的软件包、组织或用户账户名称，请通过我们的[表单](https://support.github.com/contact/trademark-policy)提交商标政策违规报告。

Use of npm's own trademarks is covered by our [Logo and Usage Policy](https://docs.npmjs.com/policies/logos-and-usage).

​	使用npm自己的商标受到我们的[商标和使用政策](https://docs.npmjs.com/policies/logos-and-usage)的约束。

## 变更 Changes

This is a living document and may be updated from time to time. Please refer to the [git history for this document](https://github.com/npm/documentation/blob/main/content/policies/disputes.mdx) to view the changes.

​	本文档是一个活动文档，可能会不时更新。请参阅[本文档的git历史记录](https://github.com/npm/documentation/blob/main/content/policies/disputes.mdx)以查看更改。

## 定义 Definitions

### 抢注 Squatting

It is against npm's [Terms of Use](https://docs.npmjs.com/policies/open-source-terms#acceptable-content) to publish a package, register a user name or an organization name simply for the purposes of reserving it for future use.

​	根据npm的[使用条款](https://docs.npmjs.com/policies/open-source-terms#acceptable-content)，发布软件包、注册用户名或组织名，仅出于保留将来使用的目的是违反规定的。

We do not pro-actively scan the registry for squatted packages, so the fact that a name is in use does not mean we consider it valid. The standards for what we consider squatting depend on what is being squatted:

​	我们不会主动扫描注册表以查找抢注的软件包，因此，名称正在使用并不意味着我们认为它是有效的。我们认为什么是抢注取决于被抢注的内容：

#### 软件包 Packages

Package names are considered squatted if the package has no genuine function.

​	如果软件包没有真正的功能，则被视为抢注的软件包。

#### 组织 Organizations

Organization names are considered squatted if there are no packages published within a reasonable time. If an organization is a paid organization, it may have private packages that are invisible to third parties. For privacy reasons, we cannot reveal whether or not an organization has private packages, so a paid organization will never be considered squatted.

​	如果在合理时间内未发布任何软件包，则被视为抢注的组织名称。如果组织是付费组织，它可能有对第三方不可见的私有软件包。出于隐私原因，我们无法透露组织是否有私有软件包，因此付费组织永远不会被视为抢注。

#### 用户名 User names

We are extremely unlikely to transfer control of a user name, as it is totally valid to be an npm user and never publish any packages: for instance, you might be part of an organization or need read-only access to private packages.

​	我们极不可能将用户账户的控制权转让给他人，因为成为npm用户并不一定意味着要发布任何软件包：例如，您可能是组织的一部分或需要对私有软件包进行只读访问。

## 许可证 License

Copyright (C) npm, Inc., All rights reserved

版权所有（C）npm, Inc.，保留所有权利

This document may be reused under a [Creative Commons Attribution-ShareAlike License](https://creativecommons.org/licenses/by-sa/4.0/).

​	本文档可根据[知识共享署名-相同方式共享许可证](https://creativecommons.org/licenses/by-sa/4.0/)进行再利用。
