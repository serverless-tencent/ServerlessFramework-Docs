---
title: "Serverless Framework 介绍"
menuText: "Serverless Framework 介绍"
layout: Doc
---

Serverless Framework 是业界非常受欢迎的无服务器应用框架，通过与众多一流云供应商如腾讯云，AWS 等的紧密合作，为广大开发者提供无需关心底层基础设施，即可编写和部署代码的无服务开发体验。

Serverless Framework 同时提供资源管理、自动伸缩、统计分析等能力，让广大开发者可以节省运维成本，真正做到“按量付费”的同时，也无需花费精力处理日志收集，异常统计等任务。

Serverless Framework 通过 CLI 工具与腾讯云紧密合作，为中国用户提供了基于组件(serverless components)的完整解决方案。覆盖了无服务应用编码、测试、部署，等全生命周期，同时更符合中国用户的使用场景和习惯。

## 开始使用

通过 Serverless CLI 工具可以创建，调试，部署，查看，移除 serverless 应用，马上[安装 Serverless CLI](./quickstart/installation.md) 并使用。

### 函数应用开发

Serverless 为函数应用开发者提供了一个统一的开发框架，通过 serverelss 开发者可以快速开发，调试，部署。结合静态站点，API 网关，数据库等其他云上资源，函数应用拥有更强大的能力和使用场景。

开始 [使用 serverless 开发函数应用](./quickstart/function-dev.md)

### 组件应用开发

Serveless 为使用传统框架(如：Nextjs, Express, Django 等)开发的应用提供了运行环境支持，通过 serverless 开发者可以继续使用传统框架开发应用，也可以通过简单改造将原有应用迁移到 serverless 平台。

开始 [使用 serverless 开发传统应用](./quickstart/components-dev.md)

### SaaS 应用托管

Serverless 为使用 SaaS 应用(如：Wordpress 等)提供了方便的运行环境支持，通过 serverless 简单配置就可以部署并开始使用 SaaS 应用，也无需担心应用的后续维护和升级。

<!-- TODO: 更新产品优势 @Oliver
## 独特优势

### （开发流程）事件机制
  * 。。。
  * 。。。
Serverless Framework 打造了从初始化、编码、调试、资源配置和部署发布，到业务监控告警、故障排查的一站式解决方案 (一个产品覆盖开发过程各个方面，避免切换)

* 通过yml完成全部配置，使用简单。
Serverless Framework 提供了丰富的软件应用生态（Component）供您搭建各种形态的 Serverless 应用。您只需几行配置描述，即可进行云函数、API 网关、COS、DB 等 Serverless 资源的快速创建、部署和修改，无需在各个云资源控制台手动开通服务和配置管理，彻底摆脱基础设施的管理和维护，轻松交付 Serverless 应用。


### （运维）弹性伸缩 0运维 高可用
  * 。。。
  * 。。。
Serverless Framework 支持用户快速部署 Serverless 化的云服务，支持用户按需付费，并能够根据业务请求自动进行弹性伸缩，让您可以从容面对业务请求峰值。您无需再提前手动配置计算资源，无需从零搭建自己的监控告警系统，完全免去传统的运维烦恼，并使得您付出的资源成本相比传统服务可节省超过 80% 。

大多数 Serverless Components 比传统的配置工具部署快 20 倍左右，Components 可以通过快速的部署和远端验证，有效减少本地模拟和调试的环节。

### （成本）按量付费 监控警告
  * 。。。

-->

## 概念区分

### Serverless Framework

### Serverless Traditional

Serverless Traditional 是独立于云平台的函数应用开发框架，同时支持事件触发，弹性扩容，并且按需付费。从而大大降低构建和维护应用的开销，供开发者专注业务逻辑。

详细介绍可以参考 [Github 上的 Serverless 项目](https://github.com/serverless/serverless/blob/master/README_CN.md)。

### Serverless Components

Serverless Components 通过定制的基础设施支持更多开发场景，如 Express, Next.js, Wordpress 等。同时具有 serverless 的弹性扩缩容，按量付费等优势。让开发者在不改变代码和开发习惯的情况下获得 serverless 的强大优势。

详细介绍可以参考 [Github 上的 Serverless Components 项目](https://github.com/serverless/components/blob/master/README.cn.md)。

**下一步：[开始使用 serverless](./quickstart/installation)**
