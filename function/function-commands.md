---
title: "函数 CLI 命令"
menuText: "函数 CLI 命令"
layout: Doc
---

<!-- TODO: 更新函数命令。 -->

> 函数组件命令需要在函数组件目录下执行，组件命令同样适用与函数组件，同时函数组件具有以下帮助进行函数开发的命令。

Serverless Tencent CLI 支持以下功能命令：

<!--

### deploy function 部署函数 （暂不支持）

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

### invoke 调用函数 (即将上线)

通过此命令调用已部署函数，同时可以发送 event 数据到函数，查看日志，以及其他函数调用相关信息。

```sh
# 调用名为functionName的已部署函数
$ serverless invoke --function functionName
```

#### 命令选项

-  `--function` 或 `-f` 调用的函数名称，默认使用配置handler指定函数
-  `--stage` 或 `-s` 调用的函数的环境名称，默认使用配置环境
-  `--region` 或 `-r` 调用的函数的地区名称，默认使用配置地区
-  `--data` 或 `-d` 调用函数的事件(event)参数的序列化数据(String)
-  `--path` 或 `-p` 调用函数的事件(event)参数的 json 文件路径

> 使用单函数 SCF Component 不需要指定 `function` 参数， 只有多函数组件需要指定 `funciton` 参数

### invoke local 本地调用 (即将上线)

通过此命令在本地调用函数。 同时可以发送 event 和 context 数据到函数进行数据模拟。

```sh
# 调用单函数应用函数
$ serverless invoke local

# 调用单函数应用函数并制定 Event 数据
$ serverless invoke local --data '{"foo":"bar"}'
```

#### 命令选项

* `--function`  或  `-f` 调用函数名称，默认使用配置handler指定函数

* `--data` 或 `-d` 调用函数的事件(event)参数的序列化数据(String)

* `--path` 或 `-p` 调用函数的事件(event)参数的 json 文件路径

* `--context` 调用函数的上下文(context)参数的序列化数据(String)

* `--contextPath` 或 `-x` 调用函数的上下文(context)参数的 json 文件所在路径

  > 本地调试函数目前仅支持 Node.js, 其他运行时的支持会在后续陆续推出。
  >
  > 使用单函数 SCF Component 不需要指定 `function` 参数， 只有多函数组件需要指定 `funciton` 参数。

### logs 查看日志 (即将上线)

通过此命令查看某一个函数的日志信息。

```sh
# 查看函数 helloFunc 的日志
$ serverless logs -f helloFunc

# 查看函数 helloFunc 的最新日志并持续监听最新日志
$ serverless logs -f hello -t
```

#### 命令选项

- `--function` 或 `-f` 查看指定函数的日志，默认使用配置handler指定函数
- `--stage` 或 `-s` 查看日志的环境名称，默认使用配置环境
- `--region` 或 `-r` 查看日志地区名称，默认使用配置地区
- `--startTime` 查看日志的开始时间，如：3d, 20130208T080910，默认10m
- `--tail` 或 `-t` 查看最新日志
- `--interval` 或 `-i` 最新日志的刷新时间 默认：1000ms

> 使用单函数 SCF Component 不需要指定 `function` 参数， 只有多函数组件需要指定 `funciton` 参数

### 其他组件命令

同时其他[组件命令](../components/components-commands.md)也可以在函数组件中使用。