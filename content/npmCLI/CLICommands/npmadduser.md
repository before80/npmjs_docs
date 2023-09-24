+++
title = "npm adduser"
date = 2023-09-22T21:10:13+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false
+++

> 原文: [https://docs.npmjs.com/cli/v10/commands/npm-adduser](https://docs.npmjs.com/cli/v10/commands/npm-adduser)

# npm-adduser

Add a registry user account

Select CLI Version:Version 10.0.0 (Latest Release)

### Synopsis



```bash
npm adduser

alias: add-user
```

Note: This command is unaware of workspaces.

### Description

Create a new user in the specified registry, and save the credentials to the `.npmrc` file. If no registry is specified, the default registry will be used (see [`registry`](https://docs.npmjs.com/cli/v10/using-npm/registry)).

When using `legacy` for your `auth-type`, the username, password, and email are read in from prompts.

### Configuration

#### `registry`

- Default: "https://registry.npmjs.org/"
- Type: URL

The base URL of the npm registry.

#### `scope`

- Default: the scope of the current project, if any, or ""
- Type: String

Associate an operation with a scope for a scoped registry.

Useful when logging in to or out of a private registry:



```
# log in, linking the scope to the custom registry
npm login --scope=@mycorp --registry=https://registry.mycorp.com

# log out, removing the link and the auth token
npm logout --scope=@mycorp
```

This will cause `@mycorp` to be mapped to the registry for future installation of packages specified according to the pattern `@mycorp/package`.

This will also cause `npm init` to create a scoped package.



```
# accept all defaults, and create a package named "@foo/whatever",
# instead of just named "whatever"
npm init --scope=@foo --yes
```

#### `auth-type`

- Default: "web"
- Type: "legacy" or "web"

What authentication strategy to use with `login`. Note that if an `otp` config is given, this value will always be set to `legacy`.

### See Also

- [npm registry](https://docs.npmjs.com/cli/v10/using-npm/registry)
- [npm config](https://docs.npmjs.com/cli/v10/commands/npm-config)
- [npmrc](https://docs.npmjs.com/cli/v10/configuring-npm/npmrc)
- [npm owner](https://docs.npmjs.com/cli/v10/commands/npm-owner)
- [npm whoami](https://docs.npmjs.com/cli/v10/commands/npm-whoami)
- [npm token](https://docs.npmjs.com/cli/v10/commands/npm-token)
- [npm profile](https://docs.npmjs.com/cli/v10/commands/npm-profile)
