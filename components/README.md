---
title: "组件开发(component)指南"
menuText: "组件开发(component)指南"
layout: Doc
---

## 概述

Serverless 组件(components)使开发人员能够更轻松地部署 Serverless 应用程序和用例，同时通过组件自定义的环境可以将传统应用(Express, Next.js, Laraval)使用 Serverless Framewok 部署并获得 Serverless 的所有优势。

- 轻松上手：通过组件部署整个无服务器应用程序/用例，而无需成为云专家。
- 即时部署：组件部署在约 8 秒钟内完成，从而可以在云上进行快速开发。
- 流式日志：组件可以实时将应用日志从输出到控制台，以进行快速调试。
- 自动统计：许多组件在部署时会自动设置度量标准，方便统计分析。
- 自定义组件：你可以轻松构建自己组件。
- 注册中心：通过 Serverless 注册中心，你可以与你的团队和整个世界共享你的组件。

> 关于组件更详细的说明请查看[Serverless 组件说明文档](https://github.com/serverless/components/blob/master/README.cn.md#%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B)。

## 官方组件

目前 Serverless 腾讯提供了以下官方组件模板供广大开发者使用：

- 静态网站([static-website](https://github.com/serverless-components/tencent-examples/tree/master/website-starter)): 静态 HTML 网站项目
- React 站点([react-starter](https://github.com/serverless-components/tencent-examples/tree/master/react-starter)): React + Parcel 静态页面模板
- Vue 站点([vue-starter](https://github.com/serverless-components/tencent-examples/tree/master/vue-starter)): @vue/cli 初始化的静态页面模板
- Next.js 站点([nextjs-starter](https://github.com/serverless-components/tencent-examples/tree/master/nextjs-starter)): Next.js 开发模板
- Nuxt.js 站点([nuxtjs-starter](https://github.com/serverless-components/tencent-examples/tree/master/nuxtjs-starter)): Nuxt.js 开发模板

- Express 应用([express-starter](https://github.com/serverless-components/tencent-examples/tree/master/express-starter)): Express 框架模板(Node.js)
- Koa 应用([koa-starter](https://github.com/serverless-components/tencent-examples/tree/master/koa-starter)): Koa 框架模板(Node.js)
- Egg.js 应用([eggjs-starter](https://github.com/serverless-components/tencent-examples/tree/master/eggjs-starter)): Eggjs 框架模板(Node.js)
- Restful API 应用([restful-api](https://github.com/serverless-components/tencent-examples/tree/master/restful-api)): Python + API gateway 模板。
- Flask 应用([flask-starter](https://github.com/serverless-components/tencent-examples/tree/master/flask-starter)): Flask 框架模板(Python)
- Laravel 应用([laravel-starter](https://github.com/serverless-components/tencent-examples/tree/master/laravel-starter)): Laravle 框架模板(PHP)
- 全栈应用([fullstack](https://github.com/serverless-components/tencent-examples/tree/master/fullstack)): vue.js + express + postgres 应用模板

<!-- - Django 应用([django-starter](https://github.com/serverless-components/tencent-django)): Django 框架模板(Python) -->

> 不同的组件的配置方式不完全相同，使用前请查看组件的配置实例进行确认。

**下一步：开始组件开发**

- [组件 CLI 命令](./components-commands)
- [前端组件应用开发](./frontend)
- [后端组件应用开发](./backend)
- [全栈应用开发](./fullstack)
- [其他应用开发](./other)
