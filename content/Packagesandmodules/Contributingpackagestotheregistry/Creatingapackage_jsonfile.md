+++
title = "创建一个 package.json 文件"
date = 2023-09-22T20:55:14+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/creating-a-package-json-file](https://docs.npmjs.com/creating-a-package-json-file)

# Creating a package.json file - 创建一个 package.json 文件

You can add a `package.json` file to your package to make it easy for others to manage and install. Packages published to the registry must contain a `package.json` file.

​	您可以为您的包添加一个  `package.json`  文件，以便其他人可以轻松地管理和安装它。发布到注册表的包必须包含一个  `package.json`  文件。

A `package.json` file:

一个  `package.json`  文件：

- lists the packages your project depends on
- 列出了您的项目依赖的包
- specifies versions of a package that your project can use using [semantic versioning rules](about-semantic-versioning)
- 使用[语义化版本规范](about-semantic-versioning)指定您的项目可以使用的包的版本
- makes your build reproducible, and therefore easier to share with other developers
- 使您的构建可重现，因此更容易与其他开发人员共享

**Note:** To make your package easier to find on the npm website, we recommend including a custom `description` in your `package.json` file.

**注意：**为了让您的包在 npm 网站上更容易找到，我们建议在您的  `package.json`  文件中包含自定义的  `description` 。

## `package.json`  字段 `package.json` fields

### 必需的  `name`  和  `version`  字段 Required `name` and `version` fields

A `package.json` file must contain `"name"` and `"version"` fields.

​	一个  `package.json`  文件必须包含  `"name"`  和  `"version"`  字段。

The `"name"` field contains your package's name, and must be lowercase and one word, and may contain hyphens and underscores.

 	`"name"`  字段包含您的包的名称，必须是小写和单词，并且可以包含连字符和下划线。

The `"version"` field must be in the form `x.x.x` and follow the [semantic versioning guidelines](about-semantic-versioning).

 	`"version"`  字段必须采用  `x.x.x`  的形式，并遵循[语义化版本规范](about-semantic-versioning)。

### Author 字段 Author field

If you want to include package author information in `"author"` field, use the following format (email and website are both optional):

​	如果您想在  `"author"`  字段中包含包的作者信息，请使用以下格式（电子邮件和网站都是可选的）：

```
Your Name <email@example.com> (http://example.com)
```

### 示例 Example



```
{
  "name": "my-awesome-package",
  "version": "1.0.0",
  "author": "Your Name <email@example.com>"
}
```

## 创建新的  `package.json`  文件 Creating a new `package.json` file

You can create a `package.json` file by running a CLI questionnaire or creating a default `package.json` file.

​	您可以通过运行 CLI 问卷调查或创建一个默认的  `package.json`  文件来创建一个  `package.json`  文件。

### 运行 CLI 问卷调查 Running a CLI questionnaire

To create a `package.json` file with values that you supply, use the `npm init` command.

​	要创建一个包含您提供的值的  `package.json`  文件，请使用  `npm init`  命令。

1. On the command line, navigate to the root directory of your package.

2. 在命令行中，导航到您的包的根目录。

   ```
   cd /path/to/package
   ```

3. Run the following command:

4. 运行以下命令：

   ```
   npm init
   ```

5. Answer the questions in the command line questionnaire.

6. 在命令行问卷调查中回答问题。

#### 自定义  `package.json`  问卷调查 Customizing the `package.json` questionnaire

If you expect to create many `package.json` files, you can customize the questions asked and fields created during the `init` process so all the `package.json` files contain a standard set of information.

​	如果您预计要创建许多  `package.json`  文件，您可以自定义  `init`  过程中提出的问题和创建的字段，以便所有的  `package.json`  文件都包含一组标准的信息。

1. In your home directory, create a file called `.npm-init.js`.

2. 在您的主目录中，创建一个名为  `.npm-init.js`  的文件。

3. To add custom questions, using a text editor, add questions with the `prompt` function:

4. 要添加自定义问题，请使用文本编辑器使用  `prompt`  函数添加问题：

   ```
   module.exports = prompt("what's your favorite flavor of ice cream, buddy?", "I LIKE THEM ALL");
   ```

5. To add custom fields, using a text editor, add desired fields to the `.npm-init.js` file:

6. 要添加自定义字段，请使用文本编辑器将所需字段添加到  `.npm-init.js`  文件中：

   ```
   module.exports = {
     customField: 'Example custom field',
     otherCustomField: 'This example field is really cool'
   }
   ```

To learn more about creating advanced `npm init` customizations, see the [init-package-json GitHub repository](https://github.com/npm/init-package-json).

​	要了解有关创建高级  `npm init`  自定义的更多信息，请参阅 [init-package-json GitHub 仓库](https://github.com/npm/init-package-json)。

### 创建默认的  `package.json`  文件 Creating a default `package.json` file

To create a default `package.json` using information extracted from the current directory, use the `npm init` command with the `--yes` or `-y` flag. For a list of default values, see "[Default values extracted from the current directory](#default-values-extracted-from-the-current-directory)".

​	要使用从当前目录提取的信息创建默认的  `package.json` ，请使用  `npm init`  命令和  `--yes`  或  `-y`  标志。有关默认值的列表，请参见"[从当前目录提取的默认值](#从当前目录提取的默认值)"。

1. On the command line, navigate to the root directory of your package.

2. 在命令行中，导航到您的包的根目录。

   ```
   cd /path/to/package
   ```

3. Run the following command:

4. 运行以下命令：

   ```
   npm init --yes
   ```

#### 示例 Example

```
> npm init --yes
Wrote to /home/monatheoctocat/my_package/package.json:

{
  "name": "my_package",
  "description": "",
  "version": "1.0.0",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/monatheoctocat/my_package.git"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/monatheoctocat/my_package/issues"
  },
  "homepage": "https://github.com/monatheoctocat/my_package"
}
```

#### 从当前目录提取的默认值 Default values extracted from the current directory

- `name`: the current directory name
- `name` ：当前目录的名称
- `version`: always `1.0.0`
- `version` ：始终为  `1.0.0` 
- `description`: info from the README, or an empty string `""`
- `description` ：来自 README 的信息，或者为空字符串  `""` 
- `scripts`: by default creates an empty `test` script
- `scripts` ：默认创建一个空的  `test`  脚本
- `keywords`: empty
- `keywords` ：空
- `author`: empty
- `author` ：空
- `license`: [`ISC`](https://opensource.org/licenses/ISC)
- `bugs`: information from the current directory, if present
- `bugs` ：如果存在，来自当前目录的信息
- `homepage`: information from the current directory, if present
- `homepage` ：如果存在，来自当前目录的信息

### 为 init 命令设置配置选项 Setting config options for the init command

You can set default config options for the init command. For example, to set the default author email, author name, and license, on the command line, run the following commands:

​	您可以为 init 命令设置默认的配置选项。例如，要设置默认的作者电子邮件、作者名称和许可证，请在命令行上运行以下命令：

```
> npm set init-author-email "example-user@example.com"
> npm set init-author-name "example_user"
> npm set init-license "MIT"
```
