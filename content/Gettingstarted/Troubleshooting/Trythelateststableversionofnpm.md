+++
title = "尝试最新稳定版本的npm"
date = 2023-09-22T20:54:01+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/try-the-latest-stable-version-of-npm](https://docs.npmjs.com/try-the-latest-stable-version-of-npm)

# Try the latest stable version of npm - 尝试最新稳定版本的npm

## 查看您正在运行的npm版本 See what version of npm you're running



```
npm -v
```

## 在 `*nix` （OSX，Linux等）上升级 Upgrading on `*nix` (OSX, Linux, etc.)

*(You may need to prefix these commands with `sudo`, especially on Linux, or OS X if you installed Node using its default installer.)*

*（您可能需要在这些命令前加上 `sudo` ，特别是在Linux上，或者如果您使用默认安装程序安装Node的OS X上。）*

You can upgrade to the latest version of npm using:

​	您可以使用以下命令升级到最新版本的npm：

```
npm install -g npm@latest
```

## 在Windows上升级 Upgrading on Windows

By default, npm is installed alongside node in

​	默认情况下，npm与node一起安装在以下位置：

```
C:\Program Files (x86)\nodejs
```

npm's globally installed packages (including, potentially, npm itself) are stored separately in a user-specific directory (which is currently

​	npm的全局安装软件包（包括可能的npm本身）单独存储在一个特定于用户的目录中（目前是

`C:\Users\<username>\AppData\Roaming\npm`).

Because the installer puts

​	因为安装程序将

```
C:\Program Files (x86)\nodejs
```

before

放在

```
C:\Users\<username>\AppData\Roaming\npm
```

on your `PATH`, it will always use the version of npm installed with node instead of the version of npm you installed using `npm -g install npm@<version>`.

之前的 `PATH` 中，它总是使用与node一起安装的npm版本，而不是使用 `npm -g install npm@<version>` 安装的npm版本。

To get around this, you can do **one** of the following:

​	为了解决这个问题，您可以选择**以下任一**方法：

- Option 1: [edit your Windows installation's `PATH`](http://superuser.com/questions/284342/what-are-path-and-other-environment-variables-and-how-can-i-set-or-use-them) to put `%appdata%\npm` before `%ProgramFiles%\nodejs`. Remember that you'll need to restart `cmd.exe` (and potentially restart Windows) when you make changes to `PATH` or how npm is installed.
- 选项1：[编辑Windows安装的 `PATH` ](http://superuser.com/questions/284342/what-are-path-and-other-environment-variables-and-how-can-i-set-or-use-them)，将 `%appdata%\npm` 放在 `%ProgramFiles%\nodejs` 之前。请记住，在更改 `PATH` 或npm的安装方式时，您需要重新启动 `cmd.exe` （可能需要重新启动Windows）。
- Option 2: remove both of
- 选项2：删除以下两个文件
  - `%ProgramFiles%\nodejs\npm`
  - `%ProgramFiles%\nodejs\npm.cmd`
- Option 3: Navigate to `%ProgramFiles%\nodejs\node_modules\npm` and copy the `npmrc`file to another folder or the desktop. Then open `cmd.exe` as an administrator and run the following commands:
- 选项3：导航至 `%ProgramFiles%\nodejs\node_modules\npm` ，并将 `npmrc` 文件复制到另一个文件夹或桌面。然后以管理员身份打开 `cmd.exe` 并运行以下命令：

```bash
cd %ProgramFiles%\nodejs
npm install npm@latest
```

If you installed npm with the node.js installer, after doing one of the previous steps, do the following.

​	如果您使用node.js安装程序安装了npm，请在执行上述步骤之后执行以下操作。

- Option 1 or 2
- 选项1或2
  - Go into `%ProgramFiles%\nodejs\node_modules\npm` and copy the file named `npmrc` in the new npm folder, which should be `%appdata%\npm\node_modules\npm`. This will tell the new npm where the global installed packages are.
  - 进入 `%ProgramFiles%\nodejs\node_modules\npm` ，并将名为 `npmrc` 的文件复制到新的npm文件夹中，该文件夹应为 `%appdata%\npm\node_modules\npm` 。这将告诉新的npm全局安装的软件包的位置。
- Option 3
- 选项3
  - Copy the npmrc file back into `%ProgramFiles%\nodejs\node_modules\npm`
  - 将npmrc文件复制回 `%ProgramFiles%\nodejs\node_modules\npm` 

*(See also the [point below](https://docs.npmjs.com/common-errors#error-enoent-stat-cusersuserappdataroamingnpm-on-windows-7) if you're running Windows 7 and don't have the directory `%appdata%\npm`.)*

（如果您运行Windows 7且没有 `%appdata%\npm` 目录，请参阅[下面的说明](https://docs.npmjs.com/common-errors#error-enoent-stat-cusersuserappdataroamingnpm-on-windows-7)。）

### 关于内置Windows配置的简要说明 A brief note on the built-in Windows configuration

The Node installer installs, directly into the npm folder, a special piece of Windows-specific configuration that tells npm where to install global packages. When npm is used to install itself, it is supposed to copy this special `builtin` configuration into the new install. There was a bug in some versions of npm that kept this from working, so you may need to go in and fix that up by hand. Run the following command to see where npm will install global packages to verify it is correct.

​	Node安装程序直接将一个特殊的Windows特定配置安装到npm文件夹中，该配置告诉npm在哪里安装全局软件包。当使用npm安装自身时，它应该将此特殊的“内置”配置复制到新的安装中。在某些npm版本中存在错误，导致此过程无法正常工作，因此您可能需要手动修复它。运行以下命令以查看npm将全局软件包安装到的位置，以验证其是否正确。

```
npm config get prefix -g
```

If it isn't set to `<X>:\Users\<user>\AppData\Roaming\npm`, you can run the below command to correct it:

​	如果它没有设置为 `<X>:\Users\<user>\AppData\Roaming\npm` ，您可以运行以下命令进行更正：

```
npm config set prefix %APPDATA%\npm -g
```

Incidentally, if you would prefer that packages not be installed to your roaming profile (because you have a quota on your shared network, or it makes logging in or out from a domain sluggish), you can put it in your local app data instead:

​	顺便说一下，如果您希望软件包不安装到漫游配置文件中（因为共享网络上有配额，或者从域登录或注销变得缓慢），您可以将其放在本地应用程序数据中：

```
npm config set prefix %LOCALAPPDATA%\npm -g
```

...as well as copying `%APPDATA%\npm` to `%LOCALAPPDATA%\npm` (and updating your `%PATH%`, of course).

...并将 `%APPDATA%\npm` 复制到 `%LOCALAPPDATA%\npm` （当然还要更新 `%PATH%` ）。

Everyone who works on npm knows that this process is complicated and fraught, and we're working on making it simpler. Stay tuned.

​	每个在npm上工作的人都知道这个过程是复杂而麻烦的，我们正在努力使其变得更简单。敬请关注。
