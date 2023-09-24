+++
title = "验证 ECDSA 注册表签名"
date = 2023-09-22T20:59:52+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/verifying-registry-signatures](https://docs.npmjs.com/verifying-registry-signatures)

# Verifying ECDSA registry signatures - 验证 ECDSA 注册表签名

To ensure the integrity of packages you download from the public npm registry, or any registry that supports signatures, you can verify the registry signatures of downloaded packages using the npm CLI.

​	为了确保您从公共 npm 注册表或任何支持签名的注册表下载的包的完整性，您可以使用 npm CLI 验证已下载包的注册表签名。

## 先决条件 Prerequisites

1. Install npm CLI version v8.15.0 or later
2. 安装 npm CLI 的 v8.15.0 或更高版本
3. Install dependencies using `npm install` or `npm ci`
4. 使用  `npm install`  或  `npm ci`  安装依赖项

## 验证注册表签名 Verifying registry signatures

Registry signatures can be verified using the following `audit` command:

​	可以使用以下  `audit`  命令验证注册表签名：

```
npm audit signatures
```

Example response if all installed versions have valid registry signatures:

​	如果所有安装的版本都具有有效的注册表签名，则示例响应如下：

```
audited 1640 packages in 2s

1640 have verified registry signatures
```

## 故障排除 Troubleshooting

### 一些包缺少注册表签名 Some packages are missing registry signatures

The CLI will error if packages don't have signatures *and* if the package registry supports signatures. This could mean an attacker might be trying to circumvent signature verification. You can check if the registry supports signatures by requesting the public signing keys from `registry-host.tld/-/npm/v1/keys`.

​	如果包没有签名，并且包注册表支持签名，CLI 将报错。这可能意味着攻击者可能试图绕过签名验证。您可以通过从  `registry-host.tld/-/npm/v1/keys`  请求公共签名密钥来检查注册表是否支持签名。

Example response if some versions have missing registry signatures:

​	如果某些版本缺少注册表签名，则示例响应如下：

```
audited 1640 packages in 2s

1405 packages have verified registry signatures

235 packages have missing registry signatures but the registry is providing signing keys:

missing-dep@1.0.0 (https://registry.npmjs.org/)
...
```
