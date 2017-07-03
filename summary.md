Requests 源码阅读  
verison: v2.18.1

# 1 看文档

## 1) 主要接口
*request  (通用，第一个参数为http方法)，其他接口方法均通过调用此方法实现
```
requests.request(method, url, **kwargs)
```
*以get为例 
```
def get(url, params=None, **kwargs):
    kwargs.setdefault('allow_redirects', True)
    return request('get', url, params=params, **kwargs)
```
*其他几个 ：options head post put patch delete  
*均返回Response对象

## 2) 异常类
requests.RequestException :模糊异常
requests.ConnectError: 连接错误
requests.HTTPError:Http错误
。。。。

## 3）Request Sessions

class requests.Session
