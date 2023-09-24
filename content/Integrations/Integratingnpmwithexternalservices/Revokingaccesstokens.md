+++
title = "撤销访问令牌"
date = 2023-09-22T21:01:02+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/revoking-access-tokens](https://docs.npmjs.com/revoking-access-tokens)

# Revoking access tokens - 撤销访问令牌

To keep your account and packages secure, we strongly recommend revoking (deleting) tokens you no longer need or that have been compromised. You can revoke any token you have created.

​	为了保护您的账户和软件包的安全，我们强烈建议撤销（删除）您不再需要或已经被泄露的令牌。您可以撤销任何您创建的令牌。

1. To see a list of your tokens, on the command line, run:

2. 在命令行上，运行以下命令以查看您的令牌列表：

   ```
   npm token list
   ```

3. In the tokens table, find and copy the ID of the token you want to delete.

4. 在令牌列表中，找到并复制您想要删除的令牌的ID。

5. On the command line, run the following command, replacing `123456` with the ID of the token you want to delete:

6. 在命令行上，运行以下命令，并将 `123456` 替换为您想要删除的令牌的ID：

   ```
   npm token delete 123456
   ```

   npm will report `Removed 1 token`

   npm将报告 `Removed 1 token` 

7. To confirm that the token has been removed, run:

8. 为了确认令牌已被删除，运行以下命令：

   ```
   npm token list
   ```

**Note:** You must use the token ID to delete a token, not the truncated version of the token. In some cases, there may be a delay of up to an hour before a token is successfully revoked.

**注意：**您必须使用令牌ID来删除令牌，而不是令牌的截断版本。在某些情况下，令牌成功撤销可能需要最多一个小时的延迟时间。
