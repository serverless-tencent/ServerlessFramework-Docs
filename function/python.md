---
title: "Python 函数应用开发"
menuText: "Python 函数应用开发"
layout: Doc
---

目前支持的 Python 开发语言包括如下版本：

Python 2.7
Python 3.6

## 定义函数

Python 环境下的入参包括 event 和 context，两者均为 Python dict 类型。

event：使用此参数传递触发事件数据。
context：使用此参数向您的处理程序传递运行时信息。

```py
import json

def main_handler(event, context):
    print("Received event: " + json.dumps(event, indent = 2))
    print("Received context: " + str(context))
    return("Hello World")
```

### 返回和异常

您的处理程序可以使用 return 来返回值，根据调用函数时的调用类型不同，返回值会有不同的处理方式。

同步调用：使用同步调用时，返回值会序列化后以 JSON 的格式返回给调用方，调用方可以获取返回值已进行后续处理。例如通过控制台进行的函数调试的调用方法就是同步调用，能够在调用完成后捕捉到函数返回值并显示。
异步调用：异步调用时，由于调用方法仅触发函数就返回，不会等待函数完成执行，因此函数返回值会被丢弃。
同时，无论同步调用还是异步调用，返回值均会在函数日志中 ret_msg 位置显示。

您可以在函数内使用 raise Exception 的方式抛出异常。抛出的异常会在函数运行环境中被捕捉到并在日志中以 Traceback 的形式展示。

## 日志

您可以在程序中使用 print 或使用 logging 模块来完成日志输出。例如，如下函数：

```py
import logging
logger = logging.getLogger()
logger.setLevel(logging.INFO)
def main_handler(event, context):
    logger.info('got event{}'.format(event))
    print("got event{}".format(event))
    return 'Hello World!'
```

输出内容您可以在函数日志中的 log 位置查看。

## 依赖库

### 使用内建库

目前包含的库如下:
| 库名称 | Python 3 版本 | Python 2 版本 |
| :--- | :----: | :---: |
| absl-py | 0.2.2 | 0.2.2 |
| asn1crypto | 0.24.0 | 0.24.0 |
| astor | 0.7.1 | 0.7.1 |
| backports.ssl-match-hostname | - | 3.4.0.2 |
| backports.weakref | - | 1.0.post1 |
| bleach | 1.5.0 | 1.5.0 |
| cassdk | - | 1.0.2 |
| certifi | 2019.3.9 | 2017.11.5 |
| cffi | 1.12.2 | 1.12.2 |
| chardet | 3.0.4 | 3.0.4 |
| cos-python-sdk-v5 | 1.6.6 | 1.6.6 |
| cryptography | 2.6.1 | 2.6.1 |
| dicttoxml | 1.7.4 | 1.7.4 |
| enum34 | - | 1.1.6 |
| funcsigs | - | 1.0.2 |
| futures | - | 3.2.0 |
| gast | 0.2.0 | 0.2.0 |
| grpcio | 1.13.0 | 1.13.0 |
| html5lib | 0.9999999 | 0.9999999 |
| idna | 2.8 | 2.6 |
| iniparse | 0.4 | 0.4 |
| iniparse | - | 1.0.22 |
| Markdown | - | 2.6.11 |
| mock | - | 2.0.0 |
| mysqlclient | 1.3.13 | 1.3.13 |
| nose | - | 1.3.7 |
| numpy | 1.15.0 | 1.14.5 |
| ordereddict | - | 1.1 |
| pbr | - | 4.1.0 |
| Pillow | 6.0.0 | 6.0.0 |
| pip | 9.0.1 | 18 |
| protobuf | 3.6.0 | 3.6.0 |
| psycopg2-binary | 2.8.2 | 2.8.2 |
| pyaml | - | 2019.4.1 |
| pycparser | 2.19 | 2.19 |
| pycurl | 7.43.0 | 7.43.0.1 |
| pygpgme | - | 0.3 |
| PyMySQL | 0.9.3 | 0.9.3 |
| pytz | 2019.1 | 2019.1 |
| PyYAML | - | 5.1 |
| qcloud-image | 1.0.0 | 1.0.0 |
| qcloudsms-py | 0.1.3 | 0.1.3 |
| requests | 2.21.0 | 2.18.4 |
| serverless-db-sdk | 0.0.1 | 0.0.1 |
| setuptools | 28.8.0 | 39.1.0 |
| six | 1.12.0 | 1.11.0 |
| tencentcloud-sdk-python | 3.0.65 | 3.0.65 |
| tencentserverless | 0.1.4 | 0.1.4 |
| tensorboard | 1.9.0 | 1.9.0 |
| tensorflow | 1.9.0 | 1.9.0 |
| tensorflow-serving-api | 1.9.0 | 1.9.0 |
| termcolor | 1.1.0 | 1.1.0 |
| urlgrabber | - | 3.10.2 |
| urllib3 | 1.24.2 | 1.22 |
| Werkzeug | 0.14.1 | 0.14.1 |
| wheel | 0.31.1 | 0.31.1 |
