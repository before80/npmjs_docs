+++
title = "解决全局安装软件包时的EACCES权限错误"
date = 2023-09-22T20:58:24+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally)

# Resolving EACCES permissions errors when installing packages globally - 解决全局安装软件包时的EACCES权限错误

If you see an `EACCES` error when you try to [install a package globally](downloading-and-installing-packages-globally), you can either:

​	如果在尝试[全局安装软件包](downloading-and-installing-packages-globally)时出现 `EACCES` 错误，您可以选择：

- Reinstall npm with a node version manager (recommended),

- 使用节点版本管理器重新安装npm（推荐），

  **or**

  或

- Manually change npm's default directory

- 手动更改npm的默认目录

## 使用节点版本管理器重新安装npm Reinstall npm with a node version manager

This is the best way to avoid permissions issues. To reinstall npm with a node version manager, follow the steps in "[Downloading and installing Node.js and npm](downloading-and-installing-node-js-and-npm)". You do not need to remove your current version of npm or Node.js before installing a node version manager.

​	这是避免权限问题的最佳方法。要使用节点版本管理器重新安装npm，请按照“[下载和安装Node.js和npm](downloading-and-installing-node-js-and-npm)”中的步骤进行操作。在安装节点版本管理器之前，您不需要删除当前版本的npm或Node.js。

## 手动更改npm的默认目录 Manually change npm's default directory

**Note:** This section does not apply to Microsoft Windows.

**注意：**此部分不适用于Microsoft Windows。

To minimize the chance of permissions errors, you can configure npm to use a different directory. In this example, you will create and use hidden directory in your home directory.

​	为了最大限度地减少权限错误的机会，您可以配置npm使用不同的目录。在此示例中，您将在主目录中创建和使用隐藏目录。

1. Back up your computer.

2. 备份计算机。

3. On the command line, in your home directory, create a directory for global installations:

4. 在命令行上，在主目录中创建一个全局安装的目录：

   ```
   mkdir ~/.npm-global
   ```

5. Configure npm to use the new directory path:

6. 配置npm以使用新的目录路径：

   ```
   npm config set prefix '~/.npm-global'
   ```

7. In your preferred text editor, open or create a `~/.profile` file and add this line:

8. 在您喜欢的文本编辑器中，打开或创建 `~/.profile` 文件，并添加以下行：

   ```
   export PATH=~/.npm-global/bin:$PATH
   ```

9. On the command line, update your system variables:

10. 在命令行上，更新系统变量：

   ```
   source ~/.profile
   ```

11. To test your new configuration, install a package globally without using `sudo`:

12. 要测试新的配置，请在不使用 `sudo` 的情况下全局安装一个软件包：

    ```
    npm install -g jshint
    ```

Instead of steps 3-5, you can use the corresponding ENV variable (e.g. if you don't want to modify `~/.profile`):

​	除了步骤3-5，您还可以使用相应的环境变量（例如，如果您不想修改 `~/.profile` ）：

```
NPM_CONFIG_PREFIX=~/.npm-global
```

**npx: an alternative to running global commands**

**npx：运行全局命令的另一种选择**

If you are using npm version 5.2 or greater, you may want to consider [npx](https://docs.npmjs.com/cli/commands/npx) as an alternative way to run global commands, especially if you only need a command occasionally. For more information, see [this article about npx](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b).

​	如果您使用的是npm 5.2或更高版本，您可能希望考虑使用[npx](https://docs.npmjs.com/cli/commands/npx)作为运行全局命令的替代方法，特别是如果您只偶尔需要一个命令。有关更多信息，请参阅[关于npx的文章](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b)。
