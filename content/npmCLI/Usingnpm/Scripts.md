+++
title = "脚本"
date = 2023-09-22T21:24:08+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/cli/v10/using-npm/scripts](https://docs.npmjs.com/cli/v10/using-npm/scripts)

# scripts - 脚本

How npm handles the "scripts" field

​	npm 如何处理 "scripts" 字段

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

The `"scripts"` property of your `package.json` file supports a number of built-in scripts and their preset life cycle events as well as arbitrary scripts. These all can be executed by running `npm run-script <stage>` or `npm run <stage>` for short. *Pre* and *post* commands with matching names will be run for those as well (e.g. `premyscript`, `myscript`, `postmyscript`). Scripts from dependencies can be run with `npm explore <pkg> -- npm run <stage>`.

​	您的  `package.json`  文件的  `"scripts"`  属性支持许多内置脚本及其预设的生命周期事件，以及任意脚本。可以通过运行  `npm run-script <stage>`  或简写为  `npm run <stage>`  来执行这些脚本。具有匹配名称的 *pre* 和 *post* 命令也将运行（例如  `premyscript` 、 `myscript` 、 `postmyscript` ）。依赖项中的脚本可以使用  `npm explore <pkg> -- npm run <stage>`  运行。

### 预先和后续脚本 Pre & Post Scripts

To create "pre" or "post" scripts for any scripts defined in the `"scripts"` section of the `package.json`, simply create another script *with a matching name* and add "pre" or "post" to the beginning of them.

​	要为  `package.json`  的  `"scripts"`  部分中定义的任何脚本创建 "pre" 或 "post" 脚本，只需创建另一个具有匹配名称的脚本，并在其前面添加 "pre" 或 "post"。

```json
{
  "scripts": {
    "precompress": "{{ executes BEFORE the `compress` script }}",
    "compress": "{{ run command to compress files }}",
    "postcompress": "{{ executes AFTER `compress` script }}"
  }
}
```

In this example `npm run compress` would execute these scripts as described.

​	在此示例中， `npm run compress`  将按照描述执行这些脚本。

### 生命周期脚本 Life Cycle Scripts

There are some special life cycle scripts that happen only in certain situations. These scripts happen in addition to the `pre<event>`, `post<event>`, and `<event>` scripts.

​	某些特殊的生命周期脚本仅在特定情况下发生。这些脚本会在  `pre<event>` 、 `post<event>`  和  `<event>`  脚本之后运行。

- `prepare`, `prepublish`, `prepublishOnly`, `prepack`, `postpack`, `dependencies`

**prepare** (since `npm@4.0.0`)

**prepare**（自  `npm@4.0.0`  起）

- Runs BEFORE the package is packed, i.e. during `npm publish` and `npm pack`
- 在打包软件包之前运行，即在  `npm publish`  和  `npm pack`  期间运行
- Runs on local `npm install` without any arguments
- 在本地  `npm install`  无任何参数的情况下运行
- Runs AFTER `prepublish`, but BEFORE `prepublishOnly`
- 在  `prepublish`  之后但在  `prepublishOnly`  之前运行
- NOTE: If a package being installed through git contains a `prepare` script, its `dependencies` and `devDependencies` will be installed, and the prepare script will be run, before the package is packaged and installed.
- 注意：如果通过 git 安装的软件包包含  `prepare`  脚本，则会安装其  `dependencies`  和  `devDependencies` ，并在打包和安装软件包之前运行  `prepare`  脚本。
- As of `npm@7` these scripts run in the background. To see the output, run with: `--foreground-scripts`.
- 从  `npm@7`  开始，这些脚本在后台运行。要查看输出，请使用： `--foreground-scripts` 。

**prepublish** (DEPRECATED)

**prepublish**（已弃用）

- Does not run during `npm publish`, but does run during `npm ci` and `npm install`. See below for more info.
- 不在  `npm publish`  期间运行，但在  `npm ci`  和  `npm install`  期间运行。详见下文了解更多信息。

**prepublishOnly**

- Runs BEFORE the package is prepared and packed, ONLY on `npm publish`.
- 仅在准备和打包软件包之前运行，仅在  `npm publish`  期间运行。

**prepack**

- Runs BEFORE a tarball is packed (on "`npm pack`", "`npm publish`", and when installing a git dependency).
- 在打包 tarball 之前运行（在 " `npm pack` "、" `npm publish` " 和安装 git 依赖项时运行）。
- NOTE: "`npm run pack`" is NOT the same as "`npm pack`". "`npm run pack`" is an arbitrary user defined script name, where as, "`npm pack`" is a CLI defined command.
- 注意：" `npm run pack` " 与 " `npm pack` " 不同。" `npm run pack` " 是一个任意用户定义的脚本名称，而 " `npm pack` " 是一个 CLI 定义的命令。

**postpack**

- Runs AFTER the tarball has been generated but before it is moved to its final destination (if at all, publish does not save the tarball locally)
- 在生成 tarball 之后但在将其移动到最终位置之前运行（如果有的话，发布不会在本地保存 tarball）

**dependencies**

- Runs AFTER any operations that modify the `node_modules` directory IF changes occurred.
- 在修改  `node_modules`  目录的任何操作之后运行，如果发生了更改。
- Does NOT run in global mode
- 不在全局模式下运行

#### Prepare and Prepublish

**Deprecation Note: prepublish**

**弃用说明：prepublish**

Since `npm@1.1.71`, the npm CLI has run the `prepublish` script for both `npm publish` and `npm install`, because it's a convenient way to prepare a package for use (some common use cases are described in the section below). It has also turned out to be, in practice, [very confusing](https://github.com/npm/npm/issues/10074). As of `npm@4.0.0`, a new event has been introduced, `prepare`, that preserves this existing behavior. A *new* event, `prepublishOnly` has been added as a transitional strategy to allow users to avoid the confusing behavior of existing npm versions and only run on `npm publish` (for instance, running the tests one last time to ensure they're in good shape).

​	自  `npm@1.1.71`  起，npm CLI 在  `npm publish`  和  `npm install`  期间都会运行  `prepublish`  脚本，因为这是一种方便的方式来准备包供使用（一些常见的用例在下面的部分中描述）。实际上，这种做法在实践中非常令人困惑（https://github.com/npm/npm/issues/10074）。自  `npm@4.0.0`  起，引入了一个新的事件  `prepare` ，它保留了这种现有行为。为了避免现有 npm 版本的混乱行为并仅在  `npm publish`  期间运行，还添加了一个过渡策略的新事件  `prepublishOnly` 。有关此更改的更详细的理由和进一步阅读，请参阅 https://github.com/npm/npm/issues/10074。

See https://github.com/npm/npm/issues/10074 for a much lengthier justification, with further reading, for this change.

**Use Cases**

**用例**

If you need to perform operations on your package before it is used, in a way that is not dependent on the operating system or architecture of the target system, use a `prepublish` script. This includes tasks such as:

​	如果您需要在包被使用之前对其执行操作，而这些操作不依赖于目标系统的操作系统或架构，请使用  `prepublish`  脚本。这包括以下任务：

- Compiling CoffeeScript source code into JavaScript.
- 将 CoffeeScript 源代码编译为 JavaScript。
- Creating minified versions of JavaScript source code.
- 创建 JavaScript 源代码的缩小版本。
- Fetching remote resources that your package will use.
- 获取您的软件包将使用的远程资源。

The advantage of doing these things at `prepublish` time is that they can be done once, in a single place, thus reducing complexity and variability. Additionally, this means that:

​	在  `prepublish`  时间执行这些操作的优点在于，它们可以一次性地在一个地方完成，从而减少复杂性和可变性。此外，这意味着：

- You can depend on `coffee-script` as a `devDependency`, and thus your users don't need to have it installed.
- 您可以将  `coffee-script`  作为  `devDependency`  依赖项，因此您的用户不需要安装它。
- You don't need to include minifiers in your package, reducing the size for your users.
- 您无需在软件包中包含缩小工具，从而减小用户的软件包大小。
- You don't need to rely on your users having `curl` or `wget` or other system tools on the target machines.
- 您无需依赖用户在目标机器上安装  `curl` 、 `wget`  或其他系统工具。

#### 依赖项 Dependencies

The `dependencies` script is run any time an `npm` command causes changes to the `node_modules` directory. It is run AFTER the changes have been applied and the `package.json` and `package-lock.json` files have been updated.

 	`dependencies`  脚本会在任何导致  `node_modules`  目录发生更改的  `npm`  命令执行时运行。它会在应用更改并更新  `package.json`  和  `package-lock.json`  文件之后运行。

### 生命周期操作顺序 Life Cycle Operation Order

#### [`npm cache add`](https://docs.npmjs.com/cli/v10/commands/npm-cache)

- `prepare`

#### [`npm ci`](https://docs.npmjs.com/cli/v10/commands/npm-ci)

- `preinstall`

- `install`

- `postinstall`

- `prepublish`

- `preprepare`

- `prepare`

- `postprepare`

  These all run after the actual installation of modules into `node_modules`, in order, with no internal actions happening in between
  
  所有这些都在将模块实际安装到  `node_modules`  之后按顺序运行，没有在中间发生的内部操作。

#### [`npm diff`](https://docs.npmjs.com/cli/v10/commands/npm-diff)

- `prepare`

#### [`npm install`](https://docs.npmjs.com/cli/v10/commands/npm-install)

These also run when you run `npm install -g <pkg-name>`

​	如果以全局模式运行  `npm install -g <pkg-name>` ，也会运行以下脚本

- `preinstall`
- `install`
- `postinstall`
- `prepublish`
- `preprepare`
- `prepare`
- `postprepare`

If there is a `binding.gyp` file in the root of your package and you haven't defined your own `install` or `preinstall` scripts, npm will default the `install` command to compile using node-gyp via `node-gyp rebuild`

​	如果在软件包的根目录中存在  `binding.gyp`  文件并且您没有定义自己的  `install`  或  `preinstall`  脚本，npm 将默认使用  `install`  命令通过  `node-gyp`  进行编译，即  `node-gyp rebuild` 

These are run from the scripts of `<pkg-name>`

​	这些脚本是从  `<pkg-name>`  的脚本中运行的

#### [`npm pack`](https://docs.npmjs.com/cli/v10/commands/npm-pack)

- `prepack`
- `prepare`
- `postpack`

#### [`npm publish`](https://docs.npmjs.com/cli/v10/commands/npm-publish)

- `prepublishOnly`
- `prepack`
- `prepare`
- `postpack`
- `publish`
- `postpublish`

```
prepare` will not run during `--dry-run
```

#### [`npm rebuild`](https://docs.npmjs.com/cli/v10/commands/npm-rebuild)

- `preinstall`
- `install`
- `postinstall`
- `prepare`

`prepare` is only run if the current directory is a symlink (e.g. with linked packages)

​	只有当当前目录是符号链接（例如链接的软件包）时，才会运行  `prepare` 

#### [`npm restart`](https://docs.npmjs.com/cli/v10/commands/npm-restart)

If there is a `restart` script defined, these events are run, otherwise `stop` and `start` are both run if present, including their `pre` and `post` iterations)

​	如果定义了  `restart`  脚本，则运行以下事件，否则如果存在，则同时运行  `stop`  和  `start` ，包括它们的  `pre`  和  `post`  迭代）

- `prerestart`
- `restart`
- `postrestart`

#### [`npm run `](https://docs.npmjs.com/cli/v10/commands/npm-run-script)

- `pre<user-defined>`
- `<user-defined>`
- `post<user-defined>`

#### [`npm start`](https://docs.npmjs.com/cli/v10/commands/npm-start)

- `prestart`
- `start`
- `poststart`

If there is a `server.js` file in the root of your package, then npm will default the `start` command to `node server.js`. `prestart` and `poststart` will still run in this case.

​	如果软件包的根目录中存在  `server.js`  文件，则 npm 将默认使用  `start`  命令运行  `node server.js` 。在这种情况下， `prestart`  和  `poststart`  仍将运行。

#### [`npm stop`](https://docs.npmjs.com/cli/v10/commands/npm-stop)

- `prestop`
- `stop`
- `poststop`

#### [`npm test`](https://docs.npmjs.com/cli/v10/commands/npm-test)

- `pretest`
- `test`
- `posttest`

#### [`npm version`](https://docs.npmjs.com/cli/v10/commands/npm-version)

- `preversion`
- `version`
- `postversion`

#### 关于缺少 [ `npm uninstall` ](https://docs.npmjs.com/cli/v10/commands/npm-uninstall) 脚本的说明 A Note on a lack of [`npm uninstall`](https://docs.npmjs.com/cli/v10/commands/npm-uninstall) scripts

While npm v6 had `uninstall` lifecycle scripts, npm v7 does not. Removal of a package can happen for a wide variety of reasons, and there's no clear way to currently give the script enough context to be useful.

​	虽然 npm v6 中有  `uninstall`  生命周期脚本，但 npm v7 中没有。卸载软件包可能发生的原因有很多，目前没有明确的方法可以为脚本提供足够的上下文来进行有用的操作。

Reasons for a package removal include:

软件包被移除的原因包括：

- a user directly uninstalled this package
- 用户直接卸载了该软件包
- a user uninstalled a dependant package and so this dependency is being uninstalled
- 用户卸载了一个依赖包，因此正在卸载此依赖项
- a user uninstalled a dependant package but another package also depends on this version
- 用户卸载了一个依赖包，但另一个软件包也依赖于此版本
- this version has been merged as a duplicate with another version
- 此版本已与另一个版本合并为重复版本
- etc.
- 等等

Due to the lack of necessary context, `uninstall` lifecycle scripts are not implemented and will not function.

​	由于缺乏必要的上下文， `uninstall`  生命周期脚本没有实现，也不会起作用。

### 用户 User

When npm is run as root, scripts are always run with the effective uid and gid of the working directory owner.

​	当以 root 用户运行 npm 时，脚本始终以工作目录所有者的有效 uid 和 gid 运行。

### 环境 Environment

Package scripts run in an environment where many pieces of information are made available regarding the setup of npm and the current state of the process.

​	包脚本在一个环境中运行，在该环境中提供了关于 npm 的设置和当前进程状态的许多信息。

#### path

If you depend on modules that define executable scripts, like test suites, then those executables will be added to the `PATH` for executing the scripts. So, if your package.json has this:

​	如果您依赖定义了可执行脚本的模块，例如测试套件，则这些可执行文件将添加到  `PATH`  以执行脚本。因此，如果您的 package.json 包含以下内容：

```json
{
  "name" : "foo",
  "dependencies" : {
    "bar" : "0.1.x"
  },
  "scripts": {
    "start" : "bar ./test"
  }
}
```

then you could run `npm start` to execute the `bar` script, which is exported into the `node_modules/.bin` directory on `npm install`.

​	那么您可以运行  `npm start`  来执行  `bar`  脚本，该脚本在  `npm install`  时导出到  `node_modules/.bin`  目录中。

#### package.json vars

The package.json fields are tacked onto the `npm_package_` prefix. So, for instance, if you had `{"name":"foo", "version":"1.2.5"}` in your package.json file, then your package scripts would have the `npm_package_name` environment variable set to "foo", and the `npm_package_version` set to "1.2.5". You can access these variables in your code with `process.env.npm_package_name` and `process.env.npm_package_version`, and so on for other fields.

​	package.json 字段会添加到  `npm_package_`  前缀。因此，例如，如果您的 package.json 文件中有  `{"name":"foo", "version":"1.2.5"}` ，那么您的包脚本将具有  `npm_package_name`  环境变量设置为 "foo"，并且  `npm_package_version`  设置为 "1.2.5"。您可以使用  `process.env.npm_package_name`  和  `process.env.npm_package_version`  在代码中访问这些变量，以及其他字段的类似方式。

See [`package.json`](https://docs.npmjs.com/cli/v10/configuring-npm/package-json) for more on package configs.

​	有关包配置的更多信息，请参见 [ `package.json` ](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)。

#### 当前生命周期事件 current lifecycle event

Lastly, the `npm_lifecycle_event` environment variable is set to whichever stage of the cycle is being executed. So, you could have a single script used for different parts of the process which switches based on what's currently happening.

​	最后， `npm_lifecycle_event`  环境变量设置为正在执行的生命周期阶段。因此，您可以使用单个脚本用于进程的不同部分，并根据当前发生的情况进行切换。

Objects are flattened following this format, so if you had `{"scripts":{"install":"foo.js"}}` in your package.json, then you'd see this in the script:

​	这些对象按照此格式进行展平，因此如果您的 package.json 中有  `{"scripts":{"install":"foo.js"}}` ，那么您将在脚本中看到这个：

```bash
process.env.npm_package_scripts_install === "foo.js"
```

### 示例 Examples

For example, if your package.json contains this:

​	例如，如果您的 package.json 包含以下内容：

```json
{
  "scripts" : {
    "install" : "scripts/install.js",
    "postinstall" : "scripts/install.js",
    "uninstall" : "scripts/uninstall.js"
  }
}
```

then `scripts/install.js` will be called for the install and post-install stages of the lifecycle, and `scripts/uninstall.js` will be called when the package is uninstalled. Since `scripts/install.js` is running for two different phases, it would be wise in this case to look at the `npm_lifecycle_event` environment variable.

那么  `scripts/install.js`  将在生命周期的安装和安装后阶段调用，并在卸载软件包时调用。由于  `scripts/install.js`  在两个不同的阶段运行，因此在这种情况下，最好查看  `npm_lifecycle_event`  环境变量。

If you want to run a make command, you can do so. This works just fine:

​	如果要运行 make 命令，可以这样做。这可以正常工作：

```json
{
  "scripts" : {
    "preinstall" : "./configure",
    "install" : "make && make install",
    "test" : "make test"
  }
}
```

### 退出 Exiting

Scripts are run by passing the line as a script argument to `sh`.

​	脚本是通过将行作为脚本参数传递给  `sh`  来运行的。

If the script exits with a code other than 0, then this will abort the process.

​	如果脚本以非零错误代码退出，那么这将中止进程。

Note that these script files don't have to be Node.js or even JavaScript programs. They just have to be some kind of executable file.

​	请注意，这些脚本文件不必是 Node.js 或甚至 JavaScript 程序。它们只需是某种可执行文件即可。

### 最佳实践 Best Practices

- Don't exit with a non-zero error code unless you *really* mean it. Except for uninstall scripts, this will cause the npm action to fail, and potentially be rolled back. If the failure is minor or only will prevent some optional features, then it's better to just print a warning and exit successfully.
- 除非您 *确实* 想这样做，否则不要以非零错误代码退出。除了卸载脚本外，这将导致 npm 操作失败，并可能被回滚。如果故障较小或仅会阻止一些可选功能，则最好只打印警告并正常退出。
- Try not to use scripts to do what npm can do for you. Read through [`package.json`](https://docs.npmjs.com/cli/v10/configuring-npm/package-json) to see all the things that you can specify and enable by simply describing your package appropriately. In general, this will lead to a more robust and consistent state.
- 尽量不要使用脚本来完成 npm 可以为您完成的工作。仔细阅读 [ `package.json` ](https://docs.npmjs.com/cli/v10/configuring-npm/package-json) 以了解通过适当描述软件包来指定和启用的所有内容。一般来说，这将导致更健壮和一致的状态。
- Inspect the env to determine where to put things. For instance, if the `npm_config_binroot` environment variable is set to `/home/user/bin`, then don't try to install executables into `/usr/local/bin`. The user probably set it up that way for a reason.
- 检查环境以确定放置事物的位置。例如，如果  `npm_config_binroot`  环境变量设置为  `/home/user/bin` ，那么不要尝试将可执行文件安装到  `/usr/local/bin` 。用户可能以某种原因设置了它。
- Don't prefix your script commands with "sudo". If root permissions are required for some reason, then it'll fail with that error, and the user will sudo the npm command in question.
- 不要在脚本命令前加上 "sudo"。如果需要 root 权限，则会因为该错误而失败，用户将对相关的 npm 命令使用 sudo。
- Don't use `install`. Use a `.gyp` file for compilation, and `prepare` for anything else. You should almost never have to explicitly set a preinstall or install script. If you are doing this, please consider if there is another option. The only valid use of `install` or `preinstall` scripts is for compilation which must be done on the target architecture.
- 不要使用  `install` 。使用  `.gyp`  文件进行编译，并使用  `prepare`  进行其他操作。您几乎不需要显式设置  `install`  或  `preinstall`  脚本。如果您正在这样做，请考虑是否有其他选项。 `install`  或  `preinstall`  脚本的唯一有效用途是必须在目标架构上进行的编译。
- Scripts are run from the root of the package folder, regardless of what the current working directory is when `npm` is invoked. If you want your script to use different behavior based on what subdirectory you're in, you can use the `INIT_CWD` environment variable, which holds the full path you were in when you ran `npm run`.
- 脚本是从软件包文件夹的根目录运行的，而不管在调用  `npm`  时的当前工作目录是什么。如果您希望脚本根据所在的子目录使用不同的行为，可以使用  `INIT_CWD`  环境变量，该变量保存运行  `npm run`  时所在的完整路径。

### See Also

- [npm run-script](https://docs.npmjs.com/cli/v10/commands/npm-run-script)
- [package.json](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)
- [npm developers](https://docs.npmjs.com/cli/v10/using-npm/developers)
- [npm install](https://docs.npmjs.com/cli/v10/commands/npm-install)
