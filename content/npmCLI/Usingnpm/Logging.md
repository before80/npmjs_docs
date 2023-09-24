+++
title = "日志记录"
date = 2023-09-22T21:23:47+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/cli/v10/using-npm/logging](https://docs.npmjs.com/cli/v10/using-npm/logging)

# Logging - 日志记录

Why, What & How We Log

为什么、什么以及如何记录日志

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

The `npm` CLI has various mechanisms for showing different levels of information back to end-users for certain commands, configurations & environments.

 	`npm`  CLI具有各种机制，用于向最终用户显示不同级别的信息，针对特定命令、配置和环境。

### 设置日志文件位置 Setting Log File Location

All logs are written to a debug log, with the path to that file printed if the execution of a command fails.

​	所有日志都写入调试日志中，如果命令执行失败，将打印该文件的路径。

The default location of the logs directory is a directory named `_logs` inside the npm cache. This can be changed with the `logs-dir` config option.

​	日志目录的默认位置是npm缓存中名为 `_logs` 的目录。可以使用 `logs-dir` 配置选项更改此位置。

For example, if you wanted to write all your logs to the current working directory, you could run: `npm install --logs-dir=.`. This is especially helpful in debugging a specific `npm` issue as you can run a command multiple times with different config values and then diff all the log files.

​	例如，如果您希望将所有日志写入当前工作目录，可以运行： `npm install --logs-dir=.` 。这在调试特定的 `npm` 问题时特别有帮助，因为您可以使用不同的配置值多次运行命令，然后比较所有日志文件。

Log files will be removed from the `logs-dir` when the number of log files exceeds `logs-max`, with the oldest logs being deleted first.

​	当日志文件的数量超过 `logs-max` 时，将从 `logs-dir` 中删除最旧的日志文件。

To turn off logs completely set `--logs-max=0`.

​	要完全关闭日志，请设置 `--logs-max=0` 。

### 设置日志级别 Setting Log Levels

#### `loglevel`

`loglevel` is a global argument/config that can be set to determine the type of information to be displayed.

 	`loglevel` 是一个全局参数/配置，可以设置以确定要显示的信息类型。

The default value of `loglevel` is `"notice"` but there are several levels/types of logs available, including:

 	`loglevel` 的默认值为 `"notice"` ，但有几个级别/类型的日志可用，包括：

- `"silent"`
- `"error"`
- `"warn"`
- `"notice"`
- `"http"`
- `"info"`
- `"verbose"`
- `"silly"`

All logs pertaining to a level proceeding the current setting will be shown.

​	显示与当前设置之前的级别相关的所有日志。

##### 别名 Aliases

The log levels listed above have various corresponding aliases, including:

​	上述日志级别有各种对应的别名，包括：

- `-d`: `--loglevel info`
- `--dd`: `--loglevel verbose`
- `--verbose`: `--loglevel verbose`
- `--ddd`: `--loglevel silly`
- `-q`: `--loglevel warn`
- `--quiet`: `--loglevel warn`
- `-s`: `--loglevel silent`
- `--silent`: `--loglevel silent`

#### `foreground-scripts`

The `npm` CLI began hiding the output of lifecycle scripts for `npm install` as of `v7`. Notably, this means you will not see logs/output from packages that may be using "install scripts" to display information back to you or from your own project's scripts defined in `package.json`. If you'd like to change this behavior & log this output you can set `foreground-scripts` to `true`.

​	自 `v7` 以来， `npm`  CLI开始隐藏 `npm install` 的生命周期脚本的输出。特别要注意的是，这意味着您将无法看到使用“安装脚本”向您显示信息的软件包或来自 `package.json` 中定义的项目脚本的日志/输出。如果您想更改此行为并记录此输出，可以将 `foreground-scripts` 设置为 `true` 。

### 时间信息 Timing Information

The [`--timing` config](https://docs.npmjs.com/cli/v10/using-npm/config#timing) can be set which does a few things:

​	可以设置[ `--timing` 配置](https://docs.npmjs.com/cli/v10/using-npm/config#timing)，它会执行以下几个操作：

1. Always shows the full path to the debug log regardless of command exit status
2. 无论命令的退出状态如何，始终显示调试日志的完整路径
3. Write timing information to a process specific timing file in the cache or `logs-dir`
4. 将定时信息写入缓存或 `logs-dir` 中的进程特定定时文件
5. Output timing information to the terminal
6. 将定时信息输出到终端

This file contains a `timers` object where the keys are an identifier for the portion of the process being timed and the value is the number of milliseconds it took to complete.

​	该文件包含一个 `timers` 对象，其中键是正在计时的过程的标识符，值是完成所花费的毫秒数。

Sometimes it is helpful to get timing information without outputting anything to the terminal. For example, the performance might be affected by writing to the terminal. In this case you can use `--timing --silent` which will still write the timing file, but not output anything to the terminal while running.

​	有时，获取定时信息而不将任何内容输出到终端可能很有帮助。例如，性能可能会受到写入终端的影响。在这种情况下，您可以使用 `--timing --silent` ，它仍然会写入定时文件，但在运行时不会向终端输出任何内容。

### 注册表响应头 Registry Response Headers

#### `npm-notice`

The `npm` CLI reads from & logs any `npm-notice` headers that are returned from the configured registry. This mechanism can be used by third-party registries to provide useful information when network-dependent requests occur.

 	`npm`  CLI会从配置的注册表中读取并记录任何返回的 `npm-notice` 头。第三方注册表可以使用此机制在发生网络相关请求时提供有用的信息。

This header is not cached, and will not be logged if the request is served from the cache.

​	此标头不会被缓存，并且如果请求是从缓存中提供的，则不会记录。

### 日志和敏感信息 Logs and Sensitive Information

The `npm` CLI makes a best effort to redact the following from terminal output and log files:

​	 `npm`  CLI会尽力从终端输出和日志文件中删除以下内容：

- Passwords inside basic auth URLs
- 基本身份验证URL中的密码
- npm tokens
- npm令牌

However, this behavior should not be relied on to keep all possible sensitive information redacted. If you are concerned about secrets in your log file or terminal output, you can use `--loglevel=silent` and `--logs-max=0` to ensure no logs are written to your terminal or filesystem.

​	但是，不应依赖此行为来保持所有可能的敏感信息被删除。如果您担心日志文件或终端输出中的机密信息，可以使用 `--loglevel=silent` 和 `--logs-max=0` 确保不会将任何日志写入终端或文件系统。

### See also

- [config](https://docs.npmjs.com/cli/v10/using-npm/config)
