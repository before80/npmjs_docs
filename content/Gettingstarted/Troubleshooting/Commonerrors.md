+++
title = "常见错误"
date = 2023-09-22T20:53:38+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/common-errors](https://docs.npmjs.com/common-errors)

# Common errors - 常见错误

## 损坏的npm安装 Broken npm installation

If your npm is broken:

​	如果您的npm损坏：

- On Mac or Linux, [reinstall npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
- 在Mac或Linux上，[重新安装npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)。
- Windows: If you're on Windows and you have a broken installation, the easiest thing to do is to reinstall node from the official installer (see [this note about installing the latest stable version](try-the-latest-stable-version-of-npm#upgrading-on-windows)).
- Windows：如果您在Windows上安装损坏，最简单的方法是从官方安装程序重新安装node（有关安装最新稳定版本的说明，请参见[此说明](try-the-latest-stable-version-of-npm#upgrading-on-windows)）。

## 随机错误 Random errors

- Some strange issues can be resolved by simply running `npm cache clean` and trying again.
- 一些奇怪的问题可以通过运行 `npm cache clean` 并重试来解决。
- If you are having trouble with `npm install`, use the `-verbose` option to see more details.
- 如果您在使用 `npm install` 时遇到问题，请使用 `-verbose` 选项查看更多详细信息。

## 找不到兼容的版本 No compatible version found

You have an outdated npm. [Please update to the latest stable npm](try-the-latest-stable-version-of-npm).

​	您的npm版本过旧。[请更新到最新稳定版本的npm](try-the-latest-stable-version-of-npm)。

## 权限错误 Permissions errors

Please see the discussions in "[Downloading and installing Node.js and npm](downloading-and-installing-node-js-and-npm)" and "[Resolving EACCES permissions errors when installing packages globally](resolving-eacces-permissions-errors-when-installing-packages-globally)" for ways to avoid and resolve permissions errors.

​	请参阅“[下载和安装Node.js和npm](downloading-and-installing-node-js-and-npm)”和“[解决全局安装软件包时的EACCES权限错误](resolving-eacces-permissions-errors-when-installing-packages-globally)”中的讨论，以避免和解决权限错误。

## Windows 7上的 `Error: ENOENT, stat 'C:\Users\<user>\AppData\Roaming\npm'`   `Error: ENOENT, stat 'C:\Users\<user>\AppData\Roaming\npm'` on Windows 7

The error `Error: ENOENT, stat 'C:\Users\<user>\AppData\Roaming\npm'` on Windows 7 is a consequence of [joyent/node#8141](https://github.com/joyent/node/issues/8141), and is an issue with the Node installer for Windows. The workaround is to ensure that `C:\Users\<user>\AppData\Roaming\npm` exists and is writable with your normal user account.

​	在Windows 7上出现 `Error: ENOENT, stat 'C:\Users\<user>\AppData\Roaming\npm'` 错误是因为[joyent/node#8141](https://github.com/joyent/node/issues/8141)引起的，这是Node Windows安装程序的问题。解决方法是确保 `C:\Users\<user>\AppData\Roaming\npm` 存在并且可由您的普通用户账户进行写入。

## 没有空间 No space



```
npm ERR! Error: ENOSPC, write
```

You are trying to install on a drive that either has no space, or has no permission to write.

​	您正在尝试在没有空间或没有写入权限的驱动器上进行安装。

- Free some disk space or
- 释放一些磁盘空间或
- Set the tmp folder somewhere with more space: `npm config set tmp /path/to/big/drive/tmp` or
- 将临时文件夹设置为具有更多空间的位置： `npm config set tmp /path/to/big/drive/tmp`  或
- Build Node yourself and install it somewhere writable with lots of space.
- 自己构建Node并将其安装在具有大量空间的可写位置。

## 没有git No git



```
npm ERR! not found: git
ENOGIT
```

You need to [install git](http://git-scm.com/book/en/Getting-Started-Installing-Git). Or, you may need to add your git information to your npm profile. You can do this from the command line or the website. For more information, see "[Managing your profile settings](managing-your-profile-settings)".

​	您需要[安装git](http://git-scm.com/book/en/Getting-Started-Installing-Git)。或者，您可能需要在npm配置文件中添加git信息。您可以在命令行或网站上执行此操作。有关更多信息，请参见“[管理个人资料设置](managing-your-profile-settings)”。

## 在Windows上运行Vagrant虚拟机失败，由于路径长度问题 Running a Vagrant box on Windows fails due to path length issues

**[@drmyersii](https://github.com/drmyersii)** went through what sounds like a lot of painful trial and error to come up with a working solution involving Windows long paths and some custom Vagrant configuration:

**[@drmyersii](https://github.com/drmyersii)** 经历了很多痛苦的试错才找到了一个解决方案，涉及到Windows长路径和一些自定义的Vagrant配置：

> [This is the commit that I implemented it in](https://github.com/renobit/vagrant-node-env/commit/bdf15f2f301e2b1660b839875e34f172ea8be227), but I'll go ahead and post the main snippet of code here:
>
> ​	[这是我实现它的提交](https://github.com/renobit/vagrant-node-env/commit/bdf15f2f301e2b1660b839875e34f172ea8be227)，但我将在此处发布主要的代码片段：
>
> ```ruby
> config.vm.provider "virtualbox" do |v|
>  v.customize ["sharedfolder", "add", :id, "--name", "www", "--hostpath", (("//?/" + File.dirname(__FILE__) + "/www").gsub("/","\\"))]
> end
> 
> config.vm.provision :shell, inline: "mkdir /home/vagrant/www"
> config.vm.provision :shell, inline: "mount -t vboxsf -o uid=`id -u vagrant`,gid=`getent group vagrant | cut -d: -f3` > www /home/vagrant/www", run: "always"
> ```
>
> In the code above, I am appending `\\?\` to the current directory absolute path. This will actually force the Windows API to allow an increase in the MAX_PATH variable (normally capped at 260). Read more about [max path](https://msdn.microsoft.com/en-us/library/windows/desktop/aa365247(v=vs.85).aspx#maxpath). This is happening during the sharedfolder creation which is intentionally handled by VBoxManage and not Vagrant's "synced_folder" method. The last bit is pretty self-explanatory; we create the new shared folder and then make sure it's mounted each time the machine is accessed or touched since Vagrant likes to reload its mounts/shared folders on each load.
>
> ​	在上面的代码中，我在当前目录的绝对路径前添加了`\\?\`。这将强制Windows API允许增加MAX_PATH变量（通常限制为260）。更多关于[max path的信息](https://msdn.microsoft.com/en-us/library/windows/desktop/aa365247(v=vs.85).aspx#maxpath)。这是在创建共享文件夹时发生的，这是有意由VBoxManage处理而不是Vagrant的“synced_folder”方法。最后一部分非常直观；我们创建了新的共享文件夹，然后确保每次访问或触摸机器时都将其挂载，因为Vagrant喜欢在每次加载时重新加载其挂载/共享文件夹。

## npm仅使用`git:`和`ssh+git:` URL访问GitHub仓库，破坏了代理 npm only uses `git:` and `ssh+git:` URLs for GitHub repos, breaking proxies

**[@LaurentGoderre](https://github.com/LaurentGoderre)** fixed this with [some Git trickery](https://github.com/npm/npm/issues/5257#issuecomment-60441477):

**[@LaurentGoderre](https://github.com/LaurentGoderre)** 使用[一些Git技巧](https://github.com/npm/npm/issues/5257#issuecomment-60441477)解决了这个问题：

> I fixed this issue for several of my colleagues by running the following two commands:
>
> ​	我通过运行以下两个命令来解决了几位同事的此问题：
>
> ```
> git config --global url."https://github.com/".insteadOf git@github.com:
> git config --global url."https://".insteadOf git://
> ```
>
> One thing we noticed is that the `.gitconfig` used is not always the one expected so if you are on a machine that modified the home path to a shared drive, you need to ensure that your `.gitconfig` is the same on both your shared drive and in `c:\users\[your user]\`
>
> ​	我们注意到的一件事是`.gitconfig`不总是所期望的那个，因此如果您在将家目录路径修改为共享驱动器的计算机上，您需要确保您的`.gitconfig`在共享驱动器和`c:\users\[your user]\`中是相同的。

## SSL错误 SSL Error



```
npm ERR! Error: 7684:error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol:openssl\ssl\s23_clnt.c:787:
```

You are trying to talk SSL to an unencrypted endpoint. More often than not, this is due to a [proxy](https://docs.npmjs.com/misc/config#proxy) [configuration](https://docs.npmjs.com/misc/config#https-proxy) [error](https://docs.npmjs.com/misc/config#cafile) (see also [this helpful, if dated, guide](http://jjasonclark.com/how-to-setup-node-behind-web-proxy)). In this case, you do **not** want to disable `strict-ssl` – you may need to set up a CA / CA file for use with your proxy, but it's much better to take the time to figure that out than disabling SSL protection.

​	您正在尝试与未加密的终端进行SSL通信。更多情况下，这是由于代理配置错误（参见[此有用但可能过时的指南](http://jjasonclark.com/how-to-setup-node-behind-web-proxy)）导致的。在这种情况下，**不要**禁用 `strict-ssl`  - 您可能需要为代理设置CA / CA文件，但最好花时间弄清楚，而不是禁用SSL保护。

```
npm ERR! Error: SSL Error: CERT_UNTRUSTED
```



```
npm ERR! Error: SSL Error: UNABLE_TO_VERIFY_LEAF_SIGNATURE
```

This problem will happen if you're running Node 0.6. Please upgrade to node 0.8 or above. [See this post for details](http://blog.npmjs.org/post/71267056460/fastly-manta-loggly-and-couchdb-attachments).

​	如果您使用的是Node 0.6版本，则会出现此问题。请升级到Node 0.8或更高版本。[详细信息请参见此帖子](http://blog.npmjs.org/post/71267056460/fastly-manta-loggly-and-couchdb-attachments)。

You could also try these workarounds: `npm config set ca ""` or `npm config set strict-ssl false`

​	您还可以尝试以下解决方法： `npm config set ca ""`  或  `npm config set strict-ssl false`

```
npm ERR! Error: SSL Error: SELF_SIGNED_CERT_IN_CHAIN
```

[npm no longer supports its self-signed certificates](http://blog.npmjs.org/post/78085451721/npms-self-signed-certificate-is-no-more)

[npm不再支持自签名证书](http://blog.npmjs.org/post/78085451721/npms-self-signed-certificate-is-no-more)

Either:

要么：

- upgrade your version of npm `npm install npm -g --ca=""`
- 升级npm版本  `npm install npm -g --ca=""` 
- tell your current version of npm to use known registrars `npm config set ca=""`
- 告诉当前版本的npm使用已知的注册机  `npm config set ca=""` 

If this does not fix the problem, then you may have an SSL-intercepting proxy. (For example, https://github.com/npm/npm/issues/7439#issuecomment-76024878)

​	如果问题未解决，则可能存在SSL拦截代理。（例如，https://github.com/npm/npm/issues/7439#issuecomment-76024878）

## SSL拦截代理 SSL-intercepting proxy

Unsolved. See https://github.com/npm/npm/issues/9282

​	未解决。参见 https://github.com/npm/npm/issues/9282

## 找不到/服务器错误 Not found / Server error



```
npm http 404 https://registry.npmjs.org/faye-websocket/-/faye-websocket-0.7.0.tgz
npm ERR! fetch failed https://registry.npmjs.org/faye-websocket/-/faye-websocket-0.7.0.tgz
npm ERR! Error: 404 Not Found
```



```
npm http 500 https://registry.npmjs.org/phonegap
```

- It's most likely a temporary npm registry glitch. Check [npm server status](http://status.npmjs.org/) and try again later.
- 这很可能是npm注册表的临时故障。请检查[npm服务器状态](http://status.npmjs.org/)，稍后重试。
- If the error persists, perhaps the published package is corrupt. Contact the package owner and have them publish a new version of the package.
- 如果错误仍然存在，可能是由于发布的软件包损坏。请联系软件包所有者，并让他们发布软件包的新版本。

## 无效的JSON Invalid JSON



```
Error: Invalid JSON
```



```
npm ERR! SyntaxError: Unexpected token <
```



```
npm ERR! registry error parsing json
```

- Possible temporary npm registry glitch, or corrupted local server cache. Run `npm cache clean` and/or try again later.
- 可能是npm注册表的临时故障，或者是本地服务器缓存损坏。运行 `npm cache clean` 和/或稍后重试。
- This can be caused by corporate proxies that give HTML responses to `package.json` requests. Check npm's proxy [configuration](https://docs.npmjs.com/misc/config).
- 这可能是由于企业代理给 `package.json` 请求的HTML响应引起的。检查npm的代理[配置](https://docs.npmjs.com/misc/config)。
- Check that it's not a problem with a package you're trying to install (e.g. invalid `package.json`).
- 检查是否是您尝试安装的软件包的问题（例如，无效的 `package.json` ）。

## 输出中有许多 `ENOENT`  /  `ENOTEMPTY` 错误 Many `ENOENT` / `ENOTEMPTY` errors in output

npm is written to use resources efficiently on install, and part of this is that it tries to do as many things concurrently as is practical. Sometimes this results in race conditions and other synchronization issues. As of npm 2.0.0, a very large number of these issues were addressed. If you see `ENOENT lstat`, `ENOENT chmod`, `ENOTEMPTY unlink`, or something similar in your log output, try updating npm to the latest version. If the problem persists, look at [npm/npm#6043](https://github.com/npm/npm/issues/6043) and see if somebody has already discussed your issue.

​	npm的设计目标是在安装时高效使用资源，其中一部分是尽可能并发地执行尽可能多的操作。有时，这会导致竞争条件和其他同步问题。从npm 2.0.0开始，许多这些问题已得到解决。如果在日志输出中看到 `ENOENT lstat` ， `ENOENT chmod` ， `ENOTEMPTY unlink` 或类似的内容，请尝试将npm更新到最新版本。如果问题仍然存在，请查看[npm/npm#6043](https://github.com/npm/npm/issues/6043)并查看是否有人已经讨论了您的问题。

## `cb() never called!` 在使用缩小的依赖项时 `cb() never called!` when using shrinkwrapped dependencies

Take a look at [issue #5920](https://github.com/npm/npm/issues/5920). ~~We're working on fixing this one, but it's a fairly subtle race condition and it's taking us a little time. You might try moving your `npm-shrinkwrap.json` file out of the way until we have this fixed.~~ This has been fixed in versions of npm newer than `npm@2.1.5`, so update to `npm@latest`.

​	请参阅[问题#5920](https://github.com/npm/npm/issues/5920)。~~我们正在努力解决这个问题，但这是一个相当微妙的竞争条件，我们需要一些时间。您可以尝试将 `npm-shrinkwrap.json` 文件移到其他位置，直到我们解决此问题。~~ 这个问题已经在更新的npm版本中（ `npm@2.1.5` 之后）得到解决，请更新到 `npm@latest` 。

## `npm login`错误 `npm login` errors

Sometimes `npm login` fails for no obvious reason. The first thing to do is to log in at https://www.npmjs.com/login and check that your e-mail address on `npmjs.com` matches the email address you are giving to `npm login`.

​	有时 `npm login` 失败，原因不明。首先要做的是在https://www.npmjs.com/login登录并检查您在 `npmjs.com` 上的电子邮件地址是否与您提供给 `npm login` 的电子邮件地址匹配。

If that's not the problem, or if you are seeing the message `"may not mix password_sha and pbkdf2"`, then

​	如果问题不在这里，或者如果您看到消息 `"may not mix password_sha and pbkdf2"` ，那么：

1. Log in at https://npmjs.com/
2. 在https://npmjs.com/上登录。
3. Change password at https://npmjs.com/password – you can even "change" it to the same password
4. 在https://npmjs.com/password上更改密码 - 您甚至可以将其“更改”为相同的密码。
5. Clear login-related fields from `~/.npmrc` – e.g., by running `sed -ie '/registry.npmjs.org/d' ~/.npmrc`
6. 从 `~/.npmrc` 中清除与登录相关的字段 - 例如，通过运行 `sed -ie '/registry.npmjs.org/d' ~/.npmrc` 。
7. `npm login`

and it generally seems to work.

通常会起作用。

See https://github.com/npm/npm/issues/6641#issuecomment-72984009 for the history of this issue.

​	有关此问题的历史，请参见https://github.com/npm/npm/issues/6641#issuecomment-72984009。

## Windows上的 `npm` 在 `addRemoteTarball` 时挂起 `npm` hangs on Windows at `addRemoteTarball`

Check if you have two temp directories set in your `.npmrc`:

​	检查 `.npmrc` 中是否设置了两个临时目录：

```
> npm config ls -l
```

Look for lines defining the `tmp` config variable. If you find more than one, remove all but one of them.

​	查找定义 `tmp` 配置变量的行。如果找到多个，请删除其中的所有内容，只保留一个。

See https://github.com/npm/npm/issues/7590 for more about this unusual problem.

​	有关此异常问题的更多信息，请参见https://github.com/npm/npm/issues/7590。

## Windows机器上的npm未运行最新版本 npm not running the latest version on a Windows machine

See the section about Windows [here](try-the-latest-stable-version-of-npm).

​	请参阅此处关于Windows的部分[here](try-the-latest-stable-version-of-npm)。
