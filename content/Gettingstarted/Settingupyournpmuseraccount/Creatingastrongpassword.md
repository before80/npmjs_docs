+++
title = "创建一个强密码"
date = 2023-09-22T20:50:41+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/creating-a-strong-password](https://docs.npmjs.com/creating-a-strong-password)

# Creating a strong password - 创建一个强密码

Secure your npm account with a strong and unique password using a password manager.

​	使用密码管理器为您的npm账户选择或生成一个强大且独特的密码。

You must choose or generate a password for your npm account that:

​	您必须为npm账户选择或生成一个满足以下条件的密码：

- is longer than 10 characters
- 长度超过10个字符
- does not match or significantly contain your username, e.g. do not use 'username123'
- 不与您的用户名匹配或包含过多的用户名信息，例如不要使用'username123'
- has not been compromised and known to the [Have I Been Pwned](https://haveibeenpwned.com/) breach database
- 未被泄露且未出现在[Have I Been Pwned](https://haveibeenpwned.com/)的泄露数据库中

To keep your account secure, we recommend you follow these best practices:

​	为保护您的账户安全，我们建议您遵循以下最佳实践：

- Use a password manager, such as [1Password](https://1password.com/), to generate a password more than 16 characters.
- 使用密码管理器，例如[1Password](https://1password.com/)，生成一个超过16个字符的密码。
- Generate a unique password for npm. If you use your npm password elsewhere and that service is compromised, then attackers or other malicious actors could use that information to access your npm account.
- 为npm生成一个独特的密码。如果您在其他地方使用了相同的npm密码，并且该服务出现了安全问题，攻击者或其他恶意行为者可能会利用这些信息来访问您的npm账户。
- Configure two-factor authentication for your account. For more information, see "About two-factor authentication."
- 为您的账户配置双因素认证。有关更多信息，请参阅“关于双因素认证”。
- Never share your password, even with a potential collaborator. Each person should use their own personal account on npm. For more information on ways to collaborate, see: "[npm organizations](https://docs.npmjs.com/organizations)".
- 永远不要分享您的密码，即使是给潜在的合作者。每个人都应该使用自己的个人npm账户。有关协作方式的更多信息，请参阅：“[npm组织](https://docs.npmjs.com/organizations)”。

When you type a password to sign in, create an account, or change your password, npm will check if the password you entered is considered weak according to datasets like HaveIBeenPwned. The password may be identified as weak even if you have never used that password before.

​	当您输入密码进行登录、创建账户或更改密码时，npm将检查您输入的密码是否被认为是弱密码，根据像HaveIBeenPwned这样的数据集。即使您以前从未使用过该密码，它也可能被识别为弱密码。

npm only inspects the password at the time you type it, and never stores the password you entered in plaintext. For more information, see [HaveIBeenPwned](https://haveibeenpwned.com/).

​	npm仅在您输入密码时检查密码，从不以明文形式存储您输入的密码。有关更多信息，请参阅[HaveIBeenPwned](https://haveibeenpwned.com/)。
