+++
title = "隐私政策"
date = 2023-09-22T21:07:20+08:00
weight = 60
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/policies/privacy](https://docs.npmjs.com/policies/privacy)

# Privacy Questions and Answers - 隐私问题与回答

This notice describes how [npm, Inc.](https://www.npmjs.com/about), or *npm* for short, collects and uses data about you.

​	本通知描述了[npm, Inc.](https://www.npmjs.com/about)或简称为*npm*如何收集和使用关于您的数据。

## 最重要的是什么？What's most important?

That depends on your personal situation, which is why you should read on and decide for yourself. But at a minimum, absolutely every npm user should understand:

​	这取决于您的个人情况，因此您应该继续阅读并自行决定。但至少，每个npm用户都应该明白：

*The npm public registry is for making software available to everyone online.*

​	*npm公共注册表是为了向每个人在线提供软件。*

But: *Software comes from people, and says something about us.*

​	但是：*软件来自人，也反映了我们的一些情况。*

So: *Think carefully about what packages to publish, what data you put in those packages, and what others might do with that data.*

​	所以：*请仔细考虑要发布哪些软件包，将哪些数据放入这些软件包中，以及其他人可能如何使用这些数据。*

When you create an account, certain contact information is displayed publicly in the npm platform. And when you upload a package, your name and contact information may become associated with that package.

​	当您创建帐户时，某些联系信息将公开显示在npm平台上。当您上传软件包时，您的姓名和联系信息可能与该软件包相关联。

If you find yourself in a jam, [open a support ticket](https://npmjs.com/support).

​	如果您遇到困境，请[提交支持工单](https://npmjs.com/support)。

## npm如何收集关于我的数据？ How does npm collect data about me?

npm collects data about you:

​	npm收集关于您的数据：

- when you use the [npm command](https://www.npmjs.com/package/npm), the [npx command](https://docs.npmjs.com/cli/commands/npx) or another program to access the [npm public registry](https://registry.npmjs.org/), [Enterprise registries that npm hosts](https://www.npmjs.com/enterprise), [private packages](https://www.npmjs.com/features), such as when you're publishing a software package, and APIs for functionality like account and permissions management
- 当您使用[npm命令](https://www.npmjs.com/package/npm)，[npx命令](https://docs.npmjs.com/cli/commands/npx)或其他程序访问[npm公共注册表](https://registry.npmjs.org/)、[npm托管的企业注册表](https://www.npmjs.com/enterprise)、[私有软件包](https://www.npmjs.com/features)（例如发布软件包时）以及用于帐户和权限管理等功能的API时
- when you browse the npm website, [npmjs.com](https://www.npmjs.com/)
- 当您浏览npm网站[npmjs.com](https://www.npmjs.com/)
- when you use either the npm command or the website to create an npm account, update your account, and sign up for npm services
- 当您使用npm命令或网站创建npm帐户、更新帐户并注册npm服务时
- when you send support, privacy, legal, and other requests to npm
- 当您向npm发送支持、隐私、法律和其他请求时
- when working with and researching current and potential customers
- 当与当前和潜在客户合作和研究时

When researching potential customers, npm staff sometimes search the public World Wide Web or paid business databases. Otherwise, npm doesn't buy or receive data about you from data brokers or other private services.

​	在研究潜在客户时，npm员工有时会搜索公共互联网或付费商业数据库。否则，npm不会从数据经纪人或其他私人服务处购买或接收关于您的数据。

npm may inadvertently collect data about you if it is included in software packages that you or others upload.

​	如果您或其他人上传的软件包中包含您的数据，npm可能会无意中收集与您有关的数据。

## npm收集关于我的哪些数据，以及为什么？ What data does npm collect about me, and why?

### npm收集关于您如何使用npm软件和注册表的数据 npm collects data about how you use npm software and registries

When you use the `npm` command, the `npx` command, or other software to work with the npm public registry, an Enterprise registry that npm hosts, or private packages, npm logs data that might be identified to you:

​	当您使用 `npm` 命令、 `npx` 命令或其他软件与npm公共注册表、npm托管的企业注册表或私有软件包进行交互时，npm会记录可能与您相关的数据：

- a random, unique identifier, called `npm-session`, for each time you run commands like `npm install`
- 每次运行 `npm install` 等命令时，为您生成一个随机的唯一标识符 `npm-session` 
- the names and versions of your project's dependencies, their dependencies, and so on, that come from the npm public registry, [but not of other dependencies, like Git dependencies](https://docs.npmjs.com/cli/audit)
- 您的项目依赖项及其依赖项等的名称和版本，这些依赖项来自npm公共注册表，[但不包括其他依赖项，如Git依赖项](https://docs.npmjs.com/cli/audit)
- the versions of Node.js, the npm command, and the operating system you are using
- 您使用的Node.js版本、npm命令版本和操作系统版本
- an `npm-in-ci` header, showing whether the command was run on a continuous integration server
- 一个 `npm-in-ci` 头，显示命令是否在持续集成服务器上运行
- the scope of the package for which you ran `npm install`, as an `npm-scope` header
- 您运行 `npm install` 时的软件包范围，作为一个 `npm-scope` 头
- a `referrer` header that shows the command you ran, with any file or directory paths redacted
- 一个 `referrer` 头，显示您运行的命令，其中任何文件或目录路径都已删除
- data about the software you're using to access the registry, such as the `User-Agent` string
- 有关访问注册表的软件的数据，例如 `User-Agent` 字符串
- network request data, such as the date and time, your IP address, and the URL
- 网络请求数据，例如日期和时间、您的IP地址和URL

npm uses this data to:

​	npm使用这些数据来：

- fulfill your requests, such as by sending the packages you ask for
- 满足您的请求，例如发送您所请求的软件包
- send you alerts about security vulnerabilities that may affect the software you're building, when you run `npm install` or `npm audit`
- 当您运行 `npm install` 或 `npm audit` 时，向您发送有关可能影响您正在构建的软件的安全漏洞的警报
- keep registries working quickly and reliably
- 保持注册表的快速和可靠运行
- debug and develop the `npm` command and other software
- 调试和开发 `npm` 命令和其他软件
- defend registries from abuse and technical attacks
- 保护注册表免受滥用和技术攻击
- compile statistics on package usage and popularity
- 编译有关软件包使用和流行度的统计信息
- prepare reports on trends in the developer community
- 准备有关开发者社区趋势的报告
- improve search results on the website
- 改进网站上的搜索结果
- recommend packages that may be relevant to your work
- 推荐可能与您的工作相关的软件包

### npm收集关于您如何使用网站的数据 npm collects data about how you use the website

When you visit [www.npmjs.com](https://www.npmjs.com/), [docs.npmjs.com](https://docs.npmjs.com/), and other npm websites, npm uses cookies, server logs, and other methods to collect data about what pages you visit, and when. npm also collects technical information about the software and computer you use, such as:

​	当您访问[www.npmjs.com](https://www.npmjs.com/)、[docs.npmjs.com](https://docs.npmjs.com/)和其他npm网站时，npm使用cookie、服务器日志和其他方法收集关于您访问页面的数据以及访问时间。npm还收集有关您使用的软件和计算机的技术信息，例如：

- your IP address
- 您的IP地址
- your preferred language
- 您的首选语言
- the web browser software you use
- 您使用的Web浏览器软件
- the kind of computer you use
- 您使用的计算机类型
- the website that referred you
- 引荐您的网站

npm uses data about how you use the website to:

​	npm使用关于您如何使用网站的数据来：

- optimize the website, so that it's quick and easy to use
- 优化网站，使其快速和易于使用
- diagnose and debug technical errors
- 诊断和调试技术错误
- defend the website from abuse and technical attacks
- 保护网站免受滥用和技术攻击
- compile statistics on package popularity
- 编译有关软件流行度的统计信息
- compile statistics on the kinds of software and computers visitors use
- 编译有关访问者使用的软件和计算机类型的统计信息
- compile statistics on visitor searches and needs, to guide development of new website pages and functionality
- 编译有关访问者搜索和需求的统计信息，以指导新网页和功能的开发
- decide who to contact about about product announcements, service changes, and new features
- 决定谁可以联系您以进行产品公告、服务变更和新功能

### npm收集帐户数据 npm collects account data

Many features of npm services require an npm account. For example, you must have an npm account to publish packages to the npm public registry.

​	npm服务的许多功能都需要npm帐户。例如，要将软件包发布到npm公共注册表，您必须拥有一个npm帐户。

To create an npm account, npm requires a working email address and an available user name. npm uses this data to provide you access to features and identify you across npm services, publicly and within npm.

​	为了创建npm帐户，npm需要一个有效的电子邮件地址和一个可用的用户名。npm使用这些数据为您提供对功能的访问，并在npm服务内部和公开范围内识别您。

You do not have to give your personal or legal name to create an npm account. You can use a pseudonym instead. You can also open more than one account.

​	创建npm帐户时，您无需提供个人或法定姓名。您可以使用化名。您也可以打开多个帐户。

If you sign up for an account, then npm will publish account data for the whole world to see on user pages [like this one](https://www.npmjs.com/~kemitchell). npm also publishes account data through the npm public registry, which is available for everyone to see, and Enterprise registries that npm hosts for others to find with commands like npm owner ls tap.

​	如果您注册了一个帐户，那么npm将公开发布整个世界都可以看到的帐户数据，例如在用户页面上[像这个页面](https://www.npmjs.com/~kemitchell)。npm还通过npm公共注册表发布帐户数据，供所有人查看，以及通过npm托管的企业注册表供其他人使用类似npm owner ls tap的命令查找。

If you give npm a personal name or names on social media like [GitHub](https://github.com/) and [Twitter](https://twitter.com/) through the website, like when you include this on your profile or user page, npm publishes that data along with the email address and user name for the account. You don't have to give npm a personal name or any social media names, and you can remove this data at any time by updating your user page.

​	如果您在网站上通过社交媒体（例如[GitHub](https://github.com/)和[Twitter](https://twitter.com/)）提供了个人名称或名称，例如在个人资料或用户页面上包含这些信息，npm将与帐户的电子邮件地址和用户名一起发布这些数据。您无需提供个人名称或任何社交媒体名称，您可以随时通过更新用户页面来删除这些数据。

npm uses your email to:

​	npm使用您的电子邮件来：

- notify you about packages published using your account
- 通知您有关使用您的帐户发布的软件包
- reset your password and help keep your account secure
- 重置您的密码并帮助保护您的帐户安全
- add metadata to packages that you publish
- 为您发布的软件包添加元数据
- contact you in special circumstances related to your account or packages
- 与您联系，处理与您的帐户或软件包相关的特殊情况
- contact you about support requests
- 与您联系，处理支持请求
- contact you about legal requests, like DMCA takedown requests and privacy complaints
- 与您联系，处理法律请求，例如DMCA撤销请求和隐私投诉
- announce new npm product offerings, service changes, and features
- 宣布新的npm产品提供、服务变更和功能
- send you tips about how to better use free and paid services
- 向您发送有关如何更好地使用免费和付费服务的提示
- send you messages about paid services you might want
- 向您发送有关您可能感兴趣的付费服务的消息

### npm收集软件包数据 npm collects package data

When you use npm publish or other software to publish packages to the npm public registry, an Enterprise registry that npm hosts, or as a private package, npm collects the contents of the package, plus [metadata](https://en.wikipedia.org/wiki/Metadata), including your account data. Other npm users may also publish packages that include data about you, such as the fact that you contributed code to a package.

​	当您使用npm publish或其他软件将软件包发布到npm公共注册表、npm托管的企业注册表或作为私有软件包时，npm会收集软件包的内容以及包括您的帐户数据在内的[元数据](https://en.wikipedia.org/wiki/Metadata)。其他npm用户也可能发布包含有关您的数据的软件包，例如您为某个软件包贡献了代码的事实。

npm uses data in packages to provide those packages to you and others who request them:

​	npm使用软件包中的数据向您和其他请求这些软件包的用户提供这些软件包：

- When you publish a package to the npm public registry, or change a package from private to public, npm makes the package and metadata available to everyone, online.
- 当您将软件包发布到npm公共注册表或将软件包从私有更改为公共时，npm会使软件包和元数据对每个人在线可用。
- When you publish a package to an Enterprise registry that npm hosts, or as a private package, npm makes all of that data available to other users according to how the registry or the private packages account is configured. You may be able to configure who can access the package, or that may be up to others, such as the administrator of your company's Enterprise registry.
- 当您将软件包发布到npm托管的企业注册表或作为私有软件包时，npm会根据注册表或私有软件包帐户的配置使所有这些数据对其他用户可见。您可以配置谁可以访问软件包，或者可能由其他人决定，例如您公司的企业注册表管理员。

Making package data available to others allows them to download, build on, and depend on your work.

​	将软件包数据提供给其他人使他们能够下载、构建和依赖于您的工作。

### npm收集支付卡数据 npm collects payment card data

To sign up for paid services, npm requires your payment card data. npm itself does not collect or store enough information to charge your card itself. Rather, [Stripe](https://stripe.com/) collects that data on npm's behalf, and gives npm security tokens that allow npm to create charges and subscriptions.

​	要注册付费服务，npm需要您的支付卡数据。npm本身不会收集或存储足够的信息来直接向您的卡收费。相反，[Stripe](https://stripe.com/)代表npm收集这些数据，并提供给npm安全令牌，允许npm创建收费和订阅。

npm uses your payment card data only to charge for npm services.

​	npm仅使用您的支付卡数据来收取npm服务的费用。

npm instructs [Stripe](https://stripe.com/) to store your payment card data only as long as you use paid npm services.

​	npm指示[Stripe](https://stripe.com/)仅在您使用付费npm服务时存储您的支付卡数据。

### npm收集有关通讯的数据 npm collects data about correspondence

npm collects data about you when you send npm support requests, legal complaints, privacy inquiries, and business inquiries. Those data usually include your name and email address, and may include your company or other affiliation.

​	当您向npm发送支持请求、法律投诉、隐私查询和商业查询时，npm会收集有关您的数据。这些数据通常包括您的姓名和电子邮件地址，可能还包括您的公司或其他关联。

npm uses contact data to:

​	npm使用联系数据来：

- respond to you
- 回复您
- compile aggregate statistics about correspondence
- 编译有关通信的汇总统计信息
- train support staff and other npm personnel
- 培训支持人员和其他npm员工
- review the performance of npm personnel who respond
- 审查回应的npm员工的表现
- defend npm from legal claims
- 保护npm免受法律索赔的侵害

### npm收集有关npm.community使用的数据 npm collects data about use of npm.community

npm collects data about visits, user accounts, and forum data on [npm.community](https://npm.community/), the discussion forum for users of npm products and services. npm uses data from npm.community to collaborate with the development community, and to inform development decisions about the command-line interface and other software.

​	npm收集有关在[npm.community](https://npm.community/)上的访问、用户帐户和论坛数据的数据，该论坛是npm产品和服务的用户的讨论论坛。npm使用npm.community的数据与开发社区合作，并为命令行界面和其他软件的开发决策提供信息。

## npm是否与其他人共享我的数据？ Does npm share data about me with others?

npm shares account data with others as [mentioned in the section about account data](#account-data).

​	npm将帐户数据与其他人共享，如[关于帐户数据的部分所述](#account-data)。

npm shares package data with others as [mentioned in the section about package data](privacy#package-data).

​	npm将软件包数据与其他人共享，如[关于软件包数据的部分所述](privacy#package-data)。

npm publishes posts and other content you submit to [npm.community](https://npm.community/).

​	npm会发布您在[npm.community](https://npm.community/)上提交的帖子和其他内容。

npm does not sell information about you to others. However, npm uses services provided by other companies to provide npm services. The types of service providers that npm uses include:

​	npm不会将您的信息出售给其他人。但是，npm使用其他公司提供的服务来提供npm服务。npm使用的服务提供商类型包括：

- Companies that enable us to offer features on our website, such as to display your avatar
- 允许我们在网站上提供功能的公司，例如显示您的头像的公司
- Companies that facilitate the efficient distribution of content
- 用于有效分发内容的公司
- Cloud computing platforms and services that host our discussion forums
- 托管我们的讨论论坛的云计算平台和服务
- Services that assist with the detection of spam, scams, abuse others, or other violations of our [terms of service](https://docs.npmjs.com/policies/privacy)
- 协助检测垃圾邮件、欺诈、滥用或其他违反我们的[服务条款](https://docs.npmjs.com/policies/privacy)的行为的服务
- Payment processors
- 付款处理器
- Platforms to help us receive, manage, and respond to support requests
- 用于接收、管理和回应支持请求的平台
- Platforms for internal communication
- 用于内部沟通的平台

### npm使用cookie - npm uses cookies

npm's website only uses cookies strictly necessary to provide, optimize and secure the website. For example, we use them to keep you logged in, remember your preferences, authenticate your device for security purposes, analyze your use of the service, compile statistical reports, and provide information for future development of npm. The website uses internal cookies for analytics purposes, not any third-party analytics or service providers.

​	npm的网站仅使用严格必要的cookie来提供、优化和保护网站。例如，我们使用cookie使您保持登录状态，记住您的偏好设置，对您的设备进行身份验证以确保安全，分析您对服务的使用情况，编制统计报告，并为未来的npm开发提供信息。网站使用内部cookie进行分析目的，而不是任何第三方分析或服务提供商。

By using the website, you agree that we can place these types of cookies on your computer or device. If you disable your browser or device’s ability to accept these cookies, you will not be able to log in or use the website.

​	通过使用该网站，您同意我们可以将这些类型的cookie放置在您的计算机或设备上。如果您禁用浏览器或设备接受这些cookie的功能，您将无法登录或使用该网站。

## 如何选择数据收集？ How can I make choices about data collection?

You choose what data the npm publish command includes in package data. You can use an [.npmignore](https://docs.npmjs.com/files/package.json#files) file in your package to keep specific files out of the package. You can also use a [files list in package.json files](https://docs.npmjs.com/files/package.json#files) to instruct npm to include only specific files that you name, in addition to standard files like `README` files, `LICENSE` files, and package.json.

​	您可以选择npm publish命令在软件包数据中包含哪些数据。您可以在软件包中使用.npmignore文件来排除特定文件。您还可以使用package.json文件中的文件列表，以指示npm仅包含您命名的特定文件，以及标准文件（如README文件、LICENSE文件和package.json）。

To double check the data that you will share in a package that you plan to publish, run the `npm publish --dry-run` command. If you are running an older version of the npm command, run the npm pack command to create a [tarball](https://en.wikipedia.org/wiki/Tar_(computing)), then check its contents, such as with `tar tvzf $tarball`.

要查看您计划发布的软件包中将共享的数据，请运行`npm publish --dry-run`命令进行确认。如果您使用的是较旧版本的npm命令，请使用npm pack命令创建tarball，然后检查其内容，例如使用`tar tvzf $tarball`命令。

To publish a package to the npm public registry, npm's terms of service require you to [license npm to share it](https://docs.npmjs.com/policies/open-source-terms#your-content)). If a package is made public, it is available for everyone online to see. However, your [choice of public license for your package](https://docs.npmjs.com/files/package.json#license) may affect what others can do with data about you in your package.

​	要将软件包发布到npm公共注册表，npm的服务条款要求您[授权npm共享](https://docs.npmjs.com/policies/open-source-terms#your-content)。如果软件包是公开的，任何人都可以在线查看。但是，您对软件包的[公共许可选择](https://docs.npmjs.com/files/package.json#license)可能会影响他人对软件包中关于您的数据的使用。

npm does not respond to the [Do Not Track HTTP header](https://en.wikipedia.org/wiki/Do_Not_Track).

​	npm不会响应[Do Not Track HTTP header](https://en.wikipedia.org/wiki/Do_Not_Track)。

## npm将我的数据存储在哪里？ Where does npm keep data about me?

npm stores account data, data about website use, data about registry use, and private packages on servers in the United States of America. metadata about those packages worldwide, via content delivery networks.

​	npm将关于您的帐户数据、网站使用数据、注册表使用数据和私有软件包数据存储在美国的服务器上。它通过内容分发网络在全球范围内存储有关这些软件包的元数据。

npm stores package data published to Enterprise registries that npm hosts, plus metadata about them, in cloud computing zones of customers' choosing.

​	npm将发布到npm托管的企业注册表的软件包数据以及与之相关的元数据存储在客户选择的云计算区域。

By using the npm platform, you consent to the collection and storage of your data as outlined in this section.

​	通过使用npm平台，您同意按照本节中概述的方式收集和存储您的数据。

## npm如何处理欧盟《通用数据保护条例》下的数据？ How does npm handle data under the EU General Data Protection Regulation?

npm respects privacy rights under [Regulation (EU) 2016/679](http://eur-lex.europa.eu/legal-content/EN/TXT/?uri=uriserv:OJ.L_.2016.119.01.0001.01.ENG), the European Union's General Data Protection Regulation (GDPR). npm processes "Personal Data" on the following legal bases: (1) with your consent; (2) as necessary to perform our agreement to provide our services; and (3) as necessary for our legitimate interests in providing our services where those interests do not override your fundamental rights and freedom related to data privacy. Information we collect may be transferred to, and stored and processed in, the United States or any other country in which we or our affiliates or subcontractors maintain facilities, as described above.

​	npm尊重欧盟[Regulation (EU) 2016/679](http://eur-lex.europa.eu/legal-content/EN/TXT/?uri=uriserv:OJ.L_.2016.119.01.0001.01.ENG)即欧盟的《通用数据保护条例》（GDPR）下的隐私权利。npm根据以下法律依据处理“个人数据”：(1) 得到您的同意；(2) 在提供我们的服务的协议中必要时；(3) 在提供我们的服务的合法利益中，前提是这些利益不超过您与数据隐私相关的基本权利和自由。我们收集的信息可能会转移到我们或我们的关联公司或分包商维护设施所在的美国或任何其他国家进行存储和处理，如上文所述。

If you reside in the EEA, Switzerland, or United Kingdom, you are entitled to certain rights, like the right to:

​	如果您居住在欧洲经济区（EEA）、瑞士或英国，您有特定的权利，例如：

- complain about our data collection or processing actions with the supervisor authority concerned. You can find a list of data protection authorities [here](http://ec.europa.eu/justice/data-protection/bodies/authorities/index_en.htm).
- 向有关监管机构投诉我们的数据收集或处理行为。您可以在[此处](http://ec.europa.eu/justice/data-protection/bodies/authorities/index_en.htm)找到数据保护机构的列表。
- access to information held about you.
- 访问关于您的信息。
- ask us to correct or amend inaccurate or incomplete information we have about you.
- 要求我们更正或修正我们对您的不准确或不完整的信息。
- ask us to erase data that under certain circumstances, like (1) when it is no longer necessary for the purpose for which it was collected, (2) you withdraw consent and no other legal basis for processing exists, or (3) you believe your fundamental rights to data privacy and protection outweigh our legitimate interest in continuing the processing.
- 要求我们删除数据，在某些情况下，例如：(1) 数据不再为收集目的所必需，(2) 您撤回同意且没有其他合法的处理基础，或者(3) 您认为您的数据隐私和保护的基本权利超过我们继续处理的合法利益。
- request that we restrict our processing if we are processing your data based on legitimate interests or the performance of a task in the public interest as an exercise of official authority (including profiling); using your data for direct marketing (including profiling); or processing your data for purposes of scientific or historical research and statistics.
- 要求我们限制处理，如果我们基于合法利益或公共利益履行任务（包括个人资料）的处理；将您的数据用于直接营销（包括个人资料）；或者将您的数据用于科学或历史研究和统计目的。

When you exercise your rights, npm may need to verify your identity and provide us with information before we access records containing your information. If you want to exercise your rights, please contact npm by [opening a support ticket](https://npmjs.com/support). We may have a reason under the law why we do not have to comply with your request or may comply with it in a more limited way than you anticipated. If we do, we will explain that to you in our response.

​	当您行使您的权利时，npm可能需要验证您的身份并在访问包含您信息的记录之前向我们提供信息。如果您想行使您的权利，请通过[提交支持工单](https://npmjs.com/support)与npm联系。根据法律的规定，我们可能有理由不必遵守您的请求，或者以比您预期更有限的方式来遵守。如果是这样，我们将在回复中向您解释。

## npm如何处理加利福尼亚消费者隐私法下的数据？ How does npm handle data under the California Consumer Privacy Act?

npm respects the rights of California residents under the [California Consumer Privacy Act](https://www.oag.ca.gov/privacy/ccpa) (CCPA). Where we collect information that is subject to the CCPA, that information we collect and your rights are described below.

​	npm尊重[《加利福尼亚消费者隐私法》](https://www.oag.ca.gov/privacy/ccpa)（CCPA）下加利福尼亚居民的权利。我们收集适用于CCPA的信息，我们收集的信息和您的权利如下所述。

Categories of personal information we collect:

​	我们收集的个人信息类别：

- *Personal Identifiers*:
- *个人识别信息*：
  - Name and email address when you create an account. You will also be asked to create a username and we will assign one or more unique identifiers to your profile. We use this information to provide our services, respond to your requests, and send information to you.
  - 创建帐户时的姓名和电子邮件地址。您还将被要求创建用户名，我们将为您的个人资料分配一个或多个唯一标识符。我们使用此信息为您提供服务、回应您的请求并向您发送信息。
  - We also collect your social media handle and basic account information if you provide it to us or interact with our services, such as our help desk, through social media.
  - 如果您向我们提供或通过社交媒体与我们的服务进行交互（例如通过社交媒体在我们的帮助台上留言），我们还会收集您的社交媒体账户和基本账户信息。
  - We collect your payment information through our service provider, Stripe, as described above.
  - 我们通过我们的服务提供商Stripe收集您的付款信息，如上所述。
- *Internet or Other Electronic Network Activity Information*: device identifiers such as IP address and user agent; the assigned unique IDs in cookies (as described below); information about how you arrived at and navigated through our Services.
- *互联网或其他电子网络活动信息*：设备标识符，如IP地址和用户代理；在cookie中分配的唯一标识符；有关您如何访问和浏览我们的服务的信息。
- *Geolocation Data:* We do not collect your specific longitude and latitude. However, we do collect imprecise location (e.g., your IP address).
- *地理位置数据*：我们不会收集您的具体经纬度。然而，我们会收集不精确的位置信息（例如，您的IP地址）。
- *Professional or employment-related information:* If you apply for employment with us, information about your employment history.
- *与职业或就业相关的信息*：如果您申请就业，我们会收集有关您的就业历史的信息。
- *Education information:* If you apply for employment with us, information about your educational history.
- *教育信息*：如果您申请就业，我们会收集有关您的教育历史的信息。

We may collect any other information about you contained in software packages uploaded to our site, as described above under the "npm collects package data" section. We also collect the contents of your communications with us, e.g., when you submit a question to us through a web form or comments to us on social media.

​	我们可能会收集您在上传到我们网站的软件包中的任何其他关于您的信息，如上文“npm收集软件包数据”部分所述。我们还会收集您与我们的通信内容，例如您通过网络表单向我们提交问题或在社交媒体上向我们发表评论。

We may disclose any of the categories of personal information listed above and use them for the above-listed purposes or for other business or operational purposes compatible with the context in which the personal information was collected. Our disclosures of personal information include disclosures to our "service providers," which are companies that we engage for business purposes to conduct activities on our behalf. The categories of service providers with whom we share information and the services they provide are described below.

​	我们可能会披露上述任何个人信息的类别，并将其用于上述目的或与收集个人信息的背景相容的其他业务或运营目的。我们披露个人信息的对象包括我们的“服务提供商”，即我们委托从事业务目的的公司。我们与之共享信息的服务提供商类别及其提供的服务在下面描述。

Rights under CCPA:

CCPA下的权利：

- *Access/Right to Know*: You have the right to request access to personal information we collected about you and information regarding the source of that personal information, the purposes for which we collect it, and the third parties and service providers with whom we share it.
- *访问/知情权*：您有权要求访问我们收集的关于您的个人信息，以及有关该个人信息的来源、我们收集它的目的以及我们与之共享它的第三方和服务提供商的信息。
- *Deletion*: You have the right to request that we erase data we have collected from you. Please note that we may have a reason to deny your deletion request or delete data in a more limited way than you anticipated, e.g., because of a legal obligation to retain it.
- *删除*：您有权要求我们删除我们从您那里收集的数据。请注意，我们可能有理由拒绝您的删除请求或以比您预期更有限的方式删除数据，例如，因为有法律义务保留数据。

To exercise your rights above, you can [open a support ticket](https://npmjs.com/support). When we process your request, we must verify your identity by asking you to (1) provide personal identifiers that we can match against information we may have collected from you previously; and (2) confirm your request using the email stated in the request.

​	要行使上述权利，您可以通过[提交支持工单](https://npmjs.com/support)与我们联系。在处理您的请求时，我们必须通过要求您提供个人识别信息（我们可以将其与我们先前从您那里收集的信息进行匹配）来验证您的身份，并使用请求中提供的电子邮件进行确认。

Opt-out of sale:

退出销售：

California residents have the right to request that we stop "selling" their personal information. A "sale" of personal information is defined broadly: "selling, renting, releasing, disclosing, disseminating, making available, transferring, or otherwise communicating orally, in writing, or by electronic or other means, a consumer's personal information by the business to another business or a third party for monetary or other valuable consideration." We do not sell your information as defined by the CCPA.

​	加利福尼亚居民有权要求我们停止“销售”他们的个人信息。根据CCPA的定义，“销售”个人信息的范围很广：“将消费者的个人信息以金钱或其他有价值的对价出售、出租、披露、传播、提供、转让或以其他方式口头、书面、电子或其他方式向商业或第三方传达。”根据CCPA的定义，我们不会出售您的信息。

Please note that your right to opt out does not apply to our sharing of personal information with service providers, who are parties we engage to perform a function on our behalf and are contractually obligated to use the Personal Information only for that function.

​	请注意，您的选择退出不适用于我们与服务提供商共享个人信息，这些服务提供商是我们为业务目的而委托从事活动的方，他们在合同上承诺仅将个人信息用于该功能。

We may also disclose information to other entities who are not listed here when required by law or to protect our Company or other persons, as described in our Privacy Policy.

​	我们还可能在法律要求或保护我们公司或其他人的情况下向其他实体披露信息，如我们的隐私政策所述。

## 我如何查看关于我的公开数据？ How can I see what data is publicly available about me?

You can access your account data at any time by visiting your account page on [www.npmjs.com](https://www.npmjs.com/). Your account page also lists all the packages published under your account or other accounts.

​	您可以随时访问您的帐户数据，方法是访问[www.npmjs.com](https://www.npmjs.com/)上的帐户页面。您的帐户页面还列出了您的帐户或其他帐户下发布的所有软件包。

You can access package data by downloading the packages, as long as they're public or you have permission to access them.

​	您可以通过下载软件包来访问软件包数据，只要它们是公开的或您有权限访问它们。

You can see metadata about packages by running npm info $package, or by accessing the appropriate [registry's API](https://github.com/npm/registry/tree/master/docs). Registry APIs provide metadata in standard [JSON](https://www.json.org/) format, and packages as [tarballs](https://en.wikipedia.org/wiki/Tar_(computing)).

​	您可以通过运行npm info $package来查看软件包的元数据，或者通过访问适当的[注册表的API](https://github.com/npm/registry/tree/master/docs)。注册表API以标准的[JSON](https://www.json.org/)格式提供元数据，以[tarballs](https://en.wikipedia.org/wiki/Tar_(computing))形式提供软件包。

## 如何更改关于我的数据？ How can I change data about me?

You can change your personal account data and payment card data at any time by visiting your account settings page on [www.npmjs.com](https://www.npmjs.com/). You can change account and payment data for Enterprise by [contacting support](https://npmjs.com/support).

​	您可以随时访问您的个人帐户数据和付款卡数据，方法是访问[www.npmjs.com](https://www.npmjs.com/)上的帐户设置页面。您可以通过[联系支持](https://npmjs.com/support)更改企业帐户和付款数据。

You can close your npm account at any time by e-mailing [contacting support](https://npmjs.com/support). Closing your account removes the profile from the public registry but does not automatically erase packages published under your account. We may retain some data about you internally even where you close your account.

​	您可以随时通过发送电子邮件给[联系支持](https://npmjs.com/support)来关闭npm帐户。关闭帐户将从公共注册表中删除个人资料，但不会自动删除您发布的软件包。即使您关闭帐户，我们可能仍在内部保留与您有关的一些数据。

npm's [unpublish policy](https://docs.npmjs.com/policies/unpublish) determines when you can erase packages from the npm public registry. The unpublish policy strikes a difficult balance between the purpose of publishing and hosting packages, others' reliance on what has been made public, and individual rights and freedoms.

​	npm的[取消发布政策](https://docs.npmjs.com/policies/unpublish)决定了您何时可以从npm公共注册表中删除软件包。取消发布政策在发布和托管软件包的目的、他人对已公开内容的依赖以及个人权利和自由之间取得了艰难的平衡。

If another user improperly publishes personal data about you, in a package or otherwise, [open a support ticket](https://npmjs.com/support).

​	如果其他用户不当地发布了关于您的个人数据，无论是在软件包中还是其他方式，您可以[提交支持工单](https://npmjs.com/support)。

Please note that while [npm publishes notices about published data that's been erased](#erasure-notice), npm can't make everyone who has downloaded published package data or account data erase that data on your behalf. Choosing a public license, such as an open source software license, may encourage and allow storage, distribution, and use of package data indefinitely. Nearly all popular open source software licenses actually require preserving personal data that attributes the software to you, such as copyright notices, as a condition of permission for the software.

​	请注意，尽管[npm发布有关已删除的发布数据的通知](#erasure-notice)，但npm无法要求每个下载了已发布软件包数据或帐户数据的人代表您删除这些数据。选择公共许可证，如开源软件许可证，可能会鼓励和允许无限期地存储、分发和使用软件包数据。几乎所有流行的开源软件许可证实际上要求保留将软件归属于您的个人数据，如版权声明，作为软件使用许可的条件。

## npm对取消发布软件包的政策是什么？ What is npm's policy on unpublishing packages?

Please see [our policy on "unpublishing" packages](https://docs.npmjs.com/policies/unpublish) or [our terms of service](https://docs.npmjs.com/policies/open-source-terms) for more information on erasing packages.

​	有关删除软件包的更多信息，请参阅[我们关于“取消发布”软件包的政策](https://docs.npmjs.com/policies/unpublish)或[我们的服务条款](https://docs.npmjs.com/policies/open-source-terms)。

If you accidentally publish a package that threatens your privacy, or discover someone else has published a package that does, [open a support ticket](https://npmjs.com/support). npm can and will take down packages in specific, exceptional situations to protect you, especially if others violate your privacy. Using npm to violate others' privacy is against our [terms of service](https://docs.npmjs.com/policies/open-source-terms).

​	如果您意外地发布了威胁您隐私的软件包，或者发现其他人发布了威胁您隐私的软件包，您可以[提交支持工单](https://npmjs.com/support)。npm可以并且将在特定的、特殊的情况下撤下软件包，以保护您，特别是如果他人侵犯了您的隐私。使用npm来侵犯他人隐私违反了我们的[服务条款](https://docs.npmjs.com/policies/open-source-terms)。

## npm如何通知他人已删除的发布数据？ How does npm notify others about published data that's erased?

npm takes a few steps to notify others who may be copying data from the npm public registry that published data has been erased:

​	npm采取了几个步骤来通知可能正在从npm公共注册表复制数据的他人已删除的发布数据：

- npm publishes new placeholder versions of some erased packages, with `README` files that mention the package has been erased, and why.
- npm发布了一些被删除软件包的新占位符版本，其中包含提到该软件包已被删除以及原因的 `README` 文件。
- npm's [registry APIs](https://github.com/npm/registry/tree/master/docs), special software services that others use to copy data from the npm public registry, send update messages about packages that have been erased.
- npm的[注册表API](https://github.com/npm/registry/tree/master/docs)是其他人用来从npm公共注册表复制数据的特殊软件服务，它们会发送有关已删除软件包的更新消息。

## 如果npm与其他公司合并或被收购会发生什么？ What happens if npm merges with or is bought by another company?

We may transfer to another entity or its affiliates or service providers some or all information about you in connection with, or during negotiations of, any merger, acquisition, sale of assets or any line of business, change in ownership control, or financing transaction. We cannot promise that an acquiring party or the merged entity will have the same privacy practices or treat your information the same as described in this Policy.

​	在与其他公司的合并、收购、资产销售、业务线变更、所有权控制变更或融资交易的过程中，我们可能会将与您有关的一些或全部信息转移给另一个实体或其关联公司或服务提供商。我们不能保证收购方或合并实体将拥有与本政策中描述的隐私惯例相同的隐私惯例或对待您的信息相同。

## npm对待儿童信息的信息实践是什么？ What are npm's information practices regarding information belonging to children?

npm's site and services are intended for users age sixteen and older. npm does not knowingly collect information from children. If we discover that we have inadvertently collected information from anyone younger than the age of 16, we will delete that information.

​	npm的网站和服务面向16岁及以上的用户。npm不会有意收集儿童的信息。如果我们发现我们无意中收集了16岁以下的任何人的信息，我们将删除该信息。

## 我可以联系谁了解有关npm和我的隐私的信息？ Who can I contact about npm and my privacy?

Please [open a support ticket](https://npmjs.com/support). You may also contact our Data Protection Officer directly.

​	请[提交支持工单](https://npmjs.com/support)。您也可以直接联系我们的数据保护官员。

Our United States HQ:

我们的美国总部：

GitHub Data Protection Officer
Attention: npm Data Protection

注意：npm数据保护

88 Colin P. Kelly Jr. St.
San Francisco, CA 94107
United States

or our EU Office:

或者我们的欧盟办公室：

GitHub BV
Vijzelstraat 68-72
1017 HL Amsterdam
The Netherlands

荷兰

## 我如何了解有关变更的信息？ How can I find out about changes?

This version of npm's privacy questions and answers took effect June 3, 2020.

​	这个版本的npm隐私问题和答案于2020年6月3日生效。

npm will announce the next version on the [npm blog](https://blog.npmjs.org/). In the meantime, npm may update [its contact information](#contact) by updating the page at [https://docs.npmjs.com/privacy](https://docs.npmjs.com/policies/privacy), without an announcement. npm may change how it announces changes in future privacy versions.

​	npm将在[npm博客](https://blog.npmjs.org/)上宣布下一个版本。与此同时，npm可能会通过更新[其联系信息](#contact)来更新[https://docs.npmjs.com/privacy](https://docs.npmjs.com/policies/privacy)页面，而不需要宣布。npm可能会改变如何在未来的隐私版本中宣布变更。

You can review the history of changes in [the Git repository for npm's public policies](https://github.com/npm/documentation/blob/main/content/policies/privacy.mdx).

​	您可以在[npm公共政策的Git存储库](https://github.com/npm/documentation/blob/main/content/policies/privacy.mdx)中查看变更历史。
