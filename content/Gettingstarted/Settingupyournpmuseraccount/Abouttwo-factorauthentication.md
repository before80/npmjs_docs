+++
title = "关于双因素认证"
date = 2023-09-22T20:50:59+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/about-two-factor-authentication](https://docs.npmjs.com/about-two-factor-authentication)

# About two-factor authentication - 关于双因素认证

[Two-factor authentication (2FA)](https://en.wikipedia.org/wiki/Multi-factor_authentication) protects against unauthorized access to your account by confirming your identity using:

​	[双因素认证（2FA）](https://en.wikipedia.org/wiki/Multi-factor_authentication)通过以下方式确认您的身份，以防止未经授权访问您的账户：

- Something you know (e.g., a password).
- 您所知道的东西（例如密码）。
- Something you have (e.g., an ID badge or a cryptographic key).
- 您所拥有的东西（例如身份证或加密密钥）。
- Something you are (e.g., a fingerprint or other biometric data).
- 您所具备的特征（例如指纹或其他生物特征数据）。

When you enable 2FA, you will be prompted for a second form of authentication before performing certain actions on your account or packages to which you have write access. Depending on your 2FA configuration you will be either prompted to authenticate with a [security-key](https://webauthn.guide/) or a [time-based one-time password (TOTP)](https://en.wikipedia.org/wiki/Time-based_one-time_password).

​	当您启用2FA时，在执行某些账户或具有写入权限的软件包的操作之前，您将被要求进行第二次身份验证。根据您的2FA配置，您将被提示进行[安全密钥](https://webauthn.guide/)或[基于时间的一次性密码（TOTP）](https://en.wikipedia.org/wiki/Time-based_one-time_password)身份验证。

- The security-key flow allows you to use biometric devices such as Apple [Touch ID](https://support.apple.com/en-gb/HT204587), [Face ID](https://support.apple.com/en-us/HT208108) or [Windows Hello](https://support.microsoft.com/en-us/windows/learn-about-windows-hello-and-set-it-up-dae28983-8242-bb2a-d3d1-87c9d265a5f0) as well as physical keys such as [Yubikey](https://www.yubico.com/), [Thetis](https://thetis.io/) or [Feitian](https://www.ftsafe.com/) as your 2FA.
- 安全密钥流程允许您使用生物特征设备，如Apple的[Touch ID](https://support.apple.com/en-gb/HT204587)、[Face ID](https://support.apple.com/en-us/HT208108)或[Windows Hello](https://support.microsoft.com/en-us/windows/learn-about-windows-hello-and-set-it-up-dae28983-8242-bb2a-d3d1-87c9d265a5f0)，以及物理密钥，如[Yubikey](https://www.yubico.com/)、[Thetis](https://thetis.io/)或[Feitian](https://www.ftsafe.com/)作为您的2FA。
- To configure TOTP you will need to install an authenticator application that can generate OTPs such as [Authy](https://authy.com/download/), [Google Authenticator](https://support.google.com/accounts/answer/1066447), or [Microsoft Authenticator](https://www.microsoft.com/security/mobile-authenticator-app) on your mobile device.
- 要配置TOTP，您需要在移动设备上安装能够生成OTP的认证器应用程序，如[Authy](https://authy.com/download/)、[Google Authenticator](https://support.google.com/accounts/answer/1066447)或[Microsoft Authenticator](https://www.microsoft.com/security/mobile-authenticator-app)。

**Note:** Two-factor authentication provides the best possible security for your account against attackers. We strongly recommend enabling 2FA on your account as soon as possible after you sign up.

**注意：**双因素认证为您的账户提供了最佳的安全性保护，能够有效防御攻击者。我们强烈建议您在注册后尽快启用2FA。

## npm上的双因素认证 Two-factor authentication on npm

Two-factor authentication on npm can be enabled for authorization and writes, or authorization only.

​	npm上的双因素认证可以用于授权和写入，或仅用于授权。

### 授权和写入 Authorization and writes

By default, 2FA is enabled for authorization and writes. We will request a second form of authentication for certain authorized actions, as well as write actions.

​	默认情况下，2FA已启用授权和写入。对于某些授权操作和写入操作，我们将要求进行第二次身份验证。

| 操作                                                         | CLI命令                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 登录到npm                                                    | [ `npm login` ](https://docs.npmjs.com/cli/adduser)          |
| 更改个人资料设置（包括密码）                                 | [ `npm profile set` ](https://docs.npmjs.com/cli/profile)    |
| 更改用户账户的2FA模式                                        | [ `npm profile enable-2fa auth-and-writes` ](https://docs.npmjs.com/cli/profile) |
| 禁用用户账户的2FA                                            | [ `npm profile disable-2fa` ](https://docs.npmjs.com/cli/profile) |
| 创建令牌                                                     | [ `npm token create` ](https://docs.npmjs.com/cli/token)     |
| 撤销令牌                                                     | [ `npm token revoke` ](https://docs.npmjs.com/cli/token)     |
| 发布软件包                                                   | [ `npm publish` ](https://docs.npmjs.com/cli/publish)        |
| 取消发布软件包                                               | [ `npm unpublish` ](https://docs.npmjs.com/cli/unpublish)    |
| 废弃软件包                                                   | [ `npm deprecate` ](https://docs.npmjs.com/cli/deprecate)    |
| 更改软件包可见性                                             | [ `npm access public/restricted` ](https://docs.npmjs.com/cli/access) |
| 更改用户和团队对软件包的访问权限                             | [ `npm access grant/revoke` ](https://docs.npmjs.com/cli/access) |
| [更改软件包的2FA要求](https://docs.npmjs.com/requiring-2fa-for-package-publishing-and-settings-modification) | [ `npm access 2fa-required/2fa-not-required` ](https://docs.npmjs.com/cli/access) |

| Action                                                       | CLI command                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Log in to npm                                                | [`npm login`](https://docs.npmjs.com/cli/adduser)            |
| Change profile settings (including your password)            | [`npm profile set`](https://docs.npmjs.com/cli/profile)      |
| Change 2FA modes for your user account                       | [`npm profile enable-2fa auth-and-writes`](https://docs.npmjs.com/cli/profile) |
| Disable 2FA for your user account                            | [`npm profile disable-2fa`](https://docs.npmjs.com/cli/profile) |
| Create tokens                                                | [`npm token create`](https://docs.npmjs.com/cli/token)       |
| Revoke tokens                                                | [`npm token revoke`](https://docs.npmjs.com/cli/token)       |
| Publish packages                                             | [`npm publish`](https://docs.npmjs.com/cli/publish)          |
| Unpublish packages                                           | [`npm unpublish`](https://docs.npmjs.com/cli/unpublish)      |
| Deprecate packages                                           | [`npm deprecate`](https://docs.npmjs.com/cli/deprecate)      |
| Change package visibility                                    | [`npm access public/restricted`](https://docs.npmjs.com/cli/access) |
| Change user and team package access                          | [`npm access grant/revoke`](https://docs.npmjs.com/cli/access) |
| [Change package 2FA requirements](https://docs.npmjs.com/requiring-2fa-for-package-publishing-and-settings-modification) | [`npm access 2fa-required/2fa-not-required`](https://docs.npmjs.com/cli/access) |

### 仅授权 Authorization only

If you enable 2FA for authorization only. We will request a second form of authentication only for certain authorized actions.

​	如果您仅启用了授权的2FA，则只会在某些授权操作时要求进行第二次身份验证。

| 操作                         | CLI命令                                                      |
| ---------------------------- | ------------------------------------------------------------ |
| 登录到npm                    | [ `npm login` ](https://docs.npmjs.com/cli/adduser)          |
| 更改个人资料设置（包括密码） | [ `npm profile set` ](https://docs.npmjs.com/cli/profile)    |
| 更改用户账户的2FA模式        | [ `npm profile enable-2fa auth-only` ](https://docs.npmjs.com/cli/profile) |
| 禁用用户账户的2FA            | [ `npm profile disable-2fa` ](https://docs.npmjs.com/cli/profile) |
| 创建令牌                     | [ `npm token create` ](https://docs.npmjs.com/cli/token)     |
| 撤销令牌                     | [ `npm token revoke` ](https://docs.npmjs.com/cli/token)     |

| Action                                            | CLI command                                                  |
| ------------------------------------------------- | ------------------------------------------------------------ |
| Log in to npm                                     | [`npm login`](https://docs.npmjs.com/cli/adduser)            |
| Change profile settings (including your password) | [`npm profile set`](https://docs.npmjs.com/cli/profile)      |
| Change 2FA modes for your user account            | [`npm profile enable-2fa auth-only`](https://docs.npmjs.com/cli/profile) |
| Disable 2FA for your user account                 | [`npm profile disable-2fa`](https://docs.npmjs.com/cli/profile) |
| Create tokens                                     | [`npm token create`](https://docs.npmjs.com/cli/token)       |
| Revoke tokens                                     | [`npm token revoke`](https://docs.npmjs.com/cli/token)       |
