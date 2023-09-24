+++
title = "npm help"
date = 2023-09-22T21:13:32+08:00
weight = 210
type = "docs"
description = ""
isCJKLanguage = true
draft = false
+++

> 原文: [https://docs.npmjs.com/cli/v10/commands/npm-help](https://docs.npmjs.com/cli/v10/commands/npm-help)

# npm-help

Get help on npm

Select CLI Version:Version 10.0.0 (Latest Release)

### Synopsis



```bash
npm help <term> [<terms..>]

alias: hlep
```

Note: This command is unaware of workspaces.

### Description

If supplied a topic, then show the appropriate documentation page.

If the topic does not exist, or if multiple terms are provided, then npm will run the `help-search` command to find a match. Note that, if `help-search` finds a single subject, then it will run `help` on that topic, so unique matches are equivalent to specifying a topic name.

### Configuration

#### `viewer`

- Default: "man" on Posix, "browser" on Windows
- Type: String

The program to use to view help content.

Set to `"browser"` to view html help content in the default web browser.

### See Also

- [npm](https://docs.npmjs.com/cli/v10/commands/npm)
- [npm folders](https://docs.npmjs.com/cli/v10/configuring-npm/folders)
- [npm config](https://docs.npmjs.com/cli/v10/commands/npm-config)
- [npmrc](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc)
- [package.json](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)
- [npm help-search](https://docs.npmjs.com/cli/v10/commands/npm-help-search)
