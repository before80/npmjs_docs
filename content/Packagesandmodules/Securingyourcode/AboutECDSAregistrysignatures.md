+++
title = "About ECDSA registry signatures"
date = 2023-09-22T20:59:42+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false
+++

> 原文: [https://docs.npmjs.com/about-registry-signatures](https://docs.npmjs.com/about-registry-signatures)

# About ECDSA registry signatures - 关于ECDSA注册表签名

Packages published to the public npm registry are signed to make it possible to detect if the package content has been tampered with.

​	发布到公共npm注册表的软件包已签名，以便检测软件包内容是否被篡改。

Signing and verifying published packages protects against an attacker controlling a registry mirror or proxy where they attempt to intercept and tamper with the package tarball content.

​	签名和验证已发布的软件包可防止攻击者控制注册表镜像或代理，从而尝试拦截和篡改软件包tarball内容。

## 从PGP迁移到ECDSA签名 Migrating from PGP to ECDSA signatures

**Note:** PGP based registry signatures will be deprecated on **April 25th 2023** in favour of ECDSA registry signatures. This means no new packages will be signed with PGP keys from this date onwards and the [public key hosted on Keybase](https://keybase.io/npmregistry) will expire.

**注意：**在**2023年4月25日**之后，将停用基于PGP的注册表签名，改用ECDSA注册表签名。这意味着从此日期开始，不会使用PGP密钥对新软件包进行签名，并且[在Keybase上托管的公共密钥](https://keybase.io/npmregistry)将过期。

The public npm registry is migrating away from the existing PGP signatures to ECDSA signatures that are more compact and can be verified without extra dependencies in the npm CLI.

​	公共npm注册表正在从现有的PGP签名迁移到更紧凑且可以在npm CLI中无需额外依赖项进行验证的ECDSA签名。

Signature verification was previously a multi-step process involving the Keybase CLI, as well as manually retrieving and parsing the signature from the package metadata.

​	以前，验证签名是一个多步骤的过程，涉及到Keybase CLI，以及手动检索和解析软件包元数据中的签名。

Read more about [migrating and verifying signatures](https://docs.npmjs.com/verifying-registry-signatures) using the npm CLI.

​	使用npm CLI阅读有关[迁移和验证签名](https://docs.npmjs.com/verifying-registry-signatures)的更多信息。

## 支持第三方注册表上的签名 Supporting signatures on third-party registries

The npm CLI supports registry signatures and signing keys provided by any registry if the following conventions are followed:

​	如果遵循以下约定，npm CLI将支持任何注册表提供的注册表签名和签名密钥：

**1. Signatures are provided in the package's `packument` in each published version within the `dist` object:**

**1. 签名在每个发布版本的 `packument` 中以 `dist` 对象的形式提供：**

```
"dist":{
  ..omitted..,
  "signatures": [{
    "keyid": "SHA256:{{SHA256_PUBLIC_KEY}}",
    "sig": "a312b9c3cb4a1b693e8ebac5ee1ca9cc01f2661c14391917dcb111517f72370809..."
  }],
```

See this [example of a signed package from the public npm registry](https://registry.npmjs.org/light-cycle/1.4.3).

​	请参阅[来自公共npm注册表的已签名软件包示例](https://registry.npmjs.org/light-cycle/1.4.3)。

To generate the signature, sign the package name, version and tarball sha integrity: `${package.name}@${package.version}:${package.dist.integrity}`.

​	要生成签名，请签名软件包名称、版本和tarball的sha完整性： `${package.name}@${package.version}:${package.dist.integrity}` 。

The current best practice is to use a [Key Management System](https://en.wikipedia.org/wiki/Key_management#Key_management_system) that does the signing operation on a [Hardware Security Module (HSM)](https://en.wikipedia.org/wiki/Hardware_security_module) in order to not directly handle the private key part, which reduces the attack surface.

​	当前的最佳实践是使用[密钥管理系统](https://en.wikipedia.org/wiki/Key_management#Key_management_system)，该系统在[硬件安全模块（HSM）](https://en.wikipedia.org/wiki/Hardware_security_module)上执行签名操作，以便不直接处理私钥部分，从而减少攻击面。

The `keyid` must match one of the public signing keys below.

 	`keyid` 必须与下面的公共签名密钥之一匹配。

**2. Public signing keys are provided at `registry-host.tld/-/npm/v1/keys` in the following format:**

**2. 公共签名密钥以以下格式提供在 `registry-host.tld/-/npm/v1/keys` ：**

```
{
  "keys": [{
    "expires": null,
    "keyid": "SHA256:{{SHA256_PUBLIC_KEY}}",
    "keytype": "ecdsa-sha2-nistp256",
    "scheme": "ecdsa-sha2-nistp256",
    "key": "{{B64_PUBLIC_KEY}}"
  }]
}
```

Keys response:

密钥响应：

- `expires`: null or a simplified extended [ISO 8601 format](https://en.wikipedia.org/wiki/ISO_8601): `YYYY-MM-DDTHH:mm:ss.sssZ`
- `expires` ：null或简化的扩展[ISO 8601格式](https://en.wikipedia.org/wiki/ISO_8601)： `YYYY-MM-DDTHH:mm:ss.sssZ` 
- `keydid`: sha256 fingerprint of the public key
- `keydid` ：公钥的SHA256指纹
- `keytype`: only `ecdsa-sha2-nistp256` is currently supported by the npm CLI
- `keytype` ：npm CLI目前仅支持 `ecdsa-sha2-nistp256` 
- `scheme`: only `ecdsa-sha2-nistp256` is currently supported by the npm CLI
- `scheme` ：npm CLI目前仅支持 `ecdsa-sha2-nistp256` 
- `key`: base64 encoded public key
- `key` ：base64编码的公钥

See this [example key's response from the public npm registry](https://registry.npmjs.org/-/npm/v1/keys).

​	请参阅[来自公共npm注册表的示例密钥响应](https://registry.npmjs.org/-/npm/v1/keys)。
