+++
title = "关于审计报告"
date = 2023-09-22T20:59:11+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/about-audit-reports](https://docs.npmjs.com/about-audit-reports)

# About audit reports - 关于审计报告

Audit reports contain tables of information about security vulnerabilities in your project's dependencies to help you fix the vulnerability or troubleshoot further.

​	审计报告包含有关项目依赖项中安全漏洞的信息表，以帮助您修复漏洞或进一步进行故障排除。

![Screenshot showing command-line audit report results](Aboutauditreports_img/audit-report-results.png)

## 漏洞表字段 Vulnerability table fields

### 严重程度 Severity

The severity of the vulnerability, determined by the impact and exploitability of the vulnerability in its most common use case.

​	漏洞的严重程度，由漏洞在其最常见用例中的影响和可利用性确定。

| 严重程度 | 推荐操作     |
| -------- | ------------ |
| 严重     | 立即处理     |
| 高       | 尽快处理     |
| 中等     | 根据时间处理 |
| 低       | 由您自行决定 |

| Severity | Recommended action             |
| -------- | ------------------------------ |
| Critical | Address immediately            |
| High     | Address as quickly as possible |
| Moderate | Address as time allows         |
| Low      | Address at your discretion     |

#### 描述 Description

The description of the vulnerability. For example, "Denial of service".

漏洞的描述。例如，“拒绝服务”。

#### 软件包 Package

The name of the package that contains the vulnerability.

​	包含漏洞的软件包的名称。

#### 已修复版本 Patched in

The semantic version range that describes which versions contain a fix for the vulnerability.

​	描述包含漏洞修复的语义版本范围。

#### 依赖于 Dependency of

The module that the package with the vulnerability depends on.

​	具有漏洞的软件包依赖的模块。

#### 路径 Path

The path to the code that contains the vulnerability.

​	包含漏洞的代码的路径。

#### 更多信息 More info

A link to the security report.

​	指向安全报告的链接。
