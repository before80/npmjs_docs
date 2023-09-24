+++
title = "配置"
date = 2023-09-22T21:23:33+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/cli/v10/using-npm/config](https://docs.npmjs.com/cli/v10/using-npm/config)

# config - 配置

More than you probably want to know about npm configuration

​	npm配置的更多细节

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

npm gets its configuration values from the following sources, sorted by priority:

​	npm从以下来源获取其配置值，按优先级排序：

#### 命令行标志 Command Line Flags

Putting `--foo bar` on the command line sets the `foo` configuration parameter to `"bar"`. A `--` argument tells the cli parser to stop reading flags. Using `--flag` without specifying any value will set the value to `true`.

​	在命令行上使用 `--foo bar` 将配置参数 `foo` 设置为 `"bar"` 。 `--` 参数告诉cli解析器停止读取标志。使用 `--flag` 而不指定任何值将将值设置为 `true` 。

Example: `--flag1 --flag2` will set both configuration parameters to `true`, while `--flag1 --flag2 bar` will set `flag1` to `true`, and `flag2` to `bar`. Finally, `--flag1 --flag2 -- bar` will set both configuration parameters to `true`, and the `bar` is taken as a command argument.

​	示例： `--flag1 --flag2` 将两个配置参数都设置为 `true` ，而 `--flag1 --flag2 bar` 将 `flag1` 设置为 `true` ， `flag2` 设置为 `bar` 。最后， `--flag1 --flag2 -- bar` 将两个配置参数都设置为 `true` ，并且 `bar` 被视为命令参数。

#### 环境变量 Environment Variables

Any environment variables that start with `npm_config_` will be interpreted as a configuration parameter. For example, putting `npm_config_foo=bar` in your environment will set the `foo` configuration parameter to `bar`. Any environment configurations that are not given a value will be given the value of `true`. Config values are case-insensitive, so `NPM_CONFIG_FOO=bar` will work the same. However, please note that inside [`scripts`](https://docs.npmjs.com/cli/v10/using-npm/scripts) npm will set its own environment variables and Node will prefer those lowercase versions over any uppercase ones that you might set. For details see [this issue](https://github.com/npm/npm/issues/14528).

​	以 `npm_config_` 开头的任何环境变量都将被解释为配置参数。例如，在环境中设置 `npm_config_foo=bar` 将会将配置参数 `foo` 设置为 `bar` 。未给出值的任何环境配置将被赋予 `true` 的值。配置值对大小写不敏感，因此 `NPM_CONFIG_FOO=bar` 将起到相同的作用。但是，请注意，在[ `scripts` ](https://docs.npmjs.com/cli/v10/using-npm/scripts)内部，npm将设置自己的环境变量，并且Node将优先使用这些小写版本，而不是您设置的任何大写版本。有关详细信息，请参见[此问题](https://github.com/npm/npm/issues/14528)。

Notice that you need to use underscores instead of dashes, so `--allow-same-version` would become `npm_config_allow_same_version=true`.

​	请注意，您需要使用下划线而不是破折号，因此 `--allow-same-version` 将变为 `npm_config_allow_same_version=true` 。

#### npmrc文件 npmrc Files

The four relevant files are:

​	四个相关的文件如下：

- per-project configuration file (`/path/to/my/project/.npmrc`)
- 项目配置文件（ `/path/to/my/project/.npmrc` ）
- per-user configuration file (defaults to `$HOME/.npmrc`; configurable via CLI option `--userconfig` or environment variable `$NPM_CONFIG_USERCONFIG`)
- 用户配置文件（默认为 `$HOME/.npmrc` ；可以通过CLI选项 `--userconfig` 或环境变量 `$NPM_CONFIG_USERCONFIG` 进行配置）
- global configuration file (defaults to `$PREFIX/etc/npmrc`; configurable via CLI option `--globalconfig` or environment variable `$NPM_CONFIG_GLOBALCONFIG`)
- 全局配置文件（默认为 `$PREFIX/etc/npmrc` ；可以通过CLI选项 `--globalconfig` 或环境变量 `$NPM_CONFIG_GLOBALCONFIG` 进行配置）
- npm's built-in configuration file (`/path/to/npm/npmrc`)
- npm的内置配置文件（ `/path/to/npm/npmrc` ）

See [npmrc](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc) for more details.

​	有关详细信息，请参见[npmrc](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc)。

#### 默认配置 Default Configs

Run `npm config ls -l` to see a set of configuration parameters that are internal to npm, and are defaults if nothing else is specified.

​	运行 `npm config ls -l` 可以查看一组仅供npm内部使用的配置参数，如果没有指定其他内容，则为默认值。

### 缩写和其他CLI便利功能 Shorthands and Other CLI Niceties

The following shorthands are parsed on the command-line:

​	以下缩写在命令行上进行解析：

- `-a`: `--all`
- `--enjoy-by`: `--before`
- `-c`: `--call`
- `--desc`: `--description`
- `-f`: `--force`
- `-g`: `--global`
- `--iwr`: `--include-workspace-root`
- `-L`: `--location`
- `-d`: `--loglevel info`
- `-s`: `--loglevel silent`
- `--silent`: `--loglevel silent`
- `--ddd`: `--loglevel silly`
- `--dd`: `--loglevel verbose`
- `--verbose`: `--loglevel verbose`
- `-q`: `--loglevel warn`
- `--quiet`: `--loglevel warn`
- `-l`: `--long`
- `-m`: `--message`
- `--local`: `--no-global`
- `-n`: `--no-yes`
- `--no`: `--no-yes`
- `-p`: `--parseable`
- `--porcelain`: `--parseable`
- `-C`: `--prefix`
- `--readonly`: `--read-only`
- `--reg`: `--registry`
- `-S`: `--save`
- `-B`: `--save-bundle`
- `-D`: `--save-dev`
- `-E`: `--save-exact`
- `-O`: `--save-optional`
- `-P`: `--save-prod`
- `-?`: `--usage`
- `-h`: `--usage`
- `-H`: `--usage`
- `--help`: `--usage`
- `-v`: `--version`
- `-w`: `--workspace`
- `--ws`: `--workspaces`
- `-y`: `--yes`

If the specified configuration param resolves unambiguously to a known configuration parameter, then it is expanded to that configuration parameter. For example:

​	如果指定的配置参数可以明确解析为已知的配置参数，则会将其扩展为该配置参数。例如：

```bash
npm ls --par
# same as:
npm ls --parseable
```

If multiple single-character shorthands are strung together, and the resulting combination is unambiguously not some other configuration param, then it is expanded to its various component pieces. For example:

​	如果将多个单字符缩写连在一起，并且生成的组合明显不是其他配置参数，则会将其扩展为其各个组成部分。例如：

```bash
npm ls -gpld
# same as:
npm ls --global --parseable --long --loglevel info
```

### 配置设置 Config Settings

#### `_auth`

- Default: null
- 默认值：null
- Type: null or String
- 类型：null或字符串

A basic-auth string to use when authenticating against the npm registry. This will ONLY be used to authenticate against the npm registry. For other registries you will need to scope it like "//other-registry.tld/:_auth"

​	在与npm注册表进行身份验证时使用的基本身份验证字符串。这仅用于与npm注册表进行身份验证。对于其他注册表，您需要像 `//other-registry.tld/:_auth` 这样进行范围限定。

Warning: This should generally not be set via a command-line option. It is safer to use a registry-provided authentication bearer token stored in the ~/.npmrc file by running `npm login`.

警告：通常不应该通过命令行选项来设置此值。最好使用存储在 `~/.npmrc` 文件中的注册表提供的身份验证令牌运行 `npm login` 。

#### `access`

- Default: 'public' for new packages, existing packages it will not change the current level
- 默认值：对于新软件包为'public'，对于现有软件包不会更改当前级别
- Type: null, "restricted", or "public"
- 类型：null、"restricted"或"public"

If you do not want your scoped package to be publicly viewable (and installable) set `--access=restricted`.

​	如果您不希望公开查看（和安装）您的作用域软件包，请设置 `--access=restricted` 。

Unscoped packages can not be set to `restricted`.

​	无法将无作用域的软件包设置为 `restricted` 。

Note: This defaults to not changing the current access level for existing packages. Specifying a value of `restricted` or `public` during publish will change the access for an existing package the same way that `npm access set status` would.

注意：对于现有软件包，默认情况下不会更改当前访问级别。在发布时指定 `restricted` 或 `public` 的值将以与 `npm access set status` 相同的方式更改现有软件包的访问级别。

#### `all`

- Default: false
- 默认值：false
- Type: Boolean
- 类型：布尔值

When running `npm outdated` and `npm ls`, setting `--all` will show all outdated or installed packages, rather than only those directly depended upon by the current project.

​	在运行 `npm outdated` 和 `npm ls` 时，设置 `--all` 将显示所有过时或已安装的软件包，而不仅仅是当前项目直接依赖的软件包。

#### `allow-same-version`

- Default: false
- 默认值：false
- Type: Boolean
- 类型：布尔值

Prevents throwing an error when `npm version` is used to set the new version to the same value as the current version.

​	当使用 `npm version` 将新版本设置为与当前版本相同时，防止抛出错误。

#### `audit`

- Default: true
- 默认值：true
- Type: Boolean
- 类型：布尔值

When "true" submit audit reports alongside the current npm command to the default registry and all registries configured for scopes. See the documentation for [`npm audit`](https://docs.npmjs.com/cli/v10/commands/npm-audit) for details on what is submitted.

​	当为"true"时，将提交审核报告与当前npm命令一起发送到默认注册表和配置了作用域的所有注册表。有关提交的详细信息，请参见[ `npm audit` ](https://docs.npmjs.com/cli/v10/commands/npm-audit)的文档。

#### `audit-level`

- Default: null
- Type: null, "info", "low", "moderate", "high", "critical", or "none"

The minimum level of vulnerability for `npm audit` to exit with a non-zero exit code.

​	`npm audit` 退出时的最低漏洞级别，以非零退出代码退出。

#### `auth-type`

- Default: "web"
- Type: "legacy" or "web"

What authentication strategy to use with `login`. Note that if an `otp` config is given, this value will always be set to `legacy`.

​	与 `login` 一起使用的身份验证策略。请注意，如果给出了 `otp` 配置，则此值将始终设置为 `legacy` 。

#### `before`

- Default: null
- Type: null or Date

If passed to `npm install`, will rebuild the npm tree such that only versions that were available **on or before** the `--before` time get installed. If there's no versions available for the current set of direct dependencies, the command will error.

​	如果传递给 `npm install` ，将重新构建npm树，以便仅安装在 `--before` 时间**之前或之前**可用的版本。如果当前直接依赖项集合没有可用的版本，则该命令将出错。

If the requested version is a `dist-tag` and the given tag does not pass the `--before` filter, the most recent version less than or equal to that tag will be used. For example, `foo@latest` might install `foo@1.2` even though `latest` is `2.0`.

​	如果请求的版本是 `dist-tag` ，并且给定的标签未通过 `--before` 过滤器，则将使用小于或等于该标签的最新版本。例如， `foo@latest` 可能会安装 `foo@1.2` ，即使 `latest` 是 `2.0` 。

#### `bin-links`

- Default: true
- Type: Boolean

Tells npm to create symlinks (or `.cmd` shims on Windows) for package executables.

​	告诉npm为软件包的可执行文件创建符号链接（或在Windows上创建 `.cmd` 的shim）。

Set to false to have it not do this. This can be used to work around the fact that some file systems don't support symlinks, even on ostensibly Unix systems.

​	将其设置为false以避免执行此操作。这可以用来解决一些文件系统即使在表面上是Unix系统上也不支持符号链接的问题。

#### `browser`

- Default: OS X: `"open"`, Windows: `"start"`, Others: `"xdg-open"`
- 默认值：OS X： `"open"` ，Windows： `"start"` ，其他系统： `"xdg-open"` 
- Type: null, Boolean, or String

The browser that is called by npm commands to open websites.

​	npm命令调用的浏览器以打开网站。

Set to `false` to suppress browser behavior and instead print urls to terminal.

​	设置为 `false` 以禁止浏览器行为，而是将URL打印到终端。

Set to `true` to use default system URL opener.

​	设置为 `true` 以使用默认的系统URL打开器。

#### `ca`

- Default: null
- Type: null or String (can be set multiple times)
- 类型：null或字符串（可以设置多次）

The Certificate Authority signing certificate that is trusted for SSL connections to the registry. Values should be in PEM format (Windows calls it "Base-64 encoded X.509 (.CER)") with newlines replaced by the string "\n". For example:

​	用于SSL连接到注册表的受信任的证书颁发机构签名证书。值应该是PEM格式（Windows称其为“Base-64编码的X.509（.CER）”），换行符用字符串“\n”替换。例如：

```ini
ca="-----BEGIN CERTIFICATE-----\nXXXX\nXXXX\n-----END CERTIFICATE-----"
```

Set to `null` to only allow "known" registrars, or to a specific CA cert to trust only that specific signing authority.

​	设置为 `null` 以仅允许“已知”的注册机构，或者设置为特定的CA证书以仅信任该特定的签名机构。

Multiple CAs can be trusted by specifying an array of certificates:

​	可以通过指定证书数组来信任多个CA：

```ini
ca[]="..."
ca[]="..."
```

See also the `strict-ssl` config.

​	还请参阅 `strict-ssl` 配置。

#### `cache`

- Default: Windows: `%LocalAppData%\npm-cache`, Posix: `~/.npm`
- 默认值：Windows： `%LocalAppData%\npm-cache` ，Posix： `~/.npm` 
- Type: Path

The location of npm's cache directory.

​	npm缓存目录的位置。

#### `cafile`

- Default: null
- Type: Path

A path to a file containing one or multiple Certificate Authority signing certificates. Similar to the `ca` setting, but allows for multiple CA's, as well as for the CA information to be stored in a file on disk.

​	指向一个包含一个或多个证书颁发机构签名证书的文件的路径。类似于 `ca` 设置，但允许多个CA，并且可以将CA信息存储在磁盘上的文件中。

#### `call`

- Default: ""
- Type: String

Optional companion option for `npm exec`, `npx` that allows for specifying a custom command to be run along with the installed packages.

​	`npm exec` 、 `npx` 的可选伴随选项，允许指定要与安装的软件包一起运行的自定义命令。

```bash
npm exec --package yo --package generator-node --call "yo node"
```

#### `cidr`

- Default: null
- Type: null or String (can be set multiple times)

This is a list of CIDR address to be used when configuring limited access tokens with the `npm token create` command.

​	这是在使用 `npm token create` 命令配置有限访问令牌时要使用的CIDR地址列表。

#### `color`

- Default: true unless the NO_COLOR environ is set to something other than '0'
- 默认值：除非NO_COLOR环境设置为非'0'，否则为true
- Type: "always" or Boolean

If false, never shows colors. If `"always"` then always shows colors. If true, then only prints color codes for tty file descriptors.

​	如果为false，则永不显示颜色。如果为 `"always"` ，则始终显示颜色。如果为true，则仅对tty文件描述符打印颜色代码。

#### `commit-hooks`

- Default: true
- Type: Boolean

Run git commit hooks when using the `npm version` command.

​	在使用 `npm version` 命令时运行git提交钩子。

#### `depth`

- Default: `Infinity` if `--all` is set, otherwise `1`
- 默认值：如果设置了 `--all` ，则为 `Infinity` ，否则为 `1` 
- Type: null or Number

The depth to go when recursing packages for `npm ls`.

​	递归 `npm ls` 包时要到达的深度。

If not set, `npm ls` will show only the immediate dependencies of the root project. If `--all` is set, then npm will show all dependencies by default.

​	如果未设置， `npm ls` 将仅显示根项目的直接依赖项。如果设置了 `--all` ，则npm将默认显示所有依赖项。

#### `description`

- Default: true
- Type: Boolean

Show the description in `npm search`

​	在 `npm search` 中显示描述。

#### `diff`

- Default:
- Type: String (can be set multiple times)

Define arguments to compare in `npm diff`.

​	在 `npm diff` 中定义要比较的参数。

#### `diff-dst-prefix`

- Default: "b/"
- Type: String

Destination prefix to be used in `npm diff` output.

​	在 `npm diff` 输出中使用的目标前缀。

#### `diff-ignore-all-space`

- Default: false
- Type: Boolean

Ignore whitespace when comparing lines in `npm diff`.

​	在 `npm diff` 中比较行时忽略空格。

#### `diff-name-only`

- Default: false
- Type: Boolean

Prints only filenames when using `npm diff`.

​	在使用 `npm diff` 时仅打印文件名。

#### `diff-no-prefix`

- Default: false
- Type: Boolean

Do not show any source or destination prefix in `npm diff` output.

​	在 `npm diff` 输出中不显示任何源或目标前缀。

Note: this causes `npm diff` to ignore the `--diff-src-prefix` and `--diff-dst-prefix` configs.

注意：这会导致 `npm diff` 忽略 `--diff-src-prefix` 和 `--diff-dst-prefix` 配置。

#### `diff-src-prefix`

- Default: "a/"
- Type: String

Source prefix to be used in `npm diff` output.

​	在 `npm diff` 输出中使用的源前缀。

#### `diff-text`

- Default: false
- Type: Boolean

Treat all files as text in `npm diff`.

​	在 `npm diff` 中将所有文件视为文本。

#### `diff-unified`

- Default: 3
- Type: Number

The number of lines of context to print in `npm diff`.

​	在 `npm diff` 中打印的上下文行数。

#### `dry-run`

- Default: false
- Type: Boolean

Indicates that you don't want npm to make any changes and that it should only report what it would have done. This can be passed into any of the commands that modify your local installation, eg, `install`, `update`, `dedupe`, `uninstall`, as well as `pack` and `publish`.

​	表示您不希望npm进行任何更改，它只会报告它将要执行的操作。这可以传递给修改本地安装的任何命令，例如 `install` 、 `update` 、 `dedupe` 、 `uninstall` ，以及 `pack` 和 `publish` 。

Note: This is NOT honored by other network related commands, eg `dist-tags`, `owner`, etc.

注意：其他与网络相关的命令（如 `dist-tags` 、 `owner` 等）不会遵守此选项。

#### `editor`

- Default: The EDITOR or VISUAL environment variables, or '%SYSTEMROOT%\notepad.exe' on Windows, or 'vi' on Unix systems
- 默认值：编辑器或VISUAL环境变量，或Windows上的'%SYSTEMROOT%\notepad.exe'，Unix系统上的'vi'
- Type: String

The command to run for `npm edit` and `npm config edit`.

​	用于 `npm edit` 和 `npm config edit` 的命令。

#### `engine-strict`

- Default: false
- Type: Boolean

If set to true, then npm will stubbornly refuse to install (or even consider installing) any package that claims to not be compatible with the current Node.js version.

​	如果设置为true，则npm将坚决拒绝安装（甚至考虑安装）任何声称与当前Node.js版本不兼容的软件包。

This can be overridden by setting the `--force` flag.

​	这可以通过设置 `--force` 标志来覆盖。

#### `fetch-retries`

- Default: 2
- Type: Number

The "retries" config for the `retry` module to use when fetching packages from the registry.

​	用于从注册表获取软件包时， `retry` 模块使用的“retries”配置。

npm will retry idempotent read requests to the registry in the case of network failures or 5xx HTTP errors.

​	在网络故障或5xx HTTP错误的情况下，npm会重试幂等读请求到注册表。

#### `fetch-retry-factor`

- Default: 10
- Type: Number

The "factor" config for the `retry` module to use when fetching packages.

​	用于获取软件包时， `retry` 模块使用的“factor”配置。

#### `fetch-retry-maxtimeout`

- Default: 60000 (1 minute)
- Type: Number

The "maxTimeout" config for the `retry` module to use when fetching packages.

​	用于获取软件包时， `retry` 模块使用的“maxTimeout”配置。

#### `fetch-retry-mintimeout`

- Default: 10000 (10 seconds)
- Type: Number

The "minTimeout" config for the `retry` module to use when fetching packages.

​	用于获取软件包时， `retry` 模块使用的“minTimeout”配置。

#### `fetch-timeout`

- Default: 300000 (5 minutes)
- Type: Number

The maximum amount of time to wait for HTTP requests to complete.

​	等待HTTP请求完成的最长时间。

#### `force`

- Default: false
- Type: Boolean

Removes various protections against unfortunate side effects, common mistakes, unnecessary performance degradation, and malicious input.

​	删除各种保护措施，以防止不幸的副作用、常见的错误、不必要的性能降级和恶意输入。

- Allow clobbering non-npm files in global installs.
- 允许在全局安装中覆盖非npm文件。
- Allow the `npm version` command to work on an unclean git repository.
- 允许在不干净的git仓库上工作 `npm version` 命令。
- Allow deleting the cache folder with `npm cache clean`.
- 允许使用 `npm cache clean` 删除缓存文件夹。
- Allow installing packages that have an `engines` declaration requiring a different version of npm.
- 允许安装具有 `engines` 声明要求不同版本的npm的软件包。
- Allow installing packages that have an `engines` declaration requiring a different version of `node`, even if `--engine-strict` is enabled.
- 允许安装具有 `engines` 声明要求不同版本的 `node` 的软件包，即使启用了 `--engine-strict` 。
- Allow `npm audit fix` to install modules outside your stated dependency range (including SemVer-major changes).
- 允许 `npm audit fix` 在超出声明的依赖范围（包括SemVer-major更改）时安装模块。
- Allow unpublishing all versions of a published package.
- 允许取消发布已发布软件包的所有版本。
- Allow conflicting peerDependencies to be installed in the root project.
- 允许在根项目中安装冲突的peerDependencies。
- Implicitly set `--yes` during `npm init`.
- 在 `npm init` 期间隐式设置 `--yes` 。
- Allow clobbering existing values in `npm pkg`
- 允许覆盖 `npm pkg` 中现有的值。
- Allow unpublishing of entire packages (not just a single version).
- 允许取消发布整个软件包（而不仅仅是单个版本）。

If you don't have a clear idea of what you want to do, it is strongly recommended that you do not use this option!

​	如果您对自己想要做什么没有明确的想法，强烈建议不要使用此选项！

#### `foreground-scripts`

- Default: false
- Type: Boolean

Run all build scripts (ie, `preinstall`, `install`, and `postinstall`) scripts for installed packages in the foreground process, sharing standard input, output, and error with the main npm process.

​	在前台进程中运行所有构建脚本（例如 `preinstall` 、 `install` 和 `postinstall` ），与主npm进程共享标准输入、输出和错误。

Note that this will generally make installs run slower, and be much noisier, but can be useful for debugging.

请注意，这通常会使安装速度变慢，并且会产生更多的输出，但对于调试非常有用。

#### `format-package-lock`

- Default: true
- Type: Boolean

Format `package-lock.json` or `npm-shrinkwrap.json` as a human readable file.

​	将 `package-lock.json` 或 `npm-shrinkwrap.json` 格式化为可读的文件。

#### `fund`

- Default: true
- Type: Boolean

When "true" displays the message at the end of each `npm install` acknowledging the number of dependencies looking for funding. See [`npm fund`](https://docs.npmjs.com/cli/v10/commands/npm-fund) for details.

​	当设置为"true"时，在每次 `npm install` 结束时显示一条消息，确认有多少个依赖项正在寻找资助。有关详细信息，请参见[ `npm fund` ](https://docs.npmjs.com/cli/v10/commands/npm-fund)。

#### `git`

- Default: "git"
- Type: String

The command to use for git commands. If git is installed on the computer, but is not in the `PATH`, then set this to the full path to the git binary.

​	用于git命令的命令。如果计算机上安装了git，但不在 `PATH` 中，则将其设置为git二进制文件的完整路径。

#### `git-tag-version`

- Default: true
- Type: Boolean

Tag the commit when using the `npm version` command. Setting this to false results in no commit being made at all.

​	在使用 `npm version` 命令时对提交进行标记。将其设置为false将导致根本不进行提交。

#### `global`

- Default: false
- Type: Boolean

Operates in "global" mode, so that packages are installed into the `prefix` folder instead of the current working directory. See [folders](https://docs.npmjs.com/cli/v10/configuring-npm/folders) for more on the differences in behavior.

​	以“全局”模式运行，因此软件包将安装到 `prefix` 文件夹中，而不是当前工作目录。有关行为差异的更多信息，请参见[folders](https://docs.npmjs.com/cli/v10/configuring-npm/folders)。

- packages are installed into the `{prefix}/lib/node_modules` folder, instead of the current working directory.
- 软件包将安装到 `{prefix}/lib/node_modules` 文件夹中，而不是当前工作目录。
- bin files are linked to `{prefix}/bin`
- bin文件将链接到 `{prefix}/bin` 
- man pages are linked to `{prefix}/share/man`
- man页面将链接到 `{prefix}/share/man` 

#### `globalconfig`

- Default: The global --prefix setting plus 'etc/npmrc'. For example, '/usr/local/etc/npmrc'
- 默认值：全局--prefix设置加上'etc/npmrc'。例如，'/usr/local/etc/npmrc'
- Type: Path

The config file to read for global config options.

​	用于全局配置选项的配置文件。

#### `heading`

- Default: "npm"
- Type: String

The string that starts all the debugging log output.

​	开始所有调试日志输出的字符串。

#### `https-proxy`

- Default: null
- Type: null or URL

A proxy to use for outgoing https requests. If the `HTTPS_PROXY` or `https_proxy` or `HTTP_PROXY` or `http_proxy` environment variables are set, proxy settings will be honored by the underlying `make-fetch-happen` library.

​	用于传出https请求的代理。如果设置了 `HTTPS_PROXY` 或 `https_proxy` 或 `HTTP_PROXY` 或 `http_proxy` 环境变量，则代理设置将由底层的 `make-fetch-happen` 库使用。

#### `if-present`

- Default: false
- Type: Boolean

If true, npm will not exit with an error code when `run-script` is invoked for a script that isn't defined in the `scripts` section of `package.json`. This option can be used when it's desirable to optionally run a script when it's present and fail if the script fails. This is useful, for example, when running scripts that may only apply for some builds in an otherwise generic CI setup.

​	如果为true，则在调用 `run-script` 时，当脚本在 `package.json` 的 `scripts` 部分中未定义时，npm不会退出错误代码。当希望在脚本存在时可选地运行脚本并且如果脚本失败则失败时，可以使用此选项。这在一个通用的CI设置中非常有用，例如只适用于某些构建的脚本。

This value is not exported to the environment for child processes.

​	此值不会导出到子进程的环境中。

#### `ignore-scripts`

- Default: false
- Type: Boolean

If true, npm does not run scripts specified in package.json files.

​	如果为true，则npm不会运行package.json文件中指定的脚本。

Note that commands explicitly intended to run a particular script, such as `npm start`, `npm stop`, `npm restart`, `npm test`, and `npm run-script` will still run their intended script if `ignore-scripts` is set, but they will *not* run any pre- or post-scripts.

请注意，明确用于运行特定脚本的命令，例如 `npm start` 、 `npm stop` 、 `npm restart` 、 `npm test` 和 `npm run-script` ，如果设置了 `ignore-scripts` ，它们仍然会运行其预期的脚本，但不会运行任何前置或后置脚本。

#### `include`

- Default:
- Type: "prod", "dev", "optional", or "peer" (can be set multiple times)
- 类型： "prod"、"dev"、"optional"或"peer"（可以多次设置）

Option that allows for defining which types of dependencies to install.

​	允许定义要安装的依赖项的类型。

This is the inverse of `--omit=<type>`.

​	这是 `--omit=<type>` 的相反。

Dependency types specified in `--include` will not be omitted, regardless of the order in which omit/include are specified on the command-line.

​	在命令行中指定的省略/包含的顺序不会影响省略/包含的顺序。

#### `include-staged`

- Default: false
- Type: Boolean

Allow installing "staged" published packages, as defined by [npm RFC PR #92](https://github.com/npm/rfcs/pull/92).

​	允许安装“staged”已发布的软件包，如[npm RFC PR＃92](https://github.com/npm/rfcs/pull/92)所定义。

This is experimental, and not implemented by the npm public registry.

​	这是实验性的，npm公共注册表不支持。

#### `include-workspace-root`

- Default: false
- Type: Boolean

Include the workspace root when workspaces are enabled for a command.

​	在启用工作区的情况下，包含工作区根目录时，npm在运行命令时将工作区与根项目一起操作。

When false, specifying individual workspaces via the `workspace` config, or all workspaces via the `workspaces` flag, will cause npm to operate only on the specified workspaces, and not on the root project.

​	当设置为false时，通过 `workspace` 配置指定单个工作区，或通过 `workspaces` 标志指定所有工作区，将导致npm仅操作指定的工作区，而不操作根项目。

This value is not exported to the environment for child processes.

​	此值不会导出到子进程的环境中。

#### `init-author-email`

- Default: ""
- Type: String

The value `npm init` should use by default for the package author's email.

​	`npm init` 默认使用的包作者的电子邮件值。

#### `init-author-name`

- Default: ""
- Type: String

The value `npm init` should use by default for the package author's name.

​	`npm init` 默认使用的包作者的名称值。

#### `init-author-url`

- Default: ""
- Type: "" or URL

The value `npm init` should use by default for the package author's homepage.

​	`npm init` 默认使用的包作者的主页值。

#### `init-license`

- Default: "ISC"
- Type: String

The value `npm init` should use by default for the package license.

​	`npm init` 默认使用的包许可证值。

#### `init-module`

- Default: "~/.npm-init.js"
- Type: Path

A module that will be loaded by the `npm init` command. See the documentation for the [init-package-json](https://github.com/npm/init-package-json) module for more information, or [npm init](https://docs.npmjs.com/cli/v10/commands/npm-init).

​	将由 `npm init` 命令加载的模块。有关更多信息，请参见[init-package-json](https://github.com/npm/init-package-json)模块的文档，或[npm init](https://docs.npmjs.com/cli/v10/commands/npm-init)。

#### `init-version`

- Default: "1.0.0"
- Type: SemVer string

The value that `npm init` should use by default for the package version number, if not already set in package.json.

​	如果在package.json中尚未设置版本号，则 `npm init` 默认使用的包版本号。

#### `install-links`

- Default: false
- Type: Boolean

When set file: protocol dependencies will be packed and installed as regular dependencies instead of creating a symlink. This option has no effect on workspaces.

​	当设置为file:协议依赖项时，将其打包并安装为常规依赖项，而不是创建符号链接。此选项对工作区没有影响。

#### `install-strategy`

- Default: "hoisted"
- Type: "hoisted", "nested", "shallow", or "linked"

Sets the strategy for installing packages in node_modules. hoisted (default): Install non-duplicated in top-level, and duplicated as necessary within directory structure. nested: (formerly --legacy-bundling) install in place, no hoisting. shallow (formerly --global-style) only install direct deps at top-level. linked: (experimental) install in node_modules/.store, link in place, unhoisted.

​	设置在node_modules中安装软件包的策略。hoisted（默认）：在顶层安装不重复的软件包，并根据需要在目录结构中复制。nested：（以前称为--legacy-bundling）原地安装，不进行提升。shallow（以前称为--global-style）仅在顶层安装直接依赖项。linked：（实验性）在node_modules/.store中安装，链接在原地，不进行提升。

#### `json`

- Default: false
- Type: Boolean

Whether or not to output JSON data, rather than the normal output.

​	是否输出JSON数据，而不是正常输出。

- In `npm pkg set` it enables parsing set values with JSON.parse() before saving them to your `package.json`.
- 在 `npm pkg set` 中，它使得在将值保存到 `package.json` 之前使用JSON.parse()解析设置的值。

Not supported by all npm commands.

​	不是所有的npm命令都支持。

#### `legacy-peer-deps`

- Default: false
- Type: Boolean

Causes npm to completely ignore `peerDependencies` when building a package tree, as in npm versions 3 through 6.

​	导致npm在构建软件包树时完全忽略 `peerDependencies` ，就像npm版本3到6一样。

If a package cannot be installed because of overly strict `peerDependencies` that collide, it provides a way to move forward resolving the situation.

​	如果由于过于严格的 `peerDependencies` 而无法安装软件包，它提供了一种解决问题的方法。

This differs from `--omit=peer`, in that `--omit=peer` will avoid unpacking `peerDependencies` on disk, but will still design a tree such that `peerDependencies` *could* be unpacked in a correct place.

​	这与 `--omit=peer` 不同， `--omit=peer` 将避免在磁盘上解压 `peerDependencies` ，但仍将设计树，以便 `peerDependencies`  *可以*在正确的位置解压。

Use of `legacy-peer-deps` is not recommended, as it will not enforce the `peerDependencies` contract that meta-dependencies may rely on.

​	不建议使用 `legacy-peer-deps` ，因为它不会强制执行元依赖项可能依赖的 `peerDependencies` 合同。

#### `link`

- Default: false
- Type: Boolean

Used with `npm ls`, limiting output to only those packages that are linked.

​	与 `npm ls` 一起使用，将输出限制为仅链接的软件包。

#### `local-address`

- Default: null
- Type: IP Address

The IP address of the local interface to use when making connections to the npm registry. Must be IPv4 in versions of Node prior to 0.12.

​	在进行与npm注册表的连接时使用的本地接口的IP地址。在Node 0.12之前的版本中，必须为IPv4。

#### `location`

- Default: "user" unless `--global` is passed, which will also set this value to "global"
- 默认值：如果传递了 `--global` ，则为"user"，否则也将此值设置为"global"
- Type: "global", "user", or "project"

When passed to `npm config` this refers to which config file to use.

​	当传递给 `npm config` 时，这是指要使用的配置文件。

When set to "global" mode, packages are installed into the `prefix` folder instead of the current working directory. See [folders](https://docs.npmjs.com/cli/v10/configuring-npm/folders) for more on the differences in behavior.

​	在设置为“global”模式时，软件包将安装到 `prefix` 文件夹中，而不是当前工作目录。有关行为差异的更多信息，请参见[folders](https://docs.npmjs.com/cli/v10/configuring-npm/folders)。

- packages are installed into the `{prefix}/lib/node_modules` folder, instead of the current working directory.
- 软件包将安装到 `{prefix}/lib/node_modules` 文件夹中，而不是当前工作目录。
- bin files are linked to `{prefix}/bin`
- bin文件将链接到 `{prefix}/bin` 
- man pages are linked to `{prefix}/share/man`
- man页面将链接到 `{prefix}/share/man` 

#### `lockfile-version`

- Default: Version 3 if no lockfile, auto-converting v1 lockfiles to v3, otherwise maintain current lockfile version.
- 默认值：如果没有lockfile，则为3，自动将v1 lockfile转换为v3，否则保持当前lockfile版本。
- Type: null, 1, 2, 3, "1", "2", or "3"

Set the lockfile format version to be used in package-lock.json and npm-shrinkwrap-json files. Possible options are:

​	设置要在package-lock.json和npm-shrinkwrap-json文件中使用的lockfile格式版本。可能的选项有：

1: The lockfile version used by npm versions 5 and 6. Lacks some data that is used during the install, resulting in slower and possibly less deterministic installs. Prevents lockfile churn when interoperating with older npm versions.

1：npm版本5和6使用的lockfile版本。缺少一些在安装过程中使用的数据，导致安装速度较慢，可能不太确定。在与旧版npm版本进行互操作时，可以防止lockfile变动。

2: The default lockfile version used by npm version 7 and 8. Includes both the version 1 lockfile data and version 3 lockfile data, for maximum determinism and interoperability, at the expense of more bytes on disk.

2：npm版本7和8使用的默认lockfile版本。包括版本1 lockfile数据和版本3 lockfile数据，以实现最大的确定性和互操作性，但磁盘上的字节数更多。

3: Only the new lockfile information introduced in npm version 7. Smaller on disk than lockfile version 2, but not interoperable with older npm versions. Ideal if all users are on npm version 7 and higher.

3：仅npm版本7中引入的新lockfile信息。磁盘上的大小比lockfile版本2小，但与旧版npm版本不互操作。如果所有用户都在npm版本7及更高版本上，则是理想的选择。

#### `loglevel`

- Default: "notice"
- Type: "silent", "error", "warn", "notice", "http", "info", "verbose", or "silly"

What level of logs to report. All logs are written to a debug log, with the path to that file printed if the execution of a command fails.

​	要报告的日志级别。所有日志都写入调试日志中，如果命令执行失败，则打印该文件的路径。

Any logs of a higher level than the setting are shown. The default is "notice".

​	显示高于设置级别的所有日志。默认值为"notice"。

See also the `foreground-scripts` config.

​	另请参阅 `foreground-scripts` 配置。

#### `logs-dir`

- Default: A directory named `_logs` inside the cache
- 默认值：缓存内名为 `_logs` 的目录
- Type: null or Path

The location of npm's log directory. See [`npm logging`](https://docs.npmjs.com/cli/v10/using-npm/logging) for more information.

​	npm日志目录的位置。有关更多信息，请参见[ `npm logging` ](https://docs.npmjs.com/cli/v10/using-npm/logging)。

#### `logs-max`

- Default: 10
- Type: Number

The maximum number of log files to store.

​	要存储的日志文件的最大数量。

If set to 0, no log files will be written for the current run.

​	如果设置为0，则不会为当前运行写入日志文件。

#### `long`

- Default: false
- Type: Boolean

Show extended information in `ls`, `search`, and `help-search`.

​	在 `ls` 、 `search` 和 `help-search` 中显示扩展信息。

#### `maxsockets`

- Default: 15
- Type: Number

The maximum number of connections to use per origin (protocol/host/port combination).

​	每个源（协议/主机/端口组合）使用的最大连接数。

#### `message`

- Default: "%s"
- Type: String

Commit message which is used by `npm version` when creating version commit.

​	在创建版本提交时， `npm version` 使用的提交消息。

Any "%s" in the message will be replaced with the version number.

​	消息中的任何“%s”都将替换为版本号。

#### `node-options`

- Default: null
- Type: null or String

Options to pass through to Node.js via the `NODE_OPTIONS` environment variable. This does not impact how npm itself is executed but it does impact how lifecycle scripts are called.

​	通过 `NODE_OPTIONS` 环境变量将选项传递给Node.js。这不会影响npm本身的执行方式，但会影响如何调用生命周期脚本。

#### `noproxy`

- Default: The value of the NO_PROXY environment variable
- 默认值：NO_PROXY环境变量的值
- Type: String (can be set multiple times)

Domain extensions that should bypass any proxies.

​	应绕过任何代理的域扩展名。

Also accepts a comma-delimited string.

​	还接受逗号分隔的字符串。

#### `offline`

- Default: false
- Type: Boolean

Force offline mode: no network requests will be done during install. To allow the CLI to fill in missing cache data, see `--prefer-offline`.

​	强制离线模式：在安装过程中不进行任何网络请求。要允许 CLI 填充缺失的缓存数据，请参阅  `--prefer-offline` 。

#### `omit`

- Default: 'dev' if the `NODE_ENV` environment variable is set to 'production', otherwise empty.
- 默认值：如果  `NODE_ENV`  环境变量设置为 'production'，则为 'dev'，否则为空。
- Type: "dev", "optional", or "peer" (can be set multiple times)

Dependency types to omit from the installation tree on disk.

​	要从安装树中省略的依赖项类型。

Note that these dependencies *are* still resolved and added to the `package-lock.json` or `npm-shrinkwrap.json` file. They are just not physically installed on disk.

请注意，这些依赖项仍然会被解析并添加到  `package-lock.json`  或  `npm-shrinkwrap.json`  文件中。它们只是不会在磁盘上实际安装。

If a package type appears in both the `--include` and `--omit` lists, then it will be included.

​	如果一个包类型在  `--include`  和  `--omit`  列表中都出现，则将包含该包。

If the resulting omit list includes `'dev'`, then the `NODE_ENV` environment variable will be set to `'production'` for all lifecycle scripts.

​	如果结果省略列表包括  `'dev'` ，则  `NODE_ENV`  环境变量将被设置为  `'production'` ，用于所有生命周期脚本。

#### `omit-lockfile-registry-resolved`

- Default: false
- Type: Boolean

This option causes npm to create lock files without a `resolved` key for registry dependencies. Subsequent installs will need to resolve tarball endpoints with the configured registry, likely resulting in a longer install time.

​	此选项会导致 npm 在创建没有注册表依赖项的  `resolved`  键的锁文件时。随后的安装将需要使用配置的注册表解析 tarball 端点，这可能会导致更长的安装时间。

#### `otp`

- Default: null
- Type: null or String

This is a one-time password from a two-factor authenticator. It's needed when publishing or changing package permissions with `npm access`.

​	这是来自双因素认证器的一次性密码。在发布或使用  `npm access`  更改软件包权限时需要。

If not set, and a registry response fails with a challenge for a one-time password, npm will prompt on the command line for one.

​	如果未设置，并且注册表响应因一次性密码的挑战而失败，npm 将在命令行上提示输入密码。

#### `pack-destination`

- Default: "."
- Type: String

Directory in which `npm pack` will save tarballs.

​	`npm pack`  命令将保存 tarball 的目录。

#### `package`

- Default:
- Type: String (can be set multiple times)

The package or packages to install for [`npm exec`](https://docs.npmjs.com/cli/v10/commands/npm-exec)

​	要为 [ `npm exec` ](https://docs.npmjs.com/cli/v10/commands/npm-exec) 安装的包。

#### `package-lock`

- Default: true
- Type: Boolean

If set to false, then ignore `package-lock.json` files when installing. This will also prevent *writing* `package-lock.json` if `save` is true.

​	如果设置为 false，则在安装时忽略  `package-lock.json`  文件。如果  `save`  为 true，这也将阻止写入  `package-lock.json` 。

#### `package-lock-only`

- Default: false
- Type: Boolean

If set to true, the current operation will only use the `package-lock.json`, ignoring `node_modules`.

​	如果设置为 true，则当前操作仅使用  `package-lock.json` ，忽略  `node_modules` 。

For `update` this means only the `package-lock.json` will be updated, instead of checking `node_modules` and downloading dependencies.

​	对于  `update` ，这意味着仅更新  `package-lock.json` ，而不是检查  `node_modules`  并下载依赖项。

For `list` this means the output will be based on the tree described by the `package-lock.json`, rather than the contents of `node_modules`.

​	对于  `list` ，这意味着输出将基于  `package-lock.json`  描述的树，而不是基于  `node_modules`  的内容。

#### `parseable`

- Default: false
- Type: Boolean

Output parseable results from commands that write to standard output. For `npm search`, this will be tab-separated table format.

​	从写入标准输出的命令中输出可解析的结果。对于  `npm search` ，这将是制表符分隔的表格格式。

#### `prefer-dedupe`

- Default: false
- Type: Boolean

Prefer to deduplicate packages if possible, rather than choosing a newer version of a dependency.

​	如果可能，优先使用去重包，而不是选择依赖项的较新版本。

#### `prefer-offline`

- Default: false
- Type: Boolean

If true, staleness checks for cached data will be bypassed, but missing data will be requested from the server. To force full offline mode, use `--offline`.

​	如果为 true，则绕过对缓存数据的过时检查，但会从服务器请求缺失的数据。要强制完全离线模式，请使用  `--offline` 。

#### `prefer-online`

- Default: false
- Type: Boolean

If true, staleness checks for cached data will be forced, making the CLI look for updates immediately even for fresh package data.

​	如果为 true，则强制对缓存数据进行过时检查，使 CLI 立即查找更新，即使对于新的包数据也是如此。

#### `prefix`

- Default: In global mode, the folder where the node executable is installed. Otherwise, the nearest parent folder containing either a package.json file or a node_modules folder.
- 默认值：在全局模式下，为安装了 node 可执行文件的文件夹。否则，为最近的包含 package.json 文件或 node_modules 文件夹的父文件夹。
- Type: Path

The location to install global items. If set on the command line, then it forces non-global commands to run in the specified folder.

​	安装全局项的位置。如果在命令行上设置了该值，则会强制非全局命令在指定的文件夹中运行。

#### `preid`

- Default: ""
- Type: String

The "prerelease identifier" to use as a prefix for the "prerelease" part of a semver. Like the `rc` in `1.2.0-rc.8`.

​	用作 semver 的 "prerelease" 部分前缀的 "prerelease 标识符"。例如在  `1.2.0-rc.8`  中的  `rc` 。

#### `progress`

- Default: `true` unless running in a known CI system
- Type: Boolean

When set to `true`, npm will display a progress bar during time intensive operations, if `process.stderr` is a TTY.

​	当设置为  `true`  时，npm 在耗时操作期间显示进度条，如果  `process.stderr`  是 TTY。

Set to `false` to suppress the progress bar.

​	将其设置为  `false`  可以抑制进度条。

#### `provenance`

- Default: false
- Type: Boolean

When publishing from a supported cloud CI/CD system, the package will be publicly linked to where it was built and published from.

​	从受支持的云 CI/CD 系统发布时，将软件包公开链接到构建和发布的位置。

This config can not be used with: `provenance-file`

​	此配置不能与  `provenance-file`  一起使用。

#### `provenance-file`

- Default: null
- Type: Path

When publishing, the provenance bundle at the given path will be used.

​	在发布时，将使用给定路径的 provenance bundle。

This config can not be used with: `provenance`

​	此配置不能与  `provenance`  一起使用。

#### `proxy`

- Default: null
- Type: null, false, or URL

A proxy to use for outgoing http requests. If the `HTTP_PROXY` or `http_proxy` environment variables are set, proxy settings will be honored by the underlying `request` library.

​	用于出站 http 请求的代理。如果设置了  `HTTP_PROXY`  或  `http_proxy`  环境变量，则  `request`  库将遵守代理设置。

#### `read-only`

- Default: false
- Type: Boolean

This is used to mark a token as unable to publish when configuring limited access tokens with the `npm token create` command.

​	用于将令牌标记为无法发布的配置项，用于使用  `npm token create`  命令配置受限访问令牌时。

#### `rebuild-bundle`

- Default: true
- Type: Boolean

Rebuild bundled dependencies after installation.

​	安装后重新构建捆绑的依赖项。

#### `registry`

- Default: "https://registry.npmjs.org/"
- Type: URL

The base URL of the npm registry.

​	npm 注册表的基本 URL。

#### `replace-registry-host`

- Default: "npmjs"
- Type: "npmjs", "never", "always", or String

Defines behavior for replacing the registry host in a lockfile with the configured registry.

​	定义替换锁文件中注册表主机的行为。

The default behavior is to replace package dist URLs from the default registry (https://registry.npmjs.org) to the configured registry. If set to "never", then use the registry value. If set to "always", then replace the registry host with the configured host every time.

​	默认行为是将包分发 URL 从默认注册表（https://registry.npmjs.org）替换为配置的注册表。如果设置为 "never"，则使用注册表值。如果设置为 "always"，则每次都将注册表主机替换为配置的主机。

You may also specify a bare hostname (e.g., "registry.npmjs.org").

​	您还可以指定一个裸主机名（例如 "registry.npmjs.org"）。

#### `save`

- Default: `true` unless when using `npm update` where it defaults to `false`
- 默认值：如果使用  `npm update` ，则为  `false` ，否则为  `true` 
- Type: Boolean

Save installed packages to a `package.json` file as dependencies.

​	将安装的软件包保存到  `package.json`  文件中作为依赖项。

When used with the `npm rm` command, removes the dependency from `package.json`.

​	在使用  `npm rm`  命令时，从  `package.json`  中删除依赖项。

Will also prevent writing to `package-lock.json` if set to `false`.

​	如果设置为  `false` ，还会阻止写入  `package-lock.json` 。

#### `save-bundle`

- Default: false
- Type: Boolean

If a package would be saved at install time by the use of `--save`, `--save-dev`, or `--save-optional`, then also put it in the `bundleDependencies` list.

​	如果使用  `--save` 、 `--save-dev`  或  `--save-optional`  保存软件包，则将其也放入  `bundleDependencies`  列表中。

Ignored if `--save-peer` is set, since peerDependencies cannot be bundled.

​	如果设置了  `--save-peer` ，则会忽略此选项，因为无法捆绑 peerDependencies。

#### `save-dev`

- Default: false
- Type: Boolean

Save installed packages to a package.json file as `devDependencies`.

​	将安装的软件包保存到  `package.json`  文件中作为  `devDependencies` 。

#### `save-exact`

- Default: false
- Type: Boolean

Dependencies saved to package.json will be configured with an exact version rather than using npm's default semver range operator.

​	将保存到 package.json 的依赖项配置为具有精确版本，而不是使用 npm 的默认 semver 范围运算符。

#### `save-optional`

- Default: false
- Type: Boolean

Save installed packages to a package.json file as `optionalDependencies`.

​	将安装的软件包保存到  `package.json`  文件中作为  `optionalDependencies` 。

#### `save-peer`

- Default: false
- Type: Boolean

Save installed packages to a package.json file as `peerDependencies`

​	将安装的软件包保存到  `package.json`  文件中作为  `peerDependencies` 

#### `save-prefix`

- Default: "^"
- Type: String

Configure how versions of packages installed to a package.json file via `--save` or `--save-dev` get prefixed.

​	配置通过  `--save`  或  `--save-dev`  将安装到 package.json 文件中的软件包的版本前缀。

For example if a package has version `1.2.3`, by default its version is set to `^1.2.3` which allows minor upgrades for that package, but after `npm config set save-prefix='~'` it would be set to `~1.2.3` which only allows patch upgrades.

​	例如，如果一个软件包的版本为  `1.2.3` ，默认情况下，其版本设置为  `^1.2.3` ，这允许对该软件包进行次要升级，但在  `npm config set save-prefix='~'`  之后，它将设置为  `~1.2.3` ，这仅允许对该软件包进行补丁升级。

#### `save-prod`

- Default: false
- Type: Boolean

Save installed packages into `dependencies` specifically. This is useful if a package already exists in `devDependencies` or `optionalDependencies`, but you want to move it to be a non-optional production dependency.

​	将安装的软件包保存到  `dependencies`  中。如果软件包已存在于  `devDependencies`  或  `optionalDependencies`  中，但您希望将其移动为非可选的生产依赖项，则这很有用。

This is the default behavior if `--save` is true, and neither `--save-dev` or `--save-optional` are true.

​	如果  `--save`  为 true，且  `--save-dev`  或  `--save-optional`  都不为 true，则为默认行为。

#### `scope`

- Default: the scope of the current project, if any, or ""
- 默认值：当前项目的范围（如果有），否则为 ""
- Type: String

Associate an operation with a scope for a scoped registry.

​	将操作与作用域关联，用于作用域注册表。

Useful when logging in to or out of a private registry:

​	在登录到或退出私有注册表时非常有用：

```
# log in, linking the scope to the custom registry
# 登录，将作用域与自定义注册表链接起来
npm login --scope=@mycorp --registry=https://registry.mycorp.com

# log out, removing the link and the auth token
# 登出，删除链接和授权令牌
npm logout --scope=@mycorp
```

This will cause `@mycorp` to be mapped to the registry for future installation of packages specified according to the pattern `@mycorp/package`.

​	这将导致  `@mycorp`  被映射到注册表，以便将来根据模式  `@mycorp/package`  指定的包安装到注册表。

This will also cause `npm init` to create a scoped package.

​	这还将导致  `npm init`  创建一个作用域包。

```
# accept all defaults, and create a package named "@foo/whatever",
# 接受所有默认值，并创建名为 "@foo/whatever" 的包，
# instead of just named "whatever"
# 而不仅仅是名为 "whatever"
npm init --scope=@foo --yes
```

#### `script-shell`

- Default: '/bin/sh' on POSIX systems, 'cmd.exe' on Windows
- 默认值：在 POSIX 系统上为 '/bin/sh'，在 Windows 上为 'cmd.exe'
- Type: null or String

The shell to use for scripts run with the `npm exec`, `npm run` and `npm init <package-spec>` commands.

​	用于使用  `npm exec` 、 `npm run`  和  `npm init <package-spec>`  命令运行的脚本的 shell。

#### `searchexclude`

- Default: ""
- Type: String

Space-separated options that limit the results from search.

​	用于限制搜索结果的选项，以空格分隔。

#### `searchlimit`

- Default: 20
- Type: Number

Number of items to limit search results to. Will not apply at all to legacy searches.

​	限制搜索结果的项目数量。不适用于传统搜索。

#### `searchopts`

- Default: ""
- Type: String

Space-separated options that are always passed to search.

​	空格分隔的选项，始终传递给搜索。

#### `searchstaleness`

- Default: 900
- Type: Number

The age of the cache, in seconds, before another registry request is made if using legacy search endpoint.

​	缓存的时间（以秒为单位），如果使用传统的搜索端点，则在进行另一个注册表请求之前。

#### `shell`

- Default: SHELL environment variable, or "bash" on Posix, or "cmd.exe" on Windows
- 默认值：SHELL环境变量，或在Posix上为"bash"，在Windows上为"cmd.exe"
- Type: String

The shell to run for the `npm explore` command.

​	用于运行 `npm explore` 命令的shell。

#### `sign-git-commit`

- Default: false
- Type: Boolean

If set to true, then the `npm version` command will commit the new package version using `-S` to add a signature.

​	如果设置为true，则 `npm version` 命令将使用 `-S` 提交新的包版本。

Note that git requires you to have set up GPG keys in your git configs for this to work properly.

​	请注意，git要求您在git配置中设置了GPG密钥才能正常工作。

#### `sign-git-tag`

- Default: false
- Type: Boolean

If set to true, then the `npm version` command will tag the version using `-s` to add a signature.

​	如果设置为true，则 `npm version` 命令将使用 `-s` 标记版本。

Note that git requires you to have set up GPG keys in your git configs for this to work properly.

​	请注意，git要求您在git配置中设置了GPG密钥才能正常工作。

#### `strict-peer-deps`

- Default: false
- Type: Boolean

If set to `true`, and `--legacy-peer-deps` is not set, then *any* conflicting `peerDependencies` will be treated as an install failure, even if npm could reasonably guess the appropriate resolution based on non-peer dependency relationships.

​	如果设置为 `true` ，且未设置 `--legacy-peer-deps` ，则*任何*冲突的 `peerDependencies` 都将被视为安装失败，即使npm可以根据非peer依赖关系合理猜测适当的解决方案。

By default, conflicting `peerDependencies` deep in the dependency graph will be resolved using the nearest non-peer dependency specification, even if doing so will result in some packages receiving a peer dependency outside the range set in their package's `peerDependencies` object.

​	默认情况下，深层的冲突 `peerDependencies` 将使用最近的非peer依赖规范来解决，即使这样做会导致某些包在其包的 `peerDependencies` 对象中设置的范围之外接收到peer依赖。

When such an override is performed, a warning is printed, explaining the conflict and the packages involved. If `--strict-peer-deps` is set, then this warning is treated as a failure.

​	当执行此类覆盖时，将打印警告，解释冲突和涉及的包。如果设置了 `--strict-peer-deps` ，则此警告将被视为失败。

#### `strict-ssl`

- Default: true
- Type: Boolean

Whether or not to do SSL key validation when making requests to the registry via https.

​	在通过https请求注册表时，是否进行SSL密钥验证。

See also the `ca` config.

​	另请参阅 `ca` 配置。

#### `tag`

- Default: "latest"
- Type: String

If you ask npm to install a package and don't tell it a specific version, then it will install the specified tag.

​	如果要求npm安装一个包并且没有指定特定版本，则将安装指定的标签。

Also the tag that is added to the package@version specified by the `npm tag` command, if no explicit tag is given.

​	还是 `npm tag` 命令指定的package@version添加的标签，如果没有给出显式标签。

When used by the `npm diff` command, this is the tag used to fetch the tarball that will be compared with the local files by default.

​	在 `npm diff` 命令中使用时，这是用于获取默认情况下与本地文件进行比较的tarball的标签。

#### `tag-version-prefix`

- Default: "v"
- Type: String

If set, alters the prefix used when tagging a new version when performing a version increment using `npm version`. To remove the prefix altogether, set it to the empty string: `""`.

​	如果设置，将更改在执行版本增量时标记新版本时使用的前缀。要完全删除前缀，请将其设置为空字符串："''"。

Because other tools may rely on the convention that npm version tags look like `v1.0.0`, *only use this property if it is absolutely necessary*. In particular, use care when overriding this setting for public packages.

​	因为其他工具可能依赖于npm版本标签的约定，看起来像 `v1.0.0` ，*只有在绝对必要时*才使用此属性。特别是，在为公共包覆盖此设置时要小心。

#### `timing`

- Default: false
- Type: Boolean

If true, writes timing information to a process specific json file in the cache or `logs-dir`. The file name ends with `-timing.json`.

​	如果为true，将计时信息写入缓存或 `logs-dir` 中的特定进程json文件。文件名以 `-timing.json` 结尾。

You can quickly view it with this [json](https://npm.im/json) command line: `cat ~/.npm/_logs/*-timing.json | npm exec -- json -g`.

​	您可以使用此[json](https://npm.im/json)命令行快速查看它： `cat ~/.npm/_logs/*-timing.json | npm exec -- json -g` 。

Timing information will also be reported in the terminal. To suppress this while still writing the timing file, use `--silent`.

​	计时信息还将在终端中报告。要在仍然写入计时文件的同时抑制此信息，请使用 `--silent` 。

#### `umask`

- Default: 0
- Type: Octal numeric string in range 0000..0777 (0..511)
- 类型：八进制数字字符串，范围为0000..0777（0..511）

The "umask" value to use when setting the file creation mode on files and folders.

​	在文件和文件夹上设置文件创建模式时要使用的"umask"值。

Folders and executables are given a mode which is `0o777` masked against this value. Other files are given a mode which is `0o666` masked against this value.

​	文件夹和可执行文件使用的模式是 `0o777` 与该值进行掩码。其他文件使用的模式是 `0o666` 与该值进行掩码。

Note that the underlying system will *also* apply its own umask value to files and folders that are created, and npm does not circumvent this, but rather adds the `--umask` config to it.

​	请注意，底层系统也将对创建的文件和文件夹应用其自己的umask值，npm不会绕过此操作，而是将 `--umask` 配置添加到其中。

Thus, the effective default umask value on most POSIX systems is 0o22, meaning that folders and executables are created with a mode of 0o755 and other files are created with a mode of 0o644.

​	因此，在大多数POSIX系统上的有效默认umask值是0o22，这意味着文件夹和可执行文件的模式为0o755，其他文件的模式为0o644。

#### `unicode`

- Default: false on windows, true on mac/unix systems with a unicode locale, as defined by the `LC_ALL`, `LC_CTYPE`, or `LANG` environment variables.
- 默认值：在Windows上为false，在具有Unicode区域设置的Mac / Unix系统上为true，由 `LC_ALL` ， `LC_CTYPE` 或 `LANG` 环境变量定义。
- Type: Boolean

When set to true, npm uses unicode characters in the tree output. When false, it uses ascii characters instead of unicode glyphs.

​	当设置为true时，npm在树输出中使用Unicode字符。当为false时，它使用ASCII字符而不是Unicode字符。

#### `update-notifier`

- Default: true
- Type: Boolean

Set to false to suppress the update notification when using an older version of npm than the latest.

​	将其设置为false以在使用旧版npm时抑制更新通知。

#### `usage`

- Default: false
- Type: Boolean

Show short usage output about the command specified.

​	显示有关指定命令的简短使用输出。

#### `user-agent`

- Default: "npm/{npm-version} node/{node-version} {platform} {arch} workspaces/{workspaces} {ci}"
- Type: String

Sets the User-Agent request header. The following fields are replaced with their actual counterparts:

​	设置User-Agent请求头。以下字段将替换为实际的对应项：

- `{npm-version}` - The npm version in use
- `{npm-version}`  - 使用的npm版本
- `{node-version}` - The Node.js version in use
- `{node-version}`  - 使用的Node.js版本
- `{platform}` - The value of `process.platform`
- `{platform}`  -  `process.platform` 的值
- `{arch}` - The value of `process.arch`
- `{arch}`  -  `process.arch` 的值
- `{workspaces}` - Set to `true` if the `workspaces` or `workspace` options are set.
- `{workspaces}`  - 如果设置了 `workspaces` 或 `workspace` 选项，则设置为 `true` 。
- `{ci}` - The value of the `ci-name` config, if set, prefixed with `ci/`, or an empty string if `ci-name` is empty.
- `{ci}`  -  `ci-name` 配置的值（如果设置了），前缀为 `ci/` ，如果 `ci-name` 为空，则为空字符串。

#### `userconfig`

- Default: "~/.npmrc"
- Type: Path

The location of user-level configuration settings.

​	用户级配置设置的位置。

This may be overridden by the `npm_config_userconfig` environment variable or the `--userconfig` command line option, but may *not* be overridden by settings in the `globalconfig` file.

​	这可以被 `npm_config_userconfig` 环境变量或 `--userconfig` 命令行选项覆盖，但不能被 `globalconfig` 文件中的设置覆盖。

#### `version`

- Default: false
- Type: Boolean

If true, output the npm version and exit successfully.

​	如果为true，则输出npm版本并成功退出。

Only relevant when specified explicitly on the command line.

​	仅在明确指定在命令行上时才相关。

#### `versions`

- Default: false
- Type: Boolean

If true, output the npm version as well as node's `process.versions` map and the version in the current working directory's `package.json` file if one exists, and exit successfully.

​	如果为true，则输出npm版本以及当前工作目录的 `package.json` 文件中的node的 `process.versions` 映射和版本，并成功退出。

Only relevant when specified explicitly on the command line.

​	仅在明确指定在命令行上时才相关。

#### `viewer`

- Default: "man" on Posix, "browser" on Windows
- 默认值：在Posix上为"man"，在Windows上为"browser"
- Type: String

The program to use to view help content.

​	用于查看帮助内容的程序。

Set to `"browser"` to view html help content in the default web browser.

​	将其设置为 `"browser"` 以在默认的Web浏览器中查看HTML帮助内容。

#### `which`

- Default: null
- Type: null or Number

If there are multiple funding sources, which 1-indexed source URL to open.

​	如果存在多个资助来源，则打开第一个索引为1的源URL。

#### `workspace`

- Default:
- Type: String (can be set multiple times)

Enable running a command in the context of the configured workspaces of the current project while filtering by running only the workspaces defined by this configuration option.

​	启用在当前项目的配置工作区上下文中运行命令，同时通过运行此配置选项定义的工作区进行过滤。

Valid values for the `workspace` config are either:

 	`workspace` 配置的有效值为：

- Workspace names
- 工作区名称
- Path to a workspace directory
- 工作区目录的路径
- Path to a parent workspace directory (will result in selecting all workspaces within that folder)
- 父工作区目录的路径（将选择该文件夹中的所有工作区）

When set for the `npm init` command, this may be set to the folder of a workspace which does not yet exist, to create the folder and set it up as a brand new workspace within the project.

​	当为 `npm init` 命令设置时，可以将其设置为尚不存在的工作区的文件夹，以在项目中创建该文件夹并将其设置为全新的工作区。

This value is not exported to the environment for child processes.

​	此值不会导出到子进程的环境中。

#### `workspaces`

- Default: null
- Type: null or Boolean

Set to true to run the command in the context of **all** configured workspaces.

​	将其设置为true以在**所有**配置的工作区上下文中运行命令。

Explicitly setting this to false will cause commands like `install` to ignore workspaces altogether. When not set explicitly:

​	显式设置为false将导致诸如 `install` 之类的命令完全忽略工作区。当未明确设置时：

- Commands that operate on the `node_modules` tree (install, update, etc.) will link workspaces into the `node_modules` folder. - Commands that do other things (test, exec, publish, etc.) will operate on the root project, *unless* one or more workspaces are specified in the `workspace` config.
- 操作 `node_modules` 树（install、update等）的命令将链接工作区到 `node_modules` 文件夹中。- 执行其他操作的命令（test、exec、publish等）将在根项目上操作，*除非*在 `workspace` 配置中指定了一个或多个工作区。

This value is not exported to the environment for child processes.

​	此值不会导出到子进程的环境中。

#### `workspaces-update`

- Default: true
- Type: Boolean

If set to true, the npm cli will run an update after operations that may possibly change the workspaces installed to the `node_modules` folder.

​	如果设置为true，则npm cli将在可能更改安装到 `node_modules` 文件夹的工作区之后运行更新操作。

#### `yes`

- Default: null
- Type: null or Boolean

Automatically answer "yes" to any prompts that npm might print on the command line.

​	自动回答npm在命令行上可能打印的任何提示的"yes"。

#### `also`

- Default: null
- Type: null, "dev", or "development"
- DEPRECATED: Please use --include=dev instead.
- 已弃用：请改用--include=dev。

When set to `dev` or `development`, this is an alias for `--include=dev`.

​	当设置为 `dev` 或 `development` 时，这是 `--include=dev` 的别名。

#### `cache-max`

- Default: Infinity
- Type: Number
- DEPRECATED: This option has been deprecated in favor of `--prefer-online`
- 已弃用：此选项已被弃用，改用 `--prefer-online` 。

```
--cache-max=0` is an alias for `--prefer-online
```

#### `cache-min`

- Default: 0
- Type: Number
- DEPRECATED: This option has been deprecated in favor of `--prefer-offline`.
- 已弃用：此选项已被弃用，改用 `--prefer-offline` 。

`--cache-min=9999 (or bigger)` is an alias for `--prefer-offline`.

`--cache-min=9999（或更大）` 是 `--prefer-offline` 的别名。

#### `cert`

- Default: null
- Type: null or String
- DEPRECATED: `key` and `cert` are no longer used for most registry operations. Use registry scoped `keyfile` and `certfile` instead. Example: //other-registry.tld/:keyfile=/path/to/key.pem //other-registry.tld/:certfile=/path/to/cert.crt
- 已弃用：大多数注册表操作不再使用 `key` 和 `cert` 。请改用注册表作用域的 `keyfile` 和 `certfile` 。示例：//other-registry.tld/:keyfile=/path/to/key.pem //other-registry.tld/:certfile=/path/to/cert.crt

A client certificate to pass when accessing the registry. Values should be in PEM format (Windows calls it "Base-64 encoded X.509 (.CER)") with newlines replaced by the string "\n". For example:

​	在访问注册表时传递的客户端证书。值应采用PEM格式（Windows称其为“Base-64编码的X.509（.CER）”），换行符替换为字符串“\n”。例如：

```ini
cert="-----BEGIN CERTIFICATE-----\nXXXX\nXXXX\n-----END CERTIFICATE-----"
```

It is *not* the path to a certificate file, though you can set a registry-scoped "certfile" path like "//other-registry.tld/:certfile=/path/to/cert.pem".

#### `dev`

- Default: false
- Type: Boolean
- DEPRECATED: Please use --include=dev instead.
- 已弃用：请改用--include=dev。

Alias for `--include=dev`.

​	`--include=dev` 的别名。

#### `global-style`

- Default: false
- Type: Boolean
- DEPRECATED: This option has been deprecated in favor of `--install-strategy=shallow`
- 已弃用：此选项已被弃用，改用 `--install-strategy=shallow` 。

Only install direct dependencies in the top level `node_modules`, but hoist on deeper dependencies. Sets `--install-strategy=shallow`.

​	仅在顶级 `node_modules` 中安装直接依赖项，但在更深的依赖项上提升。设置 `--install-strategy=shallow` 。

#### `init.author.email`

- Default: ""
- Type: String
- DEPRECATED: Use `--init-author-email` instead.
- 已弃用：请改用`--init-author-email`。

Alias for `--init-author-email`

​	`--init-author-email` 的别名。

#### `init.author.name`

- Default: ""
- Type: String
- DEPRECATED: Use `--init-author-name` instead.
- 已弃用：请改用`--init-author-name`。

Alias for `--init-author-name`

#### `init.author.url`

- Default: ""
- Type: "" or URL
- DEPRECATED: Use `--init-author-url` instead.
- 已弃用：请改用`--init-author-url`。

Alias for 

​	`--init-author-url` 的别名。

#### `init.license`

- Default: "ISC"
- Type: String
- DEPRECATED: Use `--init-license` instead.
- 已弃用：请改用`--init-license`。

Alias for `--init-license`

​	`--init-license` 的别名。

#### `init.module`

- Default: "~/.npm-init.js"
- Type: Path
- DEPRECATED: Use `--init-module` instead.
- 已弃用：请改用`--init-module`。

Alias for `--init-module`

​	`--init-module` 的别名。

#### `init.version`

- Default: "1.0.0"
- Type: SemVer string
- DEPRECATED: Use `--init-version` instead.
- 已弃用：请改用`--init-version`。

Alias for `--init-version`

​	`--init-version` 的别名。

#### `key`

- Default: null
- Type: null or String
- DEPRECATED: `key` and `cert` are no longer used for most registry operations. Use registry scoped `keyfile` and `certfile` instead. Example: //other-registry.tld/:keyfile=/path/to/key.pem //other-registry.tld/:certfile=/path/to/cert.crt
- 已弃用：大多数注册表操作不再使用 `key` 和 `cert` 。请改用注册表作用域的 `keyfile` 和 `certfile` 。示例：//other-registry.tld/:keyfile=/path/to/key.pem //other-registry.tld/:certfile=/path/to/cert.crt

A client key to pass when accessing the registry. Values should be in PEM format with newlines replaced by the string "\n". For example:

​	在访问注册表时传递的客户端密钥。值应采用PEM格式，换行符替换为字符串“\n”。例如：

```ini
key="-----BEGIN PRIVATE KEY-----\nXXXX\nXXXX\n-----END PRIVATE KEY-----"
```

It is *not* the path to a key file, though you can set a registry-scoped "keyfile" path like "//other-registry.tld/:keyfile=/path/to/key.pem".

​	它不是密钥文件的路径，但是您可以设置注册表范围的“keyfile”路径，例如“//other-registry.tld/:keyfile=/path/to/key.pem”。

#### `legacy-bundling`

- Default: false
- Type: Boolean
- DEPRECATED: This option has been deprecated in favor of `--install-strategy=nested`
- 已弃用：此选项已被弃用，改用 `--install-strategy=nested` 。

Instead of hoisting package installs in `node_modules`, install packages in the same manner that they are depended on. This may cause very deep directory structures and duplicate package installs as there is no de-duplicating. Sets `--install-strategy=nested`.

​	不是将包安装在 `node_modules` 中，而是以与其依赖项相同的方式安装包。这可能会导致非常深的目录结构和重复的包安装，因为没有去重。设置 `--install-strategy=nested` 。

#### `only`

- Default: null
- Type: null, "prod", or "production"
- DEPRECATED: Use `--omit=dev` to omit dev dependencies from the install.
- 已弃用：使用 `--omit=dev` 从安装中省略dev依赖关系。

When set to `prod` or `production`, this is an alias for `--omit=dev`.

​	当设置为 `prod` 或 `production` 时，这是 `--omit=dev` 的别名。

#### `optional`

- Default: null
- Type: null or Boolean
- DEPRECATED: Use `--omit=optional` to exclude optional dependencies, or `--include=optional` to include them.
- 已弃用：使用 `--omit=optional` 排除可选依赖项，或使用 `--include=optional` 包含它们。

Default value does install optional deps unless otherwise omitted.

​	默认情况下，确实安装可选的依赖项，除非另有省略。

Alias for `--include=optional` or `--omit=optional`

​	 `--include=optional` 或 `--omit=optional` 的别名

#### `production`

- Default: null
- Type: null or Boolean
- DEPRECATED: Use `--omit=dev` instead.
- 已弃用：请改用`--omit=dev`。

Alias for `--omit=dev`

​	`--omit=dev` 的别名

#### `shrinkwrap`

- Default: true
- Type: Boolean
- DEPRECATED: Use the `--package-lock` setting instead.
- 已弃用：请改用`--package-lock`设置。

Alias for `--package-lock`

​	`--package-lock` 的别名

### See also

- [npm config](https://docs.npmjs.com/cli/v10/commands/npm-config)
- [npmrc](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc)
- [npm scripts](https://docs.npmjs.com/cli/v10/using-npm/scripts)
- [npm folders](https://docs.npmjs.com/cli/v10/configuring-npm/folders)
- [npm](https://docs.npmjs.com/cli/v10/commands/npm)
