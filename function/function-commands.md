---
title: "函数 CLI 命令"
menuText: "函数 CLI 命令"
layout: Doc
---

<!-- TODO: 更新函数命令。 -->

> 函数组件命令需要在函数组件目录下执行，组件命令同样适用与函数组件，同时函数组件具有以下帮助进行函数开发的命令。

Serverless Tencent CLI 支持以下功能命令：

<!--
### deploy function 部署函数 （不支持）

通过此命令来部署一个单独函数，如果仅仅修改了函数代码 建议使用此方式进行快速部署。

```sh
# 部署functionName的函数
$ serverless deploy function -f functionName
```

#### 命令选项

- `--function` 或 `-f` 远程服务 Github URL 地址。
- `--stage` 或 `-s` 指定服务名称。
- `--region` 或 `-r` 指定服务名称。

-->

### invoke 调用函数

调用已部署函数，同时可以发送 event 数据到函数，查看日志，以及其他函数调用相关信息。

```sh
# 调用名为functionName的已部署函数
$ serverless invoke --function functionName
```

#### 命令选项

- `--function` 或 `-f` 要调用的函数名称。
- `--stage` 或 `-s` 要调用的函数的环境名称。
- `--region` 或 `-r` 要调用的函数的环境的地区名称。
- `--data` 或 `-d` 要传递给调用函数的序列化事件数据(String)
- `--path` 或 `-p` 要传递给调用函数的 json 文件所在路径(函数服务根目录的相对路径)。

### logs 查看日志 （现在不支持，计划支持）

通过此命令查看某一个函数的日志信息。

```sh
# 查看函数 helloFunc 的日志
$ serverless logs -f helloFunc

# 查看函数 helloFunc 的最新日志并持续监听最新日志
$ serverless logs -f hello -t
```

#### 命令选项

- `--function` or `-f` 要查看日志的函数名称。
- `--stage` or `-s` 要查看日志的函数的环境名称。
- `--region` or `-r` 要查看日志的函数的环境的地区名称。
- `--startTime` 查看日志的开始时间戳 (如: 2019-7-12 00:00:00 ).
- `--tail` or `-t` 查看最新的日志，并持续监听。
- `--interval` or `-i` 查看最新日志的监听间隔。

### info 查看部署服务信息

查看部署服务的信息，比如运行时，地区，环境，和函数列表。

```sh
# 查看已部署函数服务的信息
$ serverless info
```

#### 命令选项

- `--stage` or `-s` 要查看函数服务的环境名称。
- `--region` or `-r` 要查看函数服务的环境的地区名称。
