---
title: "统计分析"
menuText: "统计分析"
layout: Doc
---

<!-- TODO: 更新 腾讯统计分析 说明 -->

<!-- Upadate 0430: 此处并无通用统计分析能力，仅针对express、nextjs、nuxtjs 三个组件框架进行了简单自定义监控上报，也只是控制台简单展示 -->

针对 Express、Next.js、Nuxt.js 三个框架，Serverless Framework 组件支持自定义监控数据的采集和上报。通过[腾讯云应用控制台](https://console.cloud.tencent.com/sls) 的【应用监控】页面，您可以查看项目部署后输出的基本信息、项目请求次数、项目报错统计等多项监控指标，方便您轻松实现项目的管理运维。

<img src="https://img.serverlesscloud.cn/20201126/1606384460049-%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202020-11-26%2016.22.43.png" width="770px">

支持统计的指标如下：

- 函数触发次数/错误次数：function invocations & errors
- 函数延迟：function latency
- API 请求次数/错误次数：api requests & errors
- API 请求延迟：api latency
- API 5xx 错误次数：api 5xx errors
- API 4xx 错误次数：api 4xx errors
- API 错误次数统计：api errors
- 不同路径下 API 的请求方法、请求次数和平均延迟统计：api path requests
