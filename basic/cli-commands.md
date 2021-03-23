---
title: "CLI 命令"
menuText: "CLI 命令"
layout: Doc
---

目前 Serverless Framework 支持的基本指令如下，您也可以通过输入 `“serverless --help`，查看所有支持的指令。

### 应用部署指令

- **`serverless login`**：支持通过 login 命令，通过微信扫描二维码的方式，登录腾讯云账号并授权对关联资源进行操作。

- **`serverless init xxx`**：从注册中心下载指定模版，init 后填入您想下载的模版名称，例 "$ serverless init fullstack"

  `sls init xxx --name my-app`：支持自定义项目目录名称。

  `--debug`：列出模版下载过程中的日志信息。

- **`serverless deploy`**：部署实例到云端。

  `--debug`：列出组件部署过程中 `console.log()` 输出的部署操作和状态等日志信息。

  `--target ./src`： 部署该目录下指定 Serverless 实例

  ` --inputs traffic=0.1 public=true`：部署时切换 10%流量到 $latest 函数版本，其余流量到最后一次发的函数版本上。

- **`serverless remove`**：从云端移除一个 Component 实例。

  `--debug`：列出组件移除过程中 `console.log()` 输出的移除操作和状态等日志信息。

  `--target ./src`： 移除该目录下指定 Serverless 实例

- **`serverless info`**：获取并展示一个 Component 实例的相关信息。

  `--debug`：列出更多 `state`。

- **`serverless dev`**：启动 DEV MODE 开发者模式，通过检测 Component 的状态变化，自动部署变更信息。同时支持在命令行中实时输出运行日志，调用信息和错误等。此外，支持对 Node.js 应用进行云端调试。

### 模版开发指令

- **`serverless registry`**：查看可用的组件与应用模版列表。

- **`serverless publish`**：发布组件或应用模版到 Serverless 注册中心。

  `--dev`：支持 dev 参数用于发布 `@dev` 版本的 Component，用于开发或测试。

## 项目部署

完成本地项目开发后，通过 Serverless Framework，可以快速将项目部署到云端，具体操作如下:

```sh
sls deploy
```

输入该指令后，Serverless Framework Cli 将会为您完成以下操作：

**1. 扫码授权**

通过扫描二维码，完成一键授权，授权后 Cli 工具会将生成临时密钥信息写入当前目录下的` .env` 文件里，临时密钥的有效时间 2 小时，失效后，部署的时候会引导您重新扫码鉴权。

如果不想重复扫码，您也可以将永久密钥配置在项目目录下的 `.env`文件中：
`# .env TENCENT_SECRET_ID=xxxxxxxxxx #您账号的 SecretId TENCENT_SECRET_KEY=xxxxxxxx #您账号的 SecretKey`

SecretId 和 SecretKey 可以在 [API 密钥管理](https://console.cloud.tencent.com/cam/capi) 中获取 。

**2. 打包上传**

完成授权后，Serverless Framework Cli 会根据您在 `serverless.yml` 文件中配置的项目代码路径，自动为您进行项目的打包与上传。

**3. 云端部署**

上传后的项目，会根据您在 yml 文件中进行的参数配置，完成云上资源的创建，部署完成后，命令行会输出部署后的资源信息。

### 高级能力

- 查看部署过程中的具体日志信息
  ```
  sls deploy --debug
  ```
- 多版本部署时，切换指定流量到 $latest 函数版本，其余流量到最后一次发的函数版本上，实现灰度发布。
  ```
  sls deploy --inputs traffic=0.1 public=true
  ```
- 应用目录下含有多个 serverless 实例，只需要更新指定项目时

  ```
  sls deploy --target xxx
  ```

  例：在该项目根目录下，通过指令 `sls deploy --target ./cos`，仅更新 cos 实例，其它实例不受影响

  ```
  .
  ├── src
  │   ├── serverless.yml
  │   └── index1.js
  ├── cos
  │   └── serverless.yml
  ├── db
  │   └── serverless.yml
  └── .env
  ```

### 查看部署信息

完成部署后，通过以下指令，查看项目的部署信息：

```
sls info
```

### 常见问题 Q&A

如您的环境配置了代理，可能会出现以下问题：

- 问题 1：输入 `serverless` 时没有默认弹出中文引导。

  解决方案： 请确认您的 IP 在中国大陆区域，并在 .env 文件中增加配置 SERVERLESS_PLATFORM_VENDOR=tencent 即可。

- 问题 2：输入 `sls deploy` 后部署报网络错误。

  解决方案：在 .env 文件中增加以下代理配置。

  ```
  HTTP_PROXY=http://127.0.0.1:12345 #请将'12345'替换为您的代理端口
  HTTPS_PROXY=http://127.0.0.1:12345 #请将'12345'替换为您的代理端口
  ```

## 项目删除

通过以下指令，可以快速删除云端资源：

```sh
sls remove
```

### 高级能力

- 查看删除过程中的具体日志信息

  ```
  sls remove --debug
  ```

- 应用目录下含有多个 serverless 实例，只需要删除指定项目时

  ```
  sls remove --target xxx
  ```

  例：在该项目根目录下，通过指令 `sls remove --target ./cos`，仅移除 cos 实例，其它实例不受影响

  ```
  .
  ├── src
  │   ├── serverless.yml
  │   └── index1.js
  ├── cos
  │   └── serverless.yml
  ├── db
  │   └── serverless.yml
  └── .env
  ```

### 常见问题 Q&A

- 执行 `sls remove` 时，会移除哪些云端资源？

  Serverless Framework 根据 yml 配置文件完成云端资源的移除，因此，只要通过 yml 文件创建的资源，都会进行删除操作，但如果引用的已有资源，则不会进行移除。举例如下：

  通过 scf 组件部署函数时，选择新建 api 网关触发器进行部署，则在删除时，创建的函数与 API 网关资源都会进行删除；

  选择已有 api 网关触发器进行部署，则在删除时，仅删除函数资源，使用的 API 网关不会进行删除操作。
