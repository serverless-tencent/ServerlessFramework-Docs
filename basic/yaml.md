---
title: "YAML 配置"
menuText: "YAML 配置"
layout: Doc
---

Serverless Framework 通过项目配置文件 `serverless.yml` 完成应用的类型识别与资源配置，本地开发完成后的项目，必须先配置 yml 文件，才可以通过运行 `sls deploy` 命令，将 serverless.yml 中的配置文件和 inputs 中指定参数或代码目录会都被传入 Serverless Components 部署引擎中，从而完成云端部署。

### 基本信息

一个基本的 `serverless.yml` 文件里，第一层配置字段为以下内容：

```yml
#应用组织信息（可选）
app: "" # 应用名称。留空则默认取当前组件的实例名称为app名称。
stage: "" # 环境名称。默认值是 dev。建议使用${env.STAGE}变量定义环境名称

#组件信息
component: scf # (必选) 组件名称，在该实例中为scf
name: scfdemo # (必选) 组件实例名称。

#组件参数配置，根据每个组件，实现具体的资源信息配置
inputs:
```

### 详细配置

接下来在 `inputs` 字段里，根据每个组件创建的云上资源，会进行对应的信息配置，此处以[云函数 SCF 组件](https://github.com/serverless-components/tencent-scf)为例，input 字段内的二级目录如下：

```yml
inputs:
  name: xxx # 云函数名称，默认为 ${name}-${stage}-${app}
  src: ./src # 项目代码路径，默认写法，新建特定命名的 cos bucket 并上传
  handler: index.main_handler #入口
  runtime: Nodejs10.15 # 运行环境 默认 Nodejs10.15
  region: ap-guangzhou # 函数所在区域
  description: This is a function in ${app} application.
  environment: #  环境变量
    variables: #  环境变量对象
      TEST: value
  layers: #layer配置
    - name: scfLayer #  layer名称
      version: 1 #  版本
  events: # 触发器配置
    - timer: # 定时触发器
        parameters:
          cronExpression: "*/5 * * * * * *" # 每5秒触发一次
          enable: true
```

### 全量配置列表

目前 Serverless Framework 各个组件的全量配置信息列表如下：

#### 基础组件

| 组件名称        | 全量配置                                                                                                             |
| --------------- | -------------------------------------------------------------------------------------------------------------------- |
| SCF 组件        | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-scf/blob/master/docs/configure.md)        |
| Website 组件    | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-website/blob/master/docs/configure.md)    |
| API 网关组件    | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-apigateway/blob/master/docs/configure.md) |
| VPC 组件        | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-vpc/blob/master/docs/configure.md)        |
| COS 组件        | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-cos/blob/master/docs/configure.md)        |
| PostgreSQL 组件 | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-postgresql/blob/master/docs/configure.md) |
| CynosDB 组件    | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-cynosdb/blob/master/docs/configure.md)    |
| CDN 组件        | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-cdn/blob/master/example/serverless.yml)   |
| Layer 组件      | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-layer/blob/master/docs/configure.md)      |

#### 框架组件

| 组件名称      | 全量配置                                                                                                           |
| ------------- | ------------------------------------------------------------------------------------------------------------------ |
| Express 组件  | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-express/blob/master/docs/configure.md)  |
| Koa 组件      | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-koa/blob/master/docs/configure.md)      |
| Egg 组件      | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-egg/blob/master/docs/configure.md)      |
| Next.js 组件  | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-nextjs/blob/master/docs/configure.md)   |
| Nuxt.js 组件  | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-nuxtjs/blob/master/docs/configure.md)   |
| Flask 组件    | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-flask/blob/master/docs/configure.md)    |
| Django 组件   | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-django/blob/master/docs/configure.md)   |
| Laravel 组件  | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-laravel/blob/master/docs/configure.md)  |
| ThinkPHP 组件 | [serverless.yml 全量配置](https://github.com/serverless-components/tencent-thinkphp/blob/master/docs/configure.md) |

### 变量引用说明

`serverless.yml` 支持多种方式引用变量

- 顶级参数引用
  在 `inputs` 字段里，支持直接引用顶级配置信息，引用语法如下：`${org}`、`${app}`
- 环境变量引用

  在 `serverless.yml` 中，可以直接通过 `${env}` 的方式，直接引用环境变量配置（包含 .env 文件中的环境变量配置，以及手动配置在环境中的变量参数）

  例如，通过`${env:REGION}`，引用环境变量 REGION

- 引用其它组件输出结果

  如果希望在当前组件配置文件中引用其他组件实例的输出信息，可以通过如下语法进行配置：`${output:[app]:[stage]:[instance name].[output]}`

示例 yml：

```yml
app: demo
component: scf
name: rest-api
stage: dev

inputs:
  name: ${stage}-${app}-${name} # 命名最终为 "dev-demo-rest-api"
  region: ${env:REGION} # 环境变量中指定的 REGION= 信息
  vpcName: ${output:prod:my-app:vpc.name} # 获取其他组件中的输出信息
  vpcName: ${output:${stage}:${app}:vpc.name} # 上述方式也可以组合使用
```

## Stage

由于云上不同服务对环境的概念不同，Serverless Framework 支持通过 `stage` 参数配置，实现多环境模拟，此处以 `Express` 项目为例，示例 `serverless.yml` 文档如下：

```
component: express
name: expressDemo
app: appDemo
stage: test  #想要模拟多环境时，此参数必填，代表不同环境

inputs:
   functionName: expressDemo-${stage} #想要模拟多环境，此参数必填
   src: ./ #需要上传的项目路径
   region: ap-guangzhou
   runtime: Nodejs10.15
   apigatewayConf:
      protocols:
        - http
        - https
      environment: test
      # 该参数为 API 网关产品环境参数，仅支持 test（测试环境）、prepub（预发布环境）和 release（发布环境），建议和 stage 一致
```

除了基本的必填参数之外，为了实现多环境配置，以下参数也是必填的：

1）`stage` 参数：关键参数，规定不同环境

2）`functionName` 参数：函数名称，需要写为 `FunctionName-${stage}` 格式，其中的 `stage` 变量必须引入，如果没这个变量，则不同环境的函数会相互覆盖。

3）`environment`: 是配置云函数的调用 API 环境，仅支持 test（测试环境）、prepub（预发布环境）和 release（发布环境），为方便管理，建议和 stage 一致

完成 yml 配置后，只需更新 `stage` 参数，即可完成应用不同环境的切换。
