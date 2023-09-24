+++
title = "威胁和缓解措施"
linkTitle = "威胁和缓解措施"
date = 2023-09-22T21:09:40+08:00
type = "docs"
description = ""
isCJKLanguage = true
draft = false
[menu.main]
    weight = 60

+++

> 原文: [https://docs.npmjs.com/threats-and-mitigations](https://docs.npmjs.com/threats-and-mitigations)

# npm: Threats and Mitigations - npm：威胁和缓解措施

We put together this page to give an overview of the most common attacks npm faces, a high-level description of how we mitigate those attacks, and links to more information.

​	我们整理了这个页面，以概述npm面临的最常见攻击，对如何缓解这些攻击进行高级描述，并提供更多信息的链接。

## 账号劫持 Account Takeovers

### 通过破解密码 By compromising passwords

This is the most common attack, not just on npm but on any web service. The best way to protect your account is to [enable two-factor authentication](https://docs.npmjs.com/configuring-two-factor-authentication) (2FA). The strongest option is to use a security-key, either built-in to your device or an external hardware key; it binds the authentication to the site you are accessing, making phishing exceedingly difficult. Not everyone has access to a security-key though, so we also support authentication apps that generate one-time passcodes for 2FA.

​	这是最常见的攻击方式，不仅针对npm，而且针对任何网络服务。保护您的账号的最佳方法是[启用双因素身份验证](https://docs.npmjs.com/configuring-two-factor-authentication)（2FA）。最强大的选项是使用安全密钥，可以是内置在您的设备中的密钥，也可以是外部硬件密钥；它将身份验证绑定到您访问的站点，使钓鱼攻击变得非常困难。然而，并不是每个人都能获得安全密钥，因此我们还支持生成一次性验证码的身份验证应用程序用于2FA。

Because of how common this attack is, and how critical npm packages are to the broader software ecosystem, we have undertaken a phased approach in mandating 2FA for npm package maintainers. This has already rolled out to the [top-100 package maintainers](https://github.blog/2022-02-01-top-100-npm-package-maintainers-require-2fa-additional-security/) and [top-500 package maintainers](https://github.blog/changelog/2022-05-31-top-500-npm-package-maintainers-now-require-2fa/), and in the near future, maintainers of all high-impact packages (those with 1 million+ weekly downloads or 500+ dependents) will be enrolled in mandatory 2FA.

​	由于这种攻击方式非常常见，并且npm软件包对更广泛的软件生态系统至关重要，我们采取了分阶段的方法来要求npm软件包维护者使用2FA。这已经在[前100个软件包维护者](https://github.blog/2022-02-01-top-100-npm-package-maintainers-require-2fa-additional-security/)和[前500个软件包维护者](https://github.blog/changelog/2022-05-31-top-500-npm-package-maintainers-now-require-2fa/)中推出，并且在不久的将来，所有高影响力软件包的维护者（每周下载量超过100万或依赖超过500个）将被强制参加2FA。

We also recognize that passwords aren’t going away any time soon. For users that don’t opt-in to 2FA, we do an enhanced login verification with a [one-time password sent to their email](https://docs.npmjs.com/receiving-a-one-time-password-over-email) to protect from account takeover.

​	我们也认识到，密码在短期内不会消失。对于不选择2FA的用户，我们会通过[将一次性密码发送到他们的电子邮件](https://docs.npmjs.com/receiving-a-one-time-password-over-email)进行增强的登录验证，以防止账号劫持。

### 通过注册一个过期的电子邮件域 By registering an expired email domain

Another method used to take over an account is by identifying accounts using an expired domain for their email address. An attacker could register the expired domain and recreate the email address used to register the account. With access to an account's registered email address an attacker could take over an account not protected by 2FA via a password reset.

​	劫持账号的另一种方法是通过识别使用过期域名作为电子邮件地址的账号。攻击者可以注册过期的域名并重新创建用于注册账号的电子邮件地址。通过访问账号的注册电子邮件地址，攻击者可以接管未受2FA保护的账号，通过密码重置来实现。

When a package is published the email address associated with the account, **at the time the package was published**, is included in the public metadata. Attackers are able to utilize this public data to identify accounts that might be susceptible to account takeover. It is important to note that the **email addresses stored in public metadata of packages are not updated when a maintainer updates their email address**. As such crawling public metadata to identify accounts susceptible to expired domain takeover will result in false positives, accounts that appear to be vulnerable but are not.

​	当发布一个软件包时，与账号相关联的电子邮件地址，即**在软件包发布时的那个时间点**，会包含在公共元数据中。攻击者可以利用这些公共数据来识别可能容易受到账号劫持攻击的账号。重要的是要注意，**在维护者更新他们的电子邮件地址时，软件包的公共元数据中的电子邮件地址不会更新**。因此，通过爬取公共元数据来识别容易受到过期域名劫持的账号将导致误报，即看起来容易受攻击但实际上不容易受攻击的账号。

npm does periodically check if accounts email addresses have expired domains or invalid MX records. When the domain has expired, we disable the account from doing a password reset and require the user to undergo account recovery or go through a successful authentication flow before they can reset their password.

​	npm会定期检查账号的电子邮件地址是否包含过期的域名或无效的MX记录。当域名过期时，我们会禁用账号进行密码重置，并要求用户在重置密码之前进行账号恢复或通过成功的身份验证流程。

## 上传恶意软件包 Uploading Malicious Packages

### 通过"typosquatting" / 依赖混淆 By "typosquatting" / dependency confusion

Attackers may attempt to trick others into installing a malicious package by registering a package with a similar name to a popular package, in hopes that people will mistype or otherwise confuse the two. npm is able to detect typosquat attacks and block the publishing of these packages.

​	攻击者可能尝试通过注册一个与流行软件包名称相似的软件包来欺骗他人安装恶意软件包，希望人们会输错或混淆两者。npm能够检测到typosquat攻击并阻止这些软件包的发布。

A variant of this attack is when a public package is registered with the same name of a private package that an organization is using. We strongly encourage using [scoped packages](https://github.blog/2021-02-12-avoiding-npm-substitution-attacks/) to ensure that a private package isn’t being substituted with one from the public registry. While npm is not able to detect dependency confusion attacks we have a zero tolerance for malicious packages on the registry. If you believe you have identified a dependency confusion package, [please let us know](https://docs.npmjs.com/reporting-malware-in-an-npm-package)!

​	这种攻击的变体是当一个公共软件包使用与组织正在使用的私有软件包相同的名称进行注册。我们强烈建议使用[作用域包](https://github.blog/2021-02-12-avoiding-npm-substitution-attacks/)来确保私有软件包不会被公共注册表中的软件包替代。虽然npm无法检测到依赖混淆攻击，但我们对注册表上的恶意软件包持零容忍态度。如果您认为发现了依赖混淆软件包，请[告诉我们](https://docs.npmjs.com/reporting-malware-in-an-npm-package)！

### 通过更改现有软件包的恶意行为 By changing an existing package to have malicious behavior

Rather than tricking people into using a similarly-named package, attackers also try to add malicious behavior to existing popular packages. In partnership with Microsoft, npm both scans packages for known malicious content, and runs the packages to look for new patterns of behavior that could be malicious. This has led to a substantial reduction in malicious content in npm packages. Furthermore, our Trust and Safety team checks and removes malicious content reported by our users. Similar to dependency confusion attacks, we are constantly updating our detection services with new examples, so if you think a package contains malicious behavior, [please let us know](https://docs.npmjs.com/reporting-malware-in-an-npm-package)!

​	攻击者不仅试图诱使人们使用同名软件包，还试图向现有的流行软件包添加恶意行为。npm与微软合作，对软件包进行已知恶意内容的扫描，并运行软件包以寻找可能是恶意的新行为模式。这已经大大减少了npm软件包中恶意内容的数量。此外，我们的信任与安全团队会检查并删除用户报告的恶意内容。与依赖混淆攻击类似，我们不断更新我们的检测服务，提供新的示例。因此，如果您认为一个软件包包含恶意行为，请[告诉我们](https://docs.npmjs.com/reporting-malware-in-an-npm-package)！
