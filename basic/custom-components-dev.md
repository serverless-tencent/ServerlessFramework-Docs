---
title: "多组件应用开发"
menuText: "多组件应用开发"
layout: Doc
---

# 多组件应用开发

完成 Serverless Framework 安装后，可以通过以下指令，快速初始化一个示例项目，并在此基础上进行改造开发：

```
sls init scf-demo
```

通过该指令，我们在本地快速构建了一个基本的函数应用，目录结构如下：

```
.
├── serverless.yml  # 配置文件
└── src
   └── index.js # 入口函数
```

进入该目录，可以在示例模版的基础上进行项目的开发。

> `sls init` 支持快速初始化多个项目模版，请通过 `sls registry`查看所有支持的项目模版。

### 构建多组件应用

Serverless Framework 提供了多个基础资源组件，用户可以通过不同组件的结合使用，快速完成云端资源的创建与部署，无需在控制台手动操作。

查看[基础组件列表与配置方式]()。

此处以部署一个使用 COS 触发器触发的函数项目为例，教您如何在项目中引入多个组件，并快速完成部署，步骤如下：

1. 调整项目目录结构，新建 cos 文件夹，并在该目录下完成 COS 组件的配置文件 `serverless.yml` 的编写，调整后的目录结构：

   ```
   .
   ├── src
   │   ├── serverless.yml # 函数配置文件
   │   └── index.js # 入口函数
   ├── cos
   │   └── serverless.yml # 对象存储 COS 桶配置文件
   └── .env # 环境变量文件
   ```

   cos 组件的 yml 文件示例如下，全量配置文件可参考 [COS 组件全量配置](https://github.com/serverless-components/tencent-cos/blob/master/docs/configure.md)

   ```yml
   app: appDemo
   stage: dev

   component: cos
   name: cosdemo

   inputs:
     bucket: my-bucket
     region: ap-guangzhou
   ```

2. 修改 SCF 项目的 yml 配置文件，在触发器配置部分按以下语法引用 COS 组件的部署结果：

   ```yml
   app: appDemo
   stage: dev

   component: scf
   name: scfdemo
   inputs:
     ...
     events:
      - cos: # cos触发器
           parameters:
             bucket: ${output:${stage}:${app}:cosdemo.bucket}
   ```

   > 注意：同一个项目内部署多个组件实例时，需要保证每个项目的 `app`、`stage` 参数相同，否则无法成功引用。

3. 在项目根目录下，执行 `sls deploy`，即可完成 COS 桶的创建，并将 COS 组件的输出作为 SCF 组件的输入完成触发器的配置。
