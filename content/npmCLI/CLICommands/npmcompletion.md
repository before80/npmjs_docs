+++
title = "npm completion"
date = 2023-09-22T21:11:09+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false
+++

> 原文: [https://docs.npmjs.com/cli/v10/commands/npm-completion](https://docs.npmjs.com/cli/v10/commands/npm-completion)

# npm-completion

Tab Completion for npm

Select CLI Version:Version 10.0.0 (Latest Release)

### Synopsis



```bash
npm completion
```

Note: This command is unaware of workspaces.

### Description

Enables tab-completion in all npm commands.

The synopsis above loads the completions into your current shell. Adding it to your ~/.bashrc or ~/.zshrc will make the completions available everywhere:



```bash
npm completion >> ~/.bashrc
npm completion >> ~/.zshrc
```

You may of course also pipe the output of `npm completion` to a file such as `/usr/local/etc/bash_completion.d/npm` or `/etc/bash_completion.d/npm` if you have a system that will read that file for you.

When `COMP_CWORD`, `COMP_LINE`, and `COMP_POINT` are defined in the environment, `npm completion` acts in "plumbing mode", and outputs completions based on the arguments.

### See Also

- [npm developers](https://docs.npmjs.com/cli/v10/using-npm/developers)
- [npm](https://docs.npmjs.com/cli/v10/commands/npm)
