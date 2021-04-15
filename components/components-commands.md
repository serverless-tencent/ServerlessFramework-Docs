---
title: "组件 CLI 命令"
menuText: "组件 CLI 命令"
layout: Doc
---

<!-- TODO: 更新 组件命令 说明 -->

Serverless Components CLI 支持以下功能命令：

- 需要在 Serverless Components 项目目录中执行
- 也可以通过输入 `“serverless --help-compoents`，查看组件帮助指令。

### init 创建组件应用

通过指定组件模板创建组件应用

```sh
# 初始 Express 组件应用
$ sls init express-starter

# 初始 Express 组件应用并指定目录名称
$ sls init express-starter --name my-express-app
```

#### 命令选项

- `--name` 指定组件应用目录名称。（组件应用名称会在由目录名称与随机字符串拼接沟通，详情查看 `serverless.yml` 中 `app` 字段。）

> 更多可用的组件模板请通过命令 `serverless registry` 进行查看。

### deploy 部署组件应用

将组件应用部署到云端服务器

```sh
# 部署组件应用到到云端服务器
$ sls deploy

# 部署指定目录下的组件实例到云端服务器(适用与多组件应用)
$ sls deploy --target ./src
```

#### 命令选项

- `--target` 指定部署的组件应用目录。（适用与多组件应用）

### info 查看组件应用信息

查看组件应用的信息详情，包含

```sh
# 查看组件应用的信息
$ sls info
```

一下是一个 express 组件应用的信息示例。

```sh
serverless ⚡ components


最后操作:  deploy (a day ago)
部署次数:  1
应用状态:  active

region: ap-guangzhou
scf:
  functionName: express_component_g6zinoh
  runtime:      Nodejs10.15
  namespace:    default
  lastVersion:  $LATEST
  traffic:      1
apigw:
  serviceId:   service-4mekuq1y
  subDomain:   service-4mekuq1y-1302533238.gz.apigw.tencentcs.com
  environment: release
  url:         https://service-4mekuq1y-1302533238.gz.apigw.tencentcs.com/release/

应用控制台: https://console.cloud.tencent.com/ssr/detail?stageName=dev&appName=express-example-c2482779&instanceName=express-starter&stageList=dev

express-starter › 信息成功加载
```

### dev 组件应用调试

进入调试模式对组件应用进行调试，更多调试模式详情请参考[](../basic/dev-mode.md)

```sh
# 进入组件应用的开发调试模式
$ sls dev
```

### remove 删除组件应用

```sh
# 删除组件应用实例
$ sls remove

# 删除指定目录下的组件应用实例
$ sls remove --target ./src
```

### registry 组件注册中心

查看在应用中心发布的组件模板信息

```sh
# 查看全部组件模板信息
$ sls registry

# 查看指定组件模板信息
$ sls registry express-starter
```
