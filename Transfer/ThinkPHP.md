---
title: 'ThinkPHP 框架迁移'
menuText: 'ThinkPHP 框架迁移'
layout: Doc
---


通过 [Serverless Framework ThinkPHP 组件](https://github.com/serverless-components/tencent-thinkphp)，可以快速实现 ThinkPHP 应用从本地到 Serverless 函数平台的迁移。

 > 注意：支持 ThinkPHP >= 6.x

## 迁移前提

- 已经 [安装 Serverless Framework 1.67.2](../quickstart/installation) 以上版本。
- 已经[注册腾讯云账号](https://cloud.tencent.com/document/product/378/17985)并完成[实名认证](https://cloud.tencent.com/document/product/378/10495)。

  > 如果您的账户为**腾讯云子账号**，请首先联系主账号，参考 [账号和权限配置](../quickstart/credential) 进行授权。


## 操作步骤

### 1. （可选）初始化 ThinkPHP 模版项目
如果您本地并没有 ThinkPHP 项目，可通过以下指令完成 ThinkPHP 项目初始化（本地已有项目可跳过该步骤）
```
composer create-project topthink/think serverless-thinkphp
```
> 注意：ThinkPHP 使用 Composer 管理依赖，所以需要先自行安装 Composer，请参考 [官方安装文档](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-macos)


### 2. 配置 yml 文件
在项目根目录下，新建 `serverless.yml` 文件，并将下列配置模版粘贴到文件中，实现基本的项目配置。
>基于您实际部署需要，您可以在 `serverless.yml` 中完成更多配置，yml 文件的配置信息请参考[ ThinkPHP 组件全量配置](https://github.com/serverless-components/tencent-thinkphp/blob/master/docs/configure.md)

```sh
touch serverless.yml
```

```yml
# serverless.yml
app: appDemo
stage: dev
component: thinkphp
name: thinkphpDemo

inputs:
  src:
    src: ./
    exclude:
      - .env
  region: ap-guangzhou
  runtime: Php7
  apigatewayConf:
    protocols:
      - http
      - https
    environment: release
```

### 3. 应用部署
> 注意：**在部署前，需要先清理本地运行的配置缓存，执行 `php think clear` 即可。**
通过 `sls deploy` 命令进行部署，并可以添加 --debug 参数查看部署过程中的信息。

```
sls deploy --debug
```
部署完成后，通过访问输出的 API 网关链接，完成对应用的访问。
