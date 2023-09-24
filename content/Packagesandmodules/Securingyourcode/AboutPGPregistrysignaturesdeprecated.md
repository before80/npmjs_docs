+++
title = "关于 PGP 注册表签名（已弃用）"
date = 2023-09-22T21:00:02+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/about-pgp-signatures-for-packages-in-the-public-registry](https://docs.npmjs.com/about-pgp-signatures-for-packages-in-the-public-registry)

# About PGP registry signatures (deprecated) - 关于 PGP 注册表签名（已弃用）

**Note:** PGP based registry signatures will be deprecated on **April 25th 2023** in favour of [ECDSA registry signatures](https://docs.npmjs.com/about-registry-signatures). This means no new packages will be signed with PGP keys from this date onwards and the [public key hosted on Keybase](https://keybase.io/npmregistry) will expire.

**注意：**基于 PGP 的注册表签名将于**2023年4月25日**停用，改为使用[ECDSA 注册表签名](https://docs.npmjs.com/about-registry-signatures)。这意味着从此日期开始，不会再使用 PGP 密钥对新的包进行签名，并且[在 Keybase 上托管的公共密钥](https://keybase.io/npmregistry)将过期。

To increase confidence in the npm public registry, we add our [PGP](https://en.wikipedia.org/wiki/Pretty_Good_Privacy) signature to package metadata and publicize our public PGP key on [Keybase](https://keybase.io). Our Keybase account is "[npmregistry](https://keybase.io/npmregistry)" and our public PGP key can be found at https://keybase.io/npmregistry/pgp_keys.asc

​	为了增加对 npm 公共注册表的信心，我们在包元数据中添加了我们的 [PGP](https://en.wikipedia.org/wiki/Pretty_Good_Privacy) 签名，并在 [Keybase](https://keybase.io) 上公开了我们的公共 PGP 密钥。我们的 Keybase 帐户是 "[npmregistry](https://keybase.io/npmregistry)"，我们的公共 PGP 密钥可以在 https://keybase.io/npmregistry/pgp_keys.asc 找到。

You can use the package PGP signature and our public PGP key to verify that the same entity who published the key (npm) also signed the package you downloaded from the npm public registry. For more information, see "[Verifying the PGP signature of a package from the npm public registry](verifying-the-pgp-signature-for-a-package-from-the-npm-public-registry)".

​	您可以使用包的 PGP 签名和我们的公共 PGP 密钥来验证从 npm 公共注册表下载的包是否由同一实体（npm）发布。有关更多信息，请参见 "[验证从 npm 公共注册表下载的包的 PGP 签名](verifying-the-pgp-signature-for-a-package-from-the-npm-public-registry)"。

## 我们使用的工具 Tools we use

### openpgpjs

To generate PGP signatures, we use [openpgpjs](https://github.com/openpgpjs/openpgpjs), a pure JavaScript implementation of OpenPGP. To learn more about openpgpjs, see https://openpgpjs.org/.

​	为了生成 PGP 签名，我们使用 [openpgpjs](https://github.com/openpgpjs/openpgpjs)，这是一个 OpenPGP 的纯 JavaScript 实现。要了解有关 openpgpjs 的更多信息，请参见 https://openpgpjs.org/。

### Keybase

We use Keybase to publicize our PGP key and give you confidence that the npm registry you install from is the same registry that signs packages.

​	我们使用 Keybase 来公开我们的 PGP 密钥，并让您对您安装的 npm 注册表与签名包的注册表是否相同有信心。

Keybase offers two advantages over the core OpenPGP experience that move us to recommend it to you:

​	与核心 OpenPGP 体验相比，Keybase 提供了两个优势，我们建议您使用它：

- The Keybase application and CLI provide an excellent user experience for PGP, which can be intimidating for newcomers.
- Keybase 应用程序和命令行界面为 PGP 提供了出色的用户体验，这对于新手来说可能是令人生畏的。
- Keybase manages and displays social proofs that the entity that controls a specific PGP key also controls accounts on social media and other places. These proofs help you determine whether you can trust an account.
- Keybase 管理和显示了社交证明，即控制特定 PGP 密钥的实体还控制着社交媒体和其他地方的帐户。这些证明有助于您确定是否可以信任一个帐户。

We’ve established proofs on Keybase that we control [@npmjs](https://twitter.com/npmjs) on Twitter, the domain [npmjs.com](https://npmjs.com), and the domain [npmjs.org](https://npmjs.org). Verifying these proofs won’t tell you who owns those domains, but it does establish that the same entity controls them, and the PGP key advertised on Keybase.

​	我们在 Keybase 上建立了我们控制 [@npmjs](https://twitter.com/npmjs) 的 Twitter 帐户、[npmjs.com](https://npmjs.com) 域和 [npmjs.org](https://npmjs.org) 域的证明。验证这些证明不会告诉您谁拥有这些域，但它确实证明了同一实体控制它们，并且在 Keybase 上宣传了 PGP 密钥。

If you install Keybase and create an account, you can follow npmregistry yourself and obtain a local copy of the registry’s public key. For more information, and to verify the PGP signature of a specific package version from the npm public registry, see "[Verifying the PGP signature for a package from the npm public registry](verifying-the-pgp-signature-for-a-package-from-the-npm-public-registry)".

​	如果您安装了 Keybase 并创建了一个帐户，您可以关注 npmregistry 并获取注册表的公共密钥的本地副本。有关更多信息，并验证从 npm 公共注册表中的特定包版本的 PGP 签名，请参见 "[验证从 npm 公共注册表下载的包的 PGP 签名](verifying-the-pgp-signature-for-a-package-from-the-npm-public-registry)"。
