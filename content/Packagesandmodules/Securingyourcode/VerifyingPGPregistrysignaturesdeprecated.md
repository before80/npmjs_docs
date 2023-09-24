+++
title = "验证从 npm 公共注册表下载的包的 PGP 注册表签名（已弃用）"
date = 2023-09-22T21:00:10+08:00
weight = 60
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/verifying-the-pgp-signature-for-a-package-from-the-npm-public-registry](https://docs.npmjs.com/verifying-the-pgp-signature-for-a-package-from-the-npm-public-registry)

# Verifying the PGP registry signature of a package from the npm public registry (deprecated) - 验证从 npm 公共注册表下载的包的 PGP 注册表签名（已弃用）

**Note:** PGP based registry signatures will be deprecated on **April 25th 2023** in favour of [ECDSA registry signatures](https://docs.npmjs.com/about-registry-signatures). This means no new packages will be signed with PGP keys from this date onwards and the [public key hosted on Keybase](https://keybase.io/npmregistry) will expire.

**注意：**基于 PGP 的注册表签名将于**2023年4月25日**停用，改为使用[ECDSA 注册表签名](https://docs.npmjs.com/about-registry-signatures)。这意味着从此日期开始，不会再使用 PGP 密钥对新的包进行签名，并且[在 Keybase 上托管的公共密钥](https://keybase.io/npmregistry)将过期。

To ensure the integrity of a package version you download from the npm public registry, you can manually verify the [PGP signature](about-pgp-signatures-for-packages-in-the-public-registry) of the package.

​	为了确保您从 npm 公共注册表下载的包版本的完整性，您可以手动验证包的[PGP 签名](about-pgp-signatures-for-packages-in-the-public-registry)。

**Note:** Since fully verifying signatures on Keybase requires rechecking proofs (which requires network activity) and is therefore expensive, we recommend only verifying signatures if it is necessary -- for example, when verifying a deploy artifact, or when initially storing a package in your cache.

**注意：**由于在 Keybase 上完全验证签名需要重新检查证明（这需要网络活动），因此我们建议仅在必要时验证签名，例如在验证部署工件时或在初始存储包在缓存中时。

## 先决条件 Prerequisites

1. Install Keybase from https://keybase.io/download
2. 从 https://keybase.io/download 安装 Keybase
3. Create a Keybase account on https://keybase.io
4. 在 https://keybase.io 上创建一个 Keybase 帐户
5. Follow "[npmregistry](https://keybase.io/npmregistry)" on Keybase.
6. 在 Keybase 上关注 "[npmregistry](https://keybase.io/npmregistry)"
7. Download a local copy of the npm public registry's [public PGP key](https://keybase.io/npmregistry/pgp_keys.asc).
8. 下载 npm 公共注册表的[公共 PGP 密钥](https://keybase.io/npmregistry/pgp_keys.asc)的本地副本

## 验证公共注册表的 npm 签名 Verifying npm signatures for the public registry

**Note:** The following steps use version 1.4.3 of the `light-cycle` package as an example.

**注意：**以下步骤以版本 1.4.3 的  `light-cycle`  包为例。

1. On the command line, fetch the signature for the package version you want and save it in a file:

2. 在命令行中，获取您想要的包版本的签名并将其保存到一个文件中：

   ```
   npm view light-cycle@1.4.3 dist.npm-signature > sig-to-check
   ```

3. Get the integrity field for that version (example below includes response):

4. 获取该版本的完整性字段（下面的示例包括响应）：

   ```
   npm view light-cycle@1.4.3 dist.integrity
   ```

   Example response:

   示例响应：

   ```
   sha512-sFcuivsDZ99fY0TbvuRC6CDXB8r/ylafjJAMnbSF0y4EMM1/1DtQo40G2WKz1rBbyiz4SLAc3Wa6yZyC4XSGOQ==
   ```

5. Construct the string that ties the unique package name and version to the integrity string (example below includes response):

6. 构造将唯一的包名称和版本与完整性字符串关联的字符串（下面的示例包括响应）：

   ```
   keybase pgp verify --signed-by npmregistry -d sig-to-check -m 'light-cycle@1.4.3:sha512-sFcuivsDZ99fY0TbvuRC6CDXB8r/ylafjJAMnbSF0y4EMM1/1DtQo40G2WKz1rBbyiz4SLAc3Wa6yZyC4XSGOQ=='
   ```

   Example response:

   示例响应：

   ```
   ▶ INFO Identifying npmregistry
   ✔ public key fingerprint: 0963 1802 8A2B 58C8 4929 D8E1 3D4D 5B12 0276 566A
   ✔ admin of DNS zone npmjs.org: found TXT entry keybase-site-verification=Ls8jN55i6KesjiX91Ck79bUZ17eA-iohmw2jJFM16xc
   ✔ admin of DNS zone npmjs.com: found TXT entry keybase-site-verification=iK3pjpRBkv-CIJ4PHtWL4TTcFXMpPiwPynatKl3oWO4
   ✔ "npmjs" on twitter: https://twitter.com/npmjs/status/981288548845240320
   Signature verified. Signed by npmregistry 3 years ago (2018-04-13 15:00:37 -0700 MST).
   PGP Fingerprint: 096318028a2b58c84929d8e13d4d5b120276566a.
   ```
