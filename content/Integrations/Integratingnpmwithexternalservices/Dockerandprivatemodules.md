+++
title = "Docker 和私有模块"
date = 2023-09-22T21:01:25+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文: [https://docs.npmjs.com/docker-and-private-modules](https://docs.npmjs.com/docker-and-private-modules)

# Docker and private modules - Docker 和私有模块

To install private npm packages in a Docker container, you will need to use [Docker build secrets](https://docs.docker.com/develop/develop-images/build_enhancements/#new-docker-build-secret-information).

​	要在 Docker 容器中安装私有的 npm 包，您需要使用[Docker 构建机密](https://docs.docker.com/develop/develop-images/build_enhancements/#new-docker-build-secret-information)。

## 背景：运行时变量 Background: runtime variables

You cannot install private npm packages in a Docker container using only runtime variables. Consider the following Dockerfile:

​	您无法仅使用运行时变量在 Docker 容器中安装私有的 npm 包。考虑以下 Dockerfile：

```
FROM node

COPY package.json package.json
RUN npm install

# Add your source files
COPY . .
CMD npm start
```

Which will use the official [Node.js](https://hub.docker.com/_/node) image, copy the `package.json` into our container, installs dependencies, copies the source files and runs the start command as specified in the `package.json`.

​	该 Dockerfile 使用官方的 [Node.js](https://hub.docker.com/_/node) 镜像，将  `package.json`  复制到容器中，安装依赖项，复制源代码文件，并根据  `package.json`  中指定的启动命令运行。

In order to install private packages, you may think that we could just add a line before we run `npm install`, using the [ENV parameter](https://docs.docker.com/engine/reference/builder/#env):

​	为了安装私有包，您可能会认为我们只需要在运行  `npm install`  之前添加一行，使用 [ENV 参数](https://docs.docker.com/engine/reference/builder/#env)：

```docker
ENV NPM_TOKEN=00000000-0000-0000-0000-000000000000
```

However, this doesn't work as you would expect, because you want the npm install to occur when you run `docker build`, and in this instance, `ENV` variables aren't used, they are set for runtime only.

​	然而，这不会按您期望的方式工作，因为您希望 npm install 在运行  `docker build`  时发生，而在这种情况下， `ENV`  变量不会被使用，它们仅用于运行时。

Instead of run-time variables, you must use Docker build secrets.

​	而不是运行时变量，您必须使用 Docker 构建机密。

## 更新 Dockerfile Update the Dockerfile

The Dockerfile that takes advantage of this has a few more lines in it than the earlier example that allows us to use your global `.npmrc` and the access token created when running `npm login` command (if you haven't run it already - do so before moving on).

​	利用此功能的 Dockerfile 比之前的示例要多几行，这样我们就可以使用全局的  `.npmrc`  文件和在运行  `npm login`  命令时创建的访问令牌（如果您尚未运行该命令，请在继续之前运行它）。

```dockerfile
# https://docs.npmjs.com/docker-and-private-modules
FROM node:18

ENV APP_HOME="/app"

WORKDIR ${APP_HOME}

COPY package*.json ${APP_HOME}/

RUN --mount=type=secret,id=npmrc,target=/root/.npmrc npm install

COPY . ${APP_HOME}/

CMD npm start
```

This will configure your Dockerfile to receive `.npmrc` file via build secrets, that will leave no trace after npm dependency installation is done.

​	这将配置您的 Dockerfile 以通过构建机密接收  `.npmrc`  文件，在 npm 依赖项安装完成后不会留下任何痕迹。

## 构建 Docker 镜像 Build the Docker image

To build the image using the above Dockerfile and the npm authentication token, you can run the following command. Note the `.` at the end to give `docker build` the current directory as an argument.

​	要使用上述 Dockerfile 和 npm 认证令牌构建镜像，可以运行以下命令。注意最后的  `.` ，将当前目录作为参数传递给  `docker build` 。

```shell
docker build . -t secure-app-secrets:1.0 --secret id=npmrc,src=$HOME/.npmrc
```

This will build the Docker image with the access token coming from your global `.npmrc` file received via build secrets, so you can run `npm install` inside your container as the current logged-in user.

​	这将使用通过构建机密接收的全局  `.npmrc`  文件中的访问令牌构建 Docker 镜像，因此您可以在容器内以当前登录的用户身份运行  `npm install` 。

**Note:** You may need to specify a working directory different from the default `/` otherwise some frameworks like Angular will fail.

**注意：**您可能需要指定一个与默认的  `/`  不同的工作目录，否则某些框架（如 Angular）可能会失败。
