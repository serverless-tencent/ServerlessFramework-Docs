---
title: "Serverless Framework 介绍"
menuText: "Serverless Framework 介绍"
layout: Doc
---

# ⚡️ Serverless 简介

Serverless Framework 是业界非常受欢迎的无服务器应用框架，通过与众多一流云供应商如腾讯云，AWS 等的紧密合作，为广大开发者提供无需关心底层基础设施，即可编写和部署代码的无服务开发体验。

Serverless Framework 同时提供资源管理、自动伸缩、统计分析等能力，让广大开发者可以节省运维成本，真正做到“按量付费”的同时，也无需花费精力处理日志收集，异常统计等任务。

Serverless Framework 通过 CLI 工具与腾讯云紧密合作，为中国用户提供了基于组件(serverless components)的完整解决方案。覆盖了无服务应用编码、测试、部署，等全生命周期，同时更符合中国用户的使用场景和习惯。

## 开始使用

通过 Serverless CLI 工具可以创建，调试，部署，查看，移除 serverless 应用，马上[安装 Serverless CLI](./quickstart/installation.md) 并使用。

### 函数应用开发

Serverless 为函数应用开发者提供了一个统一的开发框架，通过 serverelss 开发者可以快速开发，调试，部署。结合静态站点，API 网关，数据库等其他云上资源，函数应用拥有更强大的能力和使用场景。

开始 [使用 serverless 开发函数应用](./quickstart/function-dev.md)

### 组件应用开发

Serveless 为使用传统框架(如：Nextjs, Express, Django 等)开发的应用提供了运行环境支持，通过 serverless 组件开发者可以继续使用传统框架开发应用，也可以通过简单改造将原有应用迁移到 serverless 平台。

开始 [使用 serverless 开发组件应用](./quickstart/components-dev.md)

### SaaS 应用托管

Serverless 为使用 SaaS 应用(如：Wordpress 等)提供了方便的运行环境支持，通过 serverless 简单配置就可以部署并开始使用 SaaS 应用，也无需担心应用的后续维护和升级。

## 独特优势

### 多语言，传统框架支持、远程调试

- Serverless Framework 支持众多编程语言，包含：Node.js, Python, PHP, Java, Go 等。通过 Serverless Tencent 用户可以快速进行函数开发，无需关心各个云平台的不同用法和配置操作。

- Serverless Framework 支持使用传统开发框架进行开发，包括：Express, Koa, Egg.js, next.js, nuxt.js, react.js, vue.js, Flask, Laravel 等。通过 Serverless Components 可以在不替换现有应用框架的情况下获得 serverless 的众多优势。

- Serverless Framework 支持远程在线调试，开发者无需在本地启动任何服务即可开始调试代码。

### 灵活配置、一键部署、日志报警

- Serverless Framework 通过一个 serverless.yml 几行配置即可完成所有基础设施（云函数、API 网关、COS、DB 等）的创建，部署，和修改。

- Serverless Framework 通过一个命令或者控制台一个按键即可完成在不同环境(stage)和资源地区(region)的应用部署工作。同时相比传统部署方式，通过 Serverless Framework 进行部署速度可以提升 20 倍。

- Serverless Framework 与腾讯云深度合作，为用户提供了更强大的日志收集，统计分析，异常报警服务。开发者无需任何配置即可直接使用。

### 高可用、低成本、弹性扩容

- Serverless Framework 通过与腾讯云深度合作，以及 SCF 的灰度功能为广大开发者提供了一个简单有效的应用托管平台，通过 Serverless Framework 部署的应用可靠性可以达到 99.5% 的可靠性，同时在出现代码问题时，可以快速切换至指定版本。

- Serverless Framework 通过按量计费，尽在用户的代码触发后运行时才会计费，在闲置时间不收取任何费用，相比传统虚拟机的包月/包年服务可以做多为用户用户节省 90%的使用成本。

- Serverless Framework 能够根据业务请求自动进行弹性伸缩，在服务达到峰值时会自动扩容，添加更多服务资源来为用户的应用提供支持，并在高峰过去之后，恢复收缩到扩容之前的状态。进一步保证了应用的可用性并降低了使用成本。

## 概念 & 术语

### Serverless Framework

Serverless Framework 是基于下一代公有云服务提供的弹性扩容，并按量付费的无服务器计算解决方案，从而大大降低构建和维护应用的开销，供开发者专注业务逻辑开发。

### [//]: Serverless Tencent

[//]:  Serverless Tencent 是 Serverless 的腾讯云版本，主要为广大中国开发者提供函数服务开发能力。 同时支持事件触发，弹性扩容，并且按量付费。相比于 serverless, serverless-tencent 使用更简洁，高效，同时也内置了众多 serverless plugin 功能支持。

[//]: 详细介绍可以参考 [Github 上的 Serverless 项目](https://github.com/serverless/serverless/blob/master/README_CN.md)。

### Serverless Components

Serverless Components 通过定制的基础设施支持更多开发场景，如 Express, Next.js, Wordpress 等。同时具有 serverless 的弹性扩缩容，按量付费等优势。让开发者在不改变代码和开发习惯的情况下获得 serverless 的强大优势。

详细介绍可以参考 [Github 上的 Serverless Components 项目](https://github.com/serverless/components/blob/master/README.cn.md)。

#### SCF Component

目前腾讯云的函数开发也通过组件提供了支持，可以使用 SCF 组件的对应运行时组件来进行函数开发。组件相关的命令和用法对于函数 SCF 组件 同样适用。

**下一步：[开始使用 serverless](./quickstart/installation)**
