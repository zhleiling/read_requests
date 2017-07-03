Requests 源码阅读

# 1 看文档

## 1) 主要接口
7个方法：request  (通用，第一个参数为http方法)

requests.request(method, url, **kwargs)

6个常见http方法：head get post put patch delete 
均返回Response对象

## 2) 异常类
requests.RequestException :模糊异常
requests.ConnectError: 连接错误
requests.HTTPError:Http错误
。。。。

## 3）Request Sessions

class requests.Session
