---
title: "函数 CLI 命令"
menuText: "函数 CLI 命令"
layout: Doc
---

<!-- TODO: 更新函数命令。 -->

<!-- <!-- -->

Serverless Tencent CLI 支持以下功能命令：

### Create 创建新的服务

通过 create 命令可以创建函数服务项目。

```sh
# 在向前目录下创建新的函数服务
$ serverless create --template tencent-nodejs

# 在向前目录下创建新的函数服务并指定目录名称
$ serverless create --template tencent-nodejs --path myService

# 在向前目录下通过指定路径创建新的函数服务并指定目录名称
$ serverless create --template-url https://github.com/serverless/serverless/tree/master/lib/plugins/create/templates/tencent-nodejs --path myService
```

#### 命令选项

- `--template` 或 `-t` 模板名称。
- `--template-url` 或 `-u` 远程模板的 URL 地址。
- `--template-path` 本地模板路径。
- `--path` 或 `-p` 创建服务的目标目录路径。
- `--name` 或 `-n` 指定服务名称。

> 需要指定至少 `--template`,` --template-url`, `--template-path` 中的一个。

####  函数服务模板 （sls init）

可以通过命令 `serverless create --help` 查看全部可用的函数服务模板。

以下是常用的函数服务模板

- tencent-nodejs
- tencent-python
- tencent-php
- tencent-go

> 函数服务模板默认本会部署最新版本的运行时，比如：Node.js 12.15。如果想要指定运行时，请修改配置文件`serverless.yml`中的`runtime`字段。

### install 通过 URL 安装服务 （不支持）

通过 Github URL 地址安装函数服务

```sh
# 在向前目录下通过指定路径创建新的函数服务并指定目录名称
$ serverless install --url https://github.com/serverless-tencent/serverless-tencent-scf/tree/master/templates/tencent-nodejs
```

#### 命令选项

- `--url` 或 `-u` 远程服务 Github URL 地址。
- `--name` 或 `-n` 指定服务名称。

> 需要指定至少 `--template`,` --template-url`, `--template-path` 中的一个。

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

### deploy 部署服务 （）

通过此命令来部署发布整个服务，当修改了 serverless.yml 后应当使用这种方式进行部署。

```sh
# 部署函数服务
$ serverless deploy --stage prod
```

#### 命令选项

- `--config` 或 `-c` 指定你的配置文件，默认为 serverless.yml|.yaml|.js|.json。
- `--stage` 或 `-s` 想要部署函数服务的环境名称。
- `--region` 或 `-r` 想要部署函数所在环境的地区名称。
- `--package` 或 `-p` 打包前的路径，并跳过打包步骤。
- `--force` 强制部署，强制部署时 trigger 也会更新。
- `--function` 或 `-f` 调用 `deploy function`

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

### deploy list 查看函数信息 （腾讯没有数据）

通过此命令查看你的部署相关信息。

```sh
# 查看所有可用的部署信息
$ serverless deploy list

# 查看所有已经部署的函数
$ serverless deploy list functions
```

#### 命令选项

- `--stage` 或 `-s` 要查看信息的环境名称。
- `--region` 或 `-r` 要查看信息的环境的地区名称。

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

### metrics 查看函数的统计信息 （目前没有实现， 可以通过 API 获取。）

通过此命令查看某一个函数的统计信息。

```sh
# 查看过去24小时的统计信息
$ serverless metrics

# 查看指定时间区间的统计信息
$ serverless metrics --startTime "2019-11-01 00:00:00" --endTime "2019-11-02 00:00:00"

# 查看指定函数的指定时间区间的统计信息
$ serverless metrics --function hello --startTime "2019-11-01 00:00:00" --endTime "2019-11-02 00:00:00"
```

#### 命令选项

- `--function` or `-f` 查看统计信息的函数名称。
- `--stage` or `-s` 要查看统计信息的环境名称。
- `--region` or `-r` 要查看统计信息的环境的地区信息。
- `--startTime` 要查看统计信息的开始时间戳 (如: "2019-7-12 00:10:00").
- `--endTime` 要查看统计信息的结束时间戳 (如: "2019-7-12 00:10:00").

### info 查看部署服务信息

查看部署服务的信息，比如运行时，地区，环境，和函数列表。

```sh
# 查看已部署函数服务的信息
$ serverless info
```

#### 命令选项

- `--stage` or `-s` 要查看函数服务的环境名称。
- `--region` or `-r` 要查看函数服务的环境的地区名称。

### rollabck 回滚服务

## 灰度切换。 $Latest, $7, $7, ()

通过此命令回滚到服务的指定时间部署版本。

```sh
#
$ serverless rollback --timestamp timestamp
```

> 如果么有提供时间戳信息，这条命令会显示所有的部署信息。

#### 命令选项

- `--timestamp` or `-t` 要回滚的部署版本的时间戳。
- `--verbose` or `-v` 显示所有的历史部署版本。

### remove 删除服务

通过此命令移除当一个已经部署的函数服务。

```sh
# 移除当前服务(dev, ap-guangzhou 默认的 stage 和 region)
$ serverless remove

$ serverless remove --stage dev --region ap-guangzhou
```

#### 命令选项

- `--stage` or `-s` 要移除服务的环境名称。
- `--region` or `-r` 要移除服务的环境的地区名称。
  -->
