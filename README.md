---
title: "Serverless 介绍"
menuText: "Serverless 介绍"
layout: Doc
---

Serverless Framework 是业界非常受欢迎的无服务器应用框架，开发者无需关心底层资源，即可部署完整的 Serverless 应用架构。Serverless Framework 具有资源编排、自动伸缩、事件驱动等能力，覆盖编码、调试、测试、部署等全生命周期，帮助开发者通过联动云资源，迅速构建 Serverless 应用。

Serverless Framework 主要支持以下几个开发场景：

- **基于云函数的命令行开发工具**

  通过 Serverless Framework，开发者可以在命令行完成函数的开发、部署、调试。还可以结合前端服务、 API 网关、数据库等其它云上资源，实现全栈应用的快速部署。

  点击此处[快速开始部署第一个函数应用](./quickstart/function-dev)。

- **传统应用框架的快速迁移**

  Serverless Framework 提供了一套通用的框架迁移方案，通过使用 Serverless Framework 提供的框架组件（Egg/Koa/Express 等），原有应用仅需几行代码简单改造，即可快速迁移到函数平台。同时支持命令行与控制台的开发方式。

  点击此处[快速开始部署第一个框架应用](./quickstart/components-dev)。

### 产品优势

- **简化配置**

  Serverless Framework 提供了丰富的软件应用生态（Component）供您搭建各种形态的 Serverless 应用。您只需几行配置描述，即可进行云函数、API 网关、COS、DB 等 Serverless 资源的快速创建、部署和修改，无需在各个云资源控制台手动开通服务和配置管理，彻底摆脱基础设施的管理和维护，轻松交付 Serverless 应用。

- **方便运维**

  Serverless Framework 支持用户快速部署 Serverless 化的云服务，支持用户按需付费，并能够根据业务请求自动进行弹性伸缩，让您可以从容面对业务请求峰值。您无需再提前手动配置计算资源，无需从零搭建自己的监控告警系统，完全免去传统的运维烦恼，并使得您付出的资源成本相比传统服务可节省超过 80% 。

- **一站式开发**

  Serverless Framework 打造了从初始化、编码、调试、资源配置和部署发布，到业务监控告警、故障排查的一站式解决方案。您可以快速创建 Serverless 应用，并完成应用的调试和部署，监控已发布应用运行状态并快速排障。

**下一步：[下载安装](./quickstart/installation)**

## Components

Serverless Components 是支持多个云资源编排和组织的场景化解决方案，主要基于客户的具体场景，如 Express 框架支持、网站部署等。Serverless Components 可以有效简化云资源的配置和管理，将网关、COS 和 CAM 等产品联动起来，让客户更多关注场景和业务。

详细介绍可以参考 [Github 上的 Serverless Components 项目](https://github.com/serverless/components/blob/master/README.cn.md)。

### Serverless Components 优势

- **简便易用**

Serverless Components 更多的围绕客户场景进行构建，如网站、博客系统、支付服务、图像处理场景等。通过抽象了底层的基础设施配置信息，开发者可以通过十分简单的配置实现场景。

- **可复用性**

Serverless Components 可以通过非常简单的`serverless.yml`创建和部署，但同时也支持用十分简单的语法对 JavaScript 库`serverless.js`进行扩展编写和复用。

- **秒级部署**

大多数 Serverless Components 比传统的配置工具部署快 20 倍左右，Components 可以通过快速的部署和远端验证，有效减少本地模拟和调试的环节。

### Serverless Components 支持列表

当前 Serverless Components 支持丰富的多语言开发框架和应用，具体如下：

**基础组件**：

- [@serverless/tencent-postgresql](https://github.com/serverless-components/tencent-postgresql/tree/master) - 腾讯云 PG DB Serverless 数据库组件
- [@serverless/tencent-apigateway](https://github.com/serverless-components/tencent-apigateway) - 腾讯云 API 网关组件
- [@serverless/tencent-cos](https://github.com/serverless-components/tencent-cos) - 腾讯云对象存储组件
- [@serverless/tencent-scf](https://github.com/serverless-components/tencent-scf/tree/master) - 腾讯云云函数组件
- [@serverless/tencent-cdn](https://github.com/serverless-components/tencent-cdn) - 腾讯云 CDN 组件
- [@serverless/tencent-vpc](https://github.com/serverless-components/tencent-vpc/tree/master) - 腾讯云 VPC 私有网络组件
- [@serverless/tencent-layer](https://github.com/serverless-components/tencent-layer/tree/master) - 腾讯云 Layer 组件

**高阶组件**：

- [@serverless/tencent-nextjs](https://github.com/serverless-components/tencent-nextjs/tree/master) - 快速部署基于 Next.js 框架到腾讯云函数的组件
- [@serverless/tencent-nuxtjs](https://github.com/serverless-components/tencent-nuxtjs/tree/master) - 快速部署基于 Nuxt.js 框架到腾讯云函数的组件
- [@serverless/tencent-express](https://github.com/serverless-components/tencent-express/tree/master) - 快速部署基于 Express.js 的后端服务到腾讯云函数的组件
- [@serverless/tencent-egg](https://github.com/serverless-components/tencent-egg/tree/master) - 快速部署基于 Egg.js 的后端服务到腾讯云函数的组件
- [@serverless/tencent-koa](https://github.com/serverless-components/tencent-koa/tree/master) - 快速部署基于 Koa.js 的后端服务到腾讯云函数的组件
- [@serverless/tencent-flask](https://github.com/serverless-components/tencent-flask) - 腾讯云 Python Flask RESTful API 组件
- [@serverless/tencent-django](https://github.com/serverless-tencent/tencent-django/tree/master) - 腾讯云 Python Django RESTful API 组件
- [@serverless/tencent-laravel](https://github.com/serverless-components/tencent-laravel) - 腾讯云 PHP Laravel RESTful API 组件
- [@serverless/tencent-thinkphp](https://github.com/serverless-components/tencent-thinkphp) - 腾讯云 ThinkPHP RESTful API 组件
- [@serverless/tencent-website](https://github.com/serverless-components/tencent-website/tree/master) - 快速部署静态网站到腾讯云的组件

此外，所有的 Serverless Components 均可在 [Github 仓库](https://github.com/serverless-components?q=tencent) 中查看，查看时请注意切换至最新的**v2**版本。
