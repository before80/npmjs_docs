+++
title = "依赖项选择器"
date = 2023-09-22T21:24:42+08:00
weight = 80
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/cli/v10/using-npm/dependency-selectors](https://docs.npmjs.com/cli/v10/using-npm/dependency-selectors)

# Dependency Selector Syntax & Querying - 依赖项选择器语法和查询

Dependency Selector Syntax & Querying

​	依赖项选择器语法和查询

Select CLI Version:Version 10.0.0 (Latest Release)

### 描述 Description

The [`npm query`](https://docs.npmjs.com/cli/v10/commands/npm-query) command exposes a new dependency selector syntax (informed by & respecting many aspects of the [CSS Selectors 4 Spec](https://dev.w3.org/csswg/selectors4/#relational)) which:

​	[ `npm query` ](https://docs.npmjs.com/cli/v10/commands/npm-query)命令公开了一种新的依赖项选择器语法（受到并尊重[CSS选择器4规范](https://dev.w3.org/csswg/selectors4/#relational)的许多方面），其中：

- Standardizes the shape of, & querying of, dependency graphs with a robust object model, metadata & selector syntax
- 标准化了依赖图的形状和查询，具有强大的对象模型、元数据和选择器语法
- Leverages existing, known language syntax & operators from CSS to make disparate package information broadly accessible
- 利用了来自CSS的现有、已知的语言语法和运算符，使不同的包信息广泛可访问
- Unlocks the ability to answer complex, multi-faceted questions about dependencies, their relationships & associative metadata
- 解锁了回答关于依赖关系、它们的关系和关联元数据的复杂、多方面问题的能力
- Consolidates redundant logic of similar query commands in `npm` (ex. `npm fund`, `npm ls`, `npm outdated`, `npm audit` ...)
- 整合了 `npm` 中类似查询命令的重复逻辑（例如 `npm fund` 、 `npm ls` 、 `npm outdated` 、 `npm audit` 等）

### 依赖项选择器语法 `v1.0.0`  Dependency Selector Syntax `v1.0.0`

#### 概述： Overview:

- there is no "type" or "tag" selectors (ex. `div, h1, a`) as a dependency/target is the only type of `Node` that can be queried
- 没有“类型”或“标签”选择器（例如 `div` 、 `h1` 、 `a` ），因为依赖项/目标是唯一可以查询的 `Node` 类型
- the term "dependencies" is in reference to any `Node` found in a `tree` returned by `Arborist`
- “dependencies”一词是指由 `Arborist` 返回的 `tree` 中找到的任何 `Node` 

#### 组合器Combinators

- `>` direct descendant/child
- `>`  直接子代
- `` any descendant/child
- ``  任意后代
- `~` sibling
- `~`  兄弟

#### 选择器 Selectors

- `*` universal selector
- `*`  通用选择器
- `#<name>` dependency selector (equivalent to `[name="..."]`)
- `#<name>`  依赖项选择器（等效于 `[name="..."]` ）
- `#<name>@<version>` (equivalent to `[name=<name>]:semver(<version>)`)
- `#<name>@<version>`  （等效于 `[name=<name>]:semver(<version>)` ）
- `,` selector list delimiter
- `,`  选择器列表分隔符
- `.` dependency type selector
- `.`  依赖项类型选择器
- `:` pseudo selector
- `:`  伪选择器

#### 依赖项类型选择器 Dependency Type Selectors

- `.prod` dependency found in the `dependencies` section of `package.json`, or is a child of said dependency
- `.prod`  在 `package.json` 的 `dependencies` 部分中找到的依赖项，或是该依赖项的子代
- `.dev` dependency found in the `devDependencies` section of `package.json`, or is a child of said dependency
- `.dev`  在 `package.json` 的 `devDependencies` 部分中找到的依赖项，或是该依赖项的子代
- `.optional` dependency found in the `optionalDependencies` section of `package.json`, or has `"optional": true` set in its entry in the `peerDependenciesMeta` section of `package.json`, or a child of said dependency
- `.optional`  在 `package.json` 的 `optionalDependencies` 部分中找到的依赖项，或在 `package.json` 的 `peerDependenciesMeta` 部分的条目中设置了 `"optional": true` ，或是该依赖项的子代
- `.peer` dependency found in the `peerDependencies` section of `package.json`
- `.peer`  在 `package.json` 的 `peerDependencies` 部分中找到的依赖项
- `.workspace` dependency found in the [`workspaces`](https://docs.npmjs.com/cli/v8/using-npm/workspaces) section of `package.json`
- `.workspace`  在 `package.json` 的[ `workspaces` ](https://docs.npmjs.com/cli/v8/using-npm/workspaces)部分中找到的依赖项
- `.bundled` dependency found in the `bundleDependencies` section of `package.json`, or is a child of said dependency
- `.bundled`  在 `package.json` 的 `bundleDependencies` 部分中找到的依赖项，或是该依赖项的子代

#### 伪选择器 Pseudo Selectors

- [`:not()`](https://developer.mozilla.org/en-US/docs/Web/CSS/:not)
- [`:has()`](https://developer.mozilla.org/en-US/docs/Web/CSS/:has)
- [`:is()`](https://developer.mozilla.org/en-US/docs/Web/CSS/:is)
- [`:root`](https://developer.mozilla.org/en-US/docs/Web/CSS/:root) matches the root node/dependency
- [ `:root` ](https://developer.mozilla.org/en-US/docs/Web/CSS/:root) 匹配根节点/依赖项
- [`:scope`](https://developer.mozilla.org/en-US/docs/Web/CSS/:scope) matches node/dependency it was queried against
- [ `:scope` ](https://developer.mozilla.org/en-US/docs/Web/CSS/:scope) 匹配查询所针对的节点/依赖项
- [`:empty`](https://developer.mozilla.org/en-US/docs/Web/CSS/:empty) when a dependency has no dependencies
- [ `:empty` ](https://developer.mozilla.org/en-US/docs/Web/CSS/:empty) 当一个依赖项没有依赖项时
- [`:private`](https://docs.npmjs.com/cli/v8/configuring-npm/package-json#private) when a dependency is private
- [ `:private` ](https://docs.npmjs.com/cli/v8/configuring-npm/package-json#private) 当一个依赖项是私有的时候
- `:link` when a dependency is linked (for instance, workspaces or packages manually [`linked`](https://docs.npmjs.com/cli/v8/commands/npm-link)
- `:link`  当一个依赖项被链接时（例如，工作区或手动[ `linked` ](https://docs.npmjs.com/cli/v8/commands/npm-link)的包）
- `:deduped` when a dependency has been deduped (note that this does *not* always mean the dependency has been hoisted to the root of node_modules)
- `:deduped`  当一个依赖项被去重时（请注意，这并不总是意味着依赖项已经被提升到node_modules的根目录）
- `:overridden` when a dependency has been overridden
- `:overridden`  当一个依赖项被覆盖时
- `:extraneous` when a dependency exists but is not defined as a dependency of any node
- `:extraneous`  当一个依赖项存在但没有被定义为任何节点的依赖项时
- `:invalid` when a dependency version is out of its ancestors specified range
- `:invalid`  当一个依赖项的版本超出了其祖先指定的范围时
- `:missing` when a dependency is not found on disk
- `:missing`  当一个依赖项在磁盘上找不到时
- `:semver(<spec>, [selector], [function])` match a valid [`node-semver`](https://github.com/npm/node-semver) version or range to a selector
- `:semver(<spec>, [selector], [function])`  将有效的[ `node-semver` ](https://github.com/npm/node-semver)版本或范围与选择器匹配
- `:path(<path>)` [glob](https://www.npmjs.com/package/glob) matching based on dependencies path relative to the project
- `:path(<path>)`  基于依赖项相对于项目的路径的[glob](https://www.npmjs.com/package/glob)匹配
- `:type(<type>)` [based on currently recognized types](https://github.com/npm/npm-package-arg#result-object)
- `:type(<type>)`  [基于当前已识别的类型](https://github.com/npm/npm-package-arg#result-object)
- `:outdated(<type>)` when a dependency is outdated
- `:outdated(<type>)`  当一个依赖项已过时时

##### `:semver(<spec>, [selector], [function])`

The `:semver()` pseudo selector allows comparing fields from each node's `package.json` using [semver](https://github.com/npm/node-semver#readme) methods. It accepts up to 3 parameters, all but the first of which are optional.

 	`:semver()` 伪选择器允许使用[semver](https://github.com/npm/node-semver#readme)方法比较每个节点的 `package.json` 中的字段。它最多接受3个参数，除了第一个参数外，其他参数都是可选的。

- `spec` a semver version or range
- `spec`  一个semver版本或范围
- `selector` an attribute selector for each node (default `[version]`)
- `selector`  每个节点的属性选择器（默认为 `[version]` ）
- `function` a semver method to apply, one of: `satisfies`, `intersects`, `subset`, `gt`, `gte`, `gtr`, `lt`, `lte`, `ltr`, `eq`, `neq` or the special function `infer` (default `infer`)
- `function`  应用的semver方法之一： `satisfies` 、 `intersects` 、 `subset` 、 `gt` 、 `gte` 、 `gtr` 、 `lt` 、 `lte` 、 `ltr` 、 `eq` 、 `neq` 或特殊函数 `infer` （默认为 `infer` ）

When the special `infer` function is used the `spec` and the actual value from the node are compared. If both are versions, according to `semver.valid()`, `eq` is used. If both values are ranges, according to `!semver.valid()`, `intersects` is used. If the values are mixed types `satisfies` is used.

​	当使用特殊的 `infer` 函数时，将比较 `spec` 和节点的实际值。如果两个都是版本（根据 `semver.valid()` ），则使用 `eq` 。如果两个值都是范围（根据 `!semver.valid()` ），则使用 `intersects` 。如果值是混合类型，则使用 `satisfies` 。

Some examples:

​	一些例子：

- `:semver(^1.0.0)` returns every node that has a `version` satisfied by the provided range `^1.0.0`
- `:semver(^1.0.0)`  返回每个节点，其 `version` 满足提供的范围 `^1.0.0` 
- `:semver(16.0.0, :attr(engines, [node]))` returns every node which has an `engines.node` property satisfying the version `16.0.0`
- `:semver(16.0.0, :attr(engines, [node]))`  返回每个节点，它具有满足版本 `16.0.0` 的 `engines.node` 属性
- `:semver(1.0.0, [version], lt)` every node with a `version` less than `1.0.0`
- `:semver(1.0.0, [version], lt)`  每个 `version` 小于 `1.0.0` 的节点

##### `:outdated(<type>)`

The `:outdated` pseudo selector retrieves data from the registry and returns information about which of your dependencies are outdated. The type parameter may be one of the following:

​	 `:outdated` 伪选择器从注册表中检索数据，并返回有关哪些依赖项已过时的信息。type参数可以是以下之一：

- `any` (default) a version exists that is greater than the current one
- `any` （默认值）存在一个版本大于当前版本的版本
- `in-range` a version exists that is greater than the current one, and satisfies at least one if its dependents
- `in-range`  存在一个版本大于当前版本的版本，并且满足其至少一个依赖项
- `out-of-range` a version exists that is greater than the current one, does not satisfy at least one of its dependents
- `out-of-range`  存在一个版本大于当前版本的版本，不满足至少一个依赖项
- `major` a version exists that is a semver major greater than the current one
- `major`  存在一个semver主版本大于当前版本的版本
- `minor` a version exists that is a semver minor greater than the current one
- `minor`  存在一个semver次要版本大于当前版本的版本
- `patch` a version exists that is a semver patch greater than the current one
- `patch`  存在一个semver修订版本大于当前版本的版本

In addition to the filtering performed by the pseudo selector, some extra data is added to the resulting objects. The following data can be found under the `queryContext` property of each node.

​	除了伪选择器执行的过滤之外，还会在每个节点的 `queryContext` 属性下添加一些额外的数据。以下数据可以在每个节点的 `queryContext` 属性下找到：

- `versions` an array of every available version of the given node
- `versions`  给定节点的所有可用版本的数组
- `outdated.inRange` an array of objects, each with a `from` and `versions`, where `from` is the on-disk location of the node that depends on the current node and `versions` is an array of all available versions that satisfies that dependency. This is only populated if `:outdated(in-range)` is used.
- `outdated.inRange`  一个对象数组，每个对象都有 `from` 和 `versions` 属性，其中 `from` 是依赖于当前节点的节点的磁盘位置， `versions` 是满足该依赖项的所有可用版本的数组。只有在使用 `:outdated(in-range)` 时才会填充此属性。
- `outdated.outOfRange` an array of objects, identical in shape to `inRange`, but where the `versions` array is every available version that does not satisfy the dependency. This is only populated if `:outdated(out-of-range)` is used.
- `outdated.outOfRange`  一个与 `inRange` 形状相同的对象数组，但其中 `versions` 数组是不满足依赖关系的每个可用版本。只有在使用 `:outdated(out-of-range)` 时才会填充此属性。

Some examples:

一些例子：

- `:root > :outdated(major)` returns every direct dependency that has a new semver major release
- `:root > :outdated(major)`  返回每个直接依赖项，其具有新的semver主版本发布
- `.prod:outdated(in-range)` returns production dependencies that have a new release that satisfies at least one of its edges in
- `.prod:outdated(in-range)`  返回具有新发布且满足其至少一个边缘的生产依赖项

#### 属性选择器 Attribute Selectors

The attribute selector evaluates the key/value pairs in `package.json` if they are `String`s.

​	属性选择器在 `package.json` 中的键值对（如果它们是字符串）上进行评估。

- `[]` attribute selector (ie. existence of attribute)
- `[]`  属性选择器（即属性的存在）
- `[attribute=value]` attribute value is equivalant...
- `[attribute=value]`  属性值等于...
- `[attribute~=value]` attribute value contains word...
- `[attribute~=value]`  属性值包含单词...
- `[attribute*=value]` attribute value contains string...
- `[attribute*=value]`  属性值包含字符串...
- `[attribute|=value]` attribute value is equal to or starts with...
- `[attribute|=value]`  属性值等于或以...开头
- `[attribute^=value]` attribute value starts with...
- `[attribute^=value]`  属性值以...开头
- `[attribute$=value]` attribute value ends with...
- `[attribute$=value]`  属性值以...结尾

#### `Array`  和  `Object`  属性选择器 `Array` & `Object` Attribute Selectors

The generic `:attr()` pseudo selector standardizes a pattern which can be used for attribute selection of `Object`s, `Array`s or `Arrays` of `Object`s accessible via `Arborist`'s `Node.package` metadata. This allows for iterative attribute selection beyond top-level `String` evaluation. The last argument passed to `:attr()` must be an `attribute` selector or a nested `:attr()`. See examples below:

​	通用的  `:attr()`  伪选择器标准化了一种模式，可用于对  `Object` 、 `Array`  或  `Object`  数组进行属性选择，这些属性可以通过  `Arborist`  的  `Node.package`  元数据访问。这允许进行迭代属性选择，超出顶级字符串评估。传递给  `:attr()`  的最后一个参数必须是属性选择器或嵌套的  `:attr()` 。请参阅以下示例：

#### `Objects`



```css
/* return dependencies that have a `scripts.test` containing `"tap"` */
/* 返回具有包含“tap”的`scripts.test`的依赖项 */
*:attr(scripts, [test~=tap])
```

#### 嵌套的  `Objects`  Nested `Objects`

Nested objects are expressed as sequential arguments to `:attr()`.

​	嵌套的对象表示为  `:attr()`  的连续参数。

```css
/* return dependencies that have a testling config for opera browsers */
/* 返回具有面向 Opera 浏览器的 testling 配置的依赖项 */
*:attr(testling, browsers, [~=opera])
```

#### `Arrays`

`Array`s specifically uses a special/reserved `.` character in place of a typical attribute name. `Arrays` also support exact `value` matching when a `String` is passed to the selector.

​	 `Array`  使用特殊/保留的  `.`  字符代替典型的属性名。当将字符串传递给选择器时， `Array`  还支持精确的  `value`  匹配。

##### Example of an `Array` Attribute Selection:

​	`Array`  属性选择的示例：

```css
/* removes the distinction between properties & arrays */
/* 消除了属性和数组之间的区别 */
/* ie. we'd have to check the property & iterate to match selection */
/* 例如，我们必须检查属性并迭代以匹配选择 */
*:attr([keywords^=react])
*:attr(contributors, :attr([name~=Jordan]))
```

##### Example of an `Array` matching directly to a value:

​	直接匹配到值的  `Array`  示例：

```css
/* return dependencies that have the exact keyword "react" */
/* 返回具有精确关键字“react”的依赖项 */
/* this is equivalent to `*:keywords([value="react"])` */
/* 这相当于 `*:keywords([value="react"])` */
*:attr([keywords=react])
```

##### Example of an `Array` of `Object`s:

`Object`  数组的示例：

```css
/* returns */
*:attr(contributors, [email=ruyadorno@github.com])
```

### 组 Groups

Dependency groups are defined by the package relationships to their ancestors (ie. the dependency types that are defined in `package.json`). This approach is user-centric as the ecosystem has been taught to think about dependencies in these groups first-and-foremost. Dependencies are allowed to be included in multiple groups (ex. a `prod` dependency may also be a `dev` dependency (in that it's also required by another `dev` dependency) & may also be `bundled` - a selector for that type of dependency would look like: `*.prod.dev.bundled`).

​	依赖组是由包与其祖先之间的关系（即在  `package.json`  中定义的依赖类型）定义的。这种方法以用户为中心，因为生态系统已经教导我们首先考虑这些组中的依赖关系。依赖项可以包含在多个组中（例如， `prod`  依赖项也可以是  `dev`  依赖项（因为它还被另一个  `dev`  依赖项所需）并且也可以是  `bundled`  的 - 这种类型的依赖项选择器看起来像： `*.prod.dev.bundled` ）。

- `.prod`
- `.dev`
- `.optional`
- `.peer`
- `.bundled`
- `.workspace`

Please note that currently `workspace` deps are always `prod` dependencies. Additionally the `.root` dependency is also considered a `prod` dependency.

​	请注意，当前  `workspace`  依赖项始终是  `prod`  依赖项。此外， `.root`  依赖项也被视为  `prod`  依赖项。

### 编程使用 Programmatic Usage

- `Arborist`'s `Node` Class has a  `.querySelectorAll()`method
- `Arborist`  的  `Node`  类具有  `.querySelectorAll()`  方法
  - this method will return a filtered, flattened dependency Arborist `Node` list based on a valid query selector
  - 此方法将基于有效的查询选择器返回经过过滤和展平的依赖 Arborist  `Node`  列表

```js
const Arborist = require('@npmcli/arborist')
const arb = new Arborist({})
```



```js
// root-level
arb.loadActual().then(async (tree) => {
  // query all production dependencies
  const results = await tree.querySelectorAll('.prod')
  console.log(results)
})
```



```js
// iterative
arb.loadActual().then(async (tree) => {
  // query for the deduped version of react
  const results = await tree.querySelectorAll('#react:not(:deduped)')
  // query the deduped react for git deps
  const deps = await results[0].querySelectorAll(':type(git)')
  console.log(deps)
})
```

## See Also

- [npm query](https://docs.npmjs.com/cli/v10/commands/npm-query)
- [@npmcli/arborist](https://npm.im/@npmcli/arborist)
