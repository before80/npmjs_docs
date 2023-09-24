+++
title = "生成溯源声明"
date = 2023-09-22T20:59:34+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/generating-provenance-statements](https://docs.npmjs.com/generating-provenance-statements)

# Generating provenance statements - 生成溯源声明

You can generate provenance statements for the packages you publish. This allows you to publicly establish where a package was built and who published a package, which can increase supply-chain security for your packages.

​	您可以为您发布的软件包生成溯源声明。这样可以公开确立软件包的构建位置和发布者，从而提高软件包的供应链安全性。

## 关于npm溯源 About npm provenance

npm provenance includes two types of attestations:

​	npm溯源包括两种类型的证明：

- Provenance attestation
- 溯源证明
- Publish attestation
- 发布证明

The provenance attestation is established by publicly providing a link to a package's source code and build instructions from the build environment. This allows developers to verify where and how your package was built before they download it.

​	溯源证明是通过公开提供软件包的源代码和构建环境中的构建说明来确立的。这使开发人员在下载软件包之前可以验证软件包在哪里以及如何构建。

Publish attestations are generated by the registry when a package is published by an authorized user. When an npm package is published with provenance, it is signed by Sigstore public good servers and logged in a public transparency ledger, where users can view this information.

​	当通过授权用户发布npm软件包时，注册表会生成发布证明。当使用溯源发布npm软件包时，它会由Sigstore公共服务器进行签名，并在公共透明账本中记录，用户可以在其中查看此信息。

### 关于Sigstore About Sigstore

Sigstore is a collection of tools and services aimed at making it easy to use short-lived, ephemeral certificates to sign software. Its three main components are a CLI tool, a certificate authority, and a time-stamping transparency log.

​	Sigstore是一个旨在使用短暂的、临时的证书对软件进行签名的工具和服务集合。它的三个主要组成部分是CLI工具、证书颁发机构和时间戳透明日志。

The certificate authority federates with any OIDC provider that includes verifiable build information. It acts as an intermediary between build systems and package registries by verifying the integrity of the OIDC token, issues a signing certificate that contains that build information, and then logging the signing certificate to an immutable ledger.

​	证书颁发机构与包含可验证构建信息的任何OIDC提供程序进行联合。它充当构建系统和软件包注册表之间的中间人，通过验证OIDC令牌的完整性，发放包含该构建信息的签名证书，然后将签名证书记录到不可变账本中。

The transparency log service provides a public, verifiable, tamper-evident ledger of signed attestations. This ensures transparency of the public service, as well as providing a way to detect attempts to tamper with a package if a package registry were to be compromised.

​	透明日志服务提供了一个公共的、可验证的、防篡改的签名证明账本。这确保了公共服务的透明性，并提供了一种方式来检测对软件包的篡改企图，如果软件包注册表被攻破的话。

## 溯源的限制 Provenance limitations

- In order to publish a package with provenance, you must build your package with a supported cloud CI/CD provider using a cloud-hosted runner from a public source repository. Today this includes GitHub Actions and GitLab CI, and we are collaborating with additional providers to expand support. For more information on how to establish provenance using GitHub Actions, see "[Publishing packages with provenance via GitHub Actions](#publishing-packages-with-provenance)."
- 要发布带有溯源的软件包，您必须使用支持的云CI/CD提供商在公共源代码仓库中使用云托管运行器构建软件包。目前包括GitHub Actions和GitLab CI，我们正在与其他提供商合作扩大支持范围。有关如何使用GitHub Actions建立溯源的更多信息，请参见“[通过GitHub Actions发布具有溯源的软件包](#通过GitHub Actions发布软件包)。”
- When a package in the npm registry has established provenance, it does not guarantee the package has no malicious code. Instead, npm provenance provides a verifiable link to the package's source code and build instructions, which developers can then audit and determine whether to trust it or not. For more information, see "[Searching for and choosing packages to download](https://docs.npmjs.com/searching-for-and-choosing-packages-to-download#package-provenance)."
- 当npm注册表中的软件包建立了溯源时，并不保证该软件包没有恶意代码。相反，npm溯源提供了一个可验证的链接到软件包的源代码和构建说明，开发人员可以审核并确定是否信任它。有关更多信息，请参见“[搜索和选择要下载的软件包](https://docs.npmjs.com/searching-for-and-choosing-packages-to-download#package-provenance)”。

## 先决条件 Prerequisites

Before you can publish your packages with provenance, you must:

​	在使用溯源发布您的软件包之前，您必须：

- Review the [Linux Foundation Immutable Record notice](https://lfprojects.org/policies/hosted-project-tools-immutable-records/), which applies to the public transparency log.
- 查看[Linux Foundation不可变记录通知](https://lfprojects.org/policies/hosted-project-tools-immutable-records/)，该通知适用于公共透明日志。
- Install the latest version of the npm CLI (ensure you are on `9.5.0+` as older versions don't support npm provenance). For more information, see "[Try the latest stable version of npm](https://docs.npmjs.com/try-the-latest-stable-version-of-npm)."
- 安装最新版本的npm CLI（确保您使用的是 `9.5.0+` 版本，因为旧版本不支持npm溯源）。有关更多信息，请参见“[尝试最新稳定版本的npm](https://docs.npmjs.com/try-the-latest-stable-version-of-npm)”。
- Ensure your `package.json` is configured with a public `repository` that matches where you are publishing with provenance from.
- 确保您的 `package.json` 配置了一个公共的 `repository` ，与您使用溯源发布的位置相匹配。
- Set up a GitHub Actions workflow to publish your packages to the npm registry. For more information, see [Understanding GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions) in the GitHub documentation.
- 设置一个GitHub Actions工作流，将您的软件包发布到npm注册表。有关更多信息，请参阅GitHub文档中的[了解GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)。

## 通过GitHub Actions发布带有溯源的软件包 Publishing packages with provenance via GitHub Actions

In order to establish provenance, you must use a supported cloud CI/CD provider and a cloud-hosted runner to publish your packages. GitHub Actions is a supported CI/CD platform that allows you to automate software development tasks. For more information, see [GitHub Actions](https://docs.github.com/en/actions) in the GitHub documentation.

​	为了确立溯源，您必须使用支持的云CI/CD提供商和云托管运行器来发布您的软件包。GitHub Actions是一个支持的CI/CD平台，允许您自动化软件开发任务。有关更多信息，请参阅GitHub文档中的[GitHub Actions](https://docs.github.com/en/actions)。

To update your GitHub Actions workflow to publish your packages with provenance, you must:

​	要更新您的GitHub Actions工作流程以使用溯源发布您的软件包，您必须：

- Give permission to mint an ID-token:

- 授予mint ID令牌的权限：

  ```yaml
  permissions:
    id-token: write
  ```
  
- Run on a [GitHub-hosted runner](https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners#supported-runners-and-hardware-resources):

- 在[GitHub托管的运行器](https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners#supported-runners-and-hardware-resources)上运行：

  ```yaml
  runs-on: ubuntu-latest
  ```
  
- Add the `--provenance` flag to your publish command:

- 在发布命令中添加 `--provenance` 标志：

  ```sh
  npm publish --provenance
  ```
  
- If you are publishing a package for the first time you will also need to explicitly set access to public:

- 如果您首次发布软件包，您还需要明确设置访问权限为公共：

  ```sh
  npm publish --provenance --access public
  ```

### 示例GitHub Actions工作流程 Example GitHub Actions workflow

This example workflow publishes a package to the npm registry with provenance.

​	此示例工作流程将一个软件包发布到npm注册表，并带有溯源。

```yaml
name: Publish Package to npmjs
on:
  release:
    types: [created]
jobs:
  build:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      id-token: write
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18.x'
          registry-url: 'https://registry.npmjs.org'
      - run: npm install -g npm
      - run: npm ci
      - run: npm publish --provenance --access public
        env:
          NODE_AUTH_TOKEN: ${{ secrets.NPM_TOKEN }}
```

### 示例GitLab CI作业 Example GitLab CI job

This example job publishes a package to the npm registry with provenance when a git tag is pushed. Don’t forget to define the `NPM_TOKEN` variable in your GitLab project settings.

​	此示例作业在推送git标签时将软件包发布到npm注册表，并带有溯源。不要忘记在GitLab项目设置中定义 `NPM_TOKEN` 变量。

```yaml
publish:
  image: 'node:20'
  rules:
    - if: $CI_COMMIT_TAG
  id_tokens:
    SIGSTORE_ID_TOKEN:
      aud: sigstore
  script:
    - npm config set //registry.npmjs.org/:_authToken "$NPM_TOKEN"
    - npm publish --provenance --access public
```

### 使用第三方软件包发布工具 Using third-party package publishing tools

If you publish your packages with tools that do not directly invoke the `npm publish` command, you can do one of the following in your GitHub Actions workflow to publish your packages with provenance.

​	如果您使用的是未直接调用 `npm publish` 命令的工具来发布软件包，您可以在GitHub Actions工作流中执行以下操作，以使用溯源发布您的软件包。

- **Configure environment variables:** In your GitHub Actions workflow, you can use an environment variable called `NPM_CONFIG_PROVENANCE`, and set it to `true`.

- **配置环境变量：**在GitHub Actions工作流中，您可以使用一个名为 `NPM_CONFIG_PROVENANCE` 的环境变量，并将其设置为 `true` 。

- Configure your `package.json` file:

- 配置您的 `package.json` 文件： 

  You can add a `publishConfig` block to your `package.json` file:

  您可以在您的 `package.json` 文件中添加一个

  ```json
"publishConfig": {
    "provenance": true
  },
  ```

- Add an `.npmrc` file:

- 添加一个 `.npmrc` 文件： 

  You can add an `.npmrc` file to your project with the following entry:

  您可以在您的项目中添加一个 `.npmrc` 文件，并包含以下条目：

  ```ini
  provenance=true
  ```

**Note:** At this time, `yarn` is not a supported tool for publishing your packages with provenance.

**注意：**目前， `yarn` 不是一个支持溯源发布软件包的工具。