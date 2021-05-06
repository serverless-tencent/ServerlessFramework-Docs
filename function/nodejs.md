---
title: "Node.js 函数应用开发"
menuText: "Node.js 函数应用开发"
layout: Doc
---

目前 腾讯 SCF 对于支持的 Node.js 运行时有

- Node.js 10.15
- Node.js 12.16

## 定义函数

腾讯 SCF 函数的参数说明：

- event：使用此参数传递触发事件数据。
- context：使用此参数向您的处理程序传递运行时信息。
- callback（可选）：使用此参数用于将您所希望的信息返回给调用方。使用 async 描述的入口函数，需要使用 return 关键字返回，非 async 模式的入口函数，需要使用 callback 入参返回。

```js
// callback 方式定义函数
module.exports = (event, context, callback) => {
  console.log(event);
  callback(null, { code: 0 });
};

// async 方式定义
module.exports = async (event, context) => {
  console.log(event);
  return { code: 0 };
};
```

### 返回和异常

您的处理程序可以使用 callback 入参，或代码中的 return 关键字来返回信息。使用 callback 或 return 进行返回的支持情况如下

callback 方式的回掉参数说明

```js
callback(error, result);
```

- error：【可选】函数执行失败时使用此参数返回错误。成功情况下反回 null。
- result：【可选】函数执行成功的结果信息。参数需兼容 JSON.stringify 以便序列化为 JSON 格式。

如果使用 return 关键字进行返回，可直接使用 return object 来返回一个对象或值。
如果在代码中未调用 callback 或 return，云函数后台将会隐式调用，并且返回 null。

根据调用函数时的调用类型不同，返回值会有不同的处理方式。同步调用的返回值将会序列化为 JSON 格式后返回给调用方，异步调用的返回值将会被抛弃。同时，无论同步调用还是异步调用，返回值均会在函数日志中 ret_msg 位置显示。

### 关闭事件循环等待

由于部分外部引入的库的原因，可能会导致事件循环持续不为空。这种情况将会在某些条件下导致函数无法返回直至超时。为了避免外部库的影响，可以通过关闭事件循环等待来自行控制函数的返回时机。通过如下方式，可以修改默认的回调行为，避免等待事件循环为空。

设置 `context.callbackWaitsForEmptyEventLoop` 为 false。
通过在 callback 回调执行前设置 `context.callbackWaitsForEmptyEventLoop = false`; ，可以使云函数后台在 callback 回调被调用后立刻冻结进程，不再等待事件循环内的事件，而在同步过程完成后立刻返回。

## 日志

您可以在程序中使用如下语句来完成日志输出：

```js
console.log(...);
console.error(...);
console.warn(...);
console.info(...);
```

## 依赖库

### 使用内建的工具库

Serverless 腾讯内置了许多常用工具库，方便开发者在函数开发过程中使用，具体使用方法如下。

```js
const COS = require("cos-nodejs-sdk-v5");
```

目前包含的库如下:
| 库名称 | Node.js 12 版本 | Node.js 10 版本 |
| :--- | :----: | :---: |
| [cos-nodejs-sdk-v5](https://github.com/tencentyun/cos-nodejs-sdk-v5) | 2.5.20 | 2.5.14 |
| [base64-js](https://github.com/beatgammit/base64-js) | 1.3.1 | 1.3.1 |
| [buffer](https://github.com/feross/buffer) | 5.5.0 | 5.4.3 |
| [crypto-browserify](https://github.com/crypto-browserify/crypto-browserify) | 3.12.0 | 3.12.0 |
| [ieee754](https://github.com/feross/ieee754) | 1.1.13 | 1.1.13 |
| [imagemagick](https://github.com/rsms/node-imagemagick) | 0.1.3 | 0.1.3 |
| [isarray](https://github.com/juliangruber/isarray) | 2.0.5 | 2.0.5 |
| [jmespath](https://github.com/jmespath/jmespath.js) | 0.15.0 | 0.15.0 |
| [lodash](https://github.com/lodash/lodash) | 4.17.15 | 4.17.15 |
| [microtime](https://github.com/wadey/node-microtime) | 3.0.0 | 3.0.0 |
| [npm](https://github.com/npm/cli) | 6.13.4 | 6.4.1 |
| [punycode](https://github.com/bestiejs/punycode.js) | 2.1.1 | 2.1.1 |
| [puppeteer](https://github.com/puppeteer/puppeteer) | 2.1.1 | 2.0.0 |
| [qcloudapi-sdk](https://www.npmjs.com/package/qcloudapi-sdk) | 0.2.1 | 0.2.1 |
| [querystring](https://github.com/Gozala/querystring) | 0.2.0 | 0.2.0 |
| [request](https://github.com/request/request) | 2.88.2 | 2.88.0 |
| [sax](https://github.com/isaacs/sax-js) | 1.2.4 | 1.2.4 |
| [scf-nodejs-serverlessdb-sdk](https://github.com/tencentyun/scf-serverlessdb-sdk-nodejs) | 1.1.0 | 1.0.1 |
| [tencentcloud-sdk-nodejs](https://github.com/tencentcloud/tencentcloud-sdk-nodejs) | 3.0.147 | 3.0.104 |
| [url](https://github.com/defunctzombie/node-url) | 0.11.0 | 0.11.0 |
| [uuid](https://github.com/uuidjs/uuid) | 7.0.3 | 3.3.3 |
| [xml2js](https://github.com/Leonidas-from-XIV/node-xml2js) | 0.4.23 | 0.4.22 |
| [xmlbuilder](https://github.com/oozcitak/xmlbuilder-js) | 15.1.0 | 13.0.2 |

### 使用自定义工具

Serverless Framework 函数组件支持使用`package.json`中的依赖库，会在完成部署后自动安装跟目录`package.json`中的依赖文件。
