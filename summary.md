Requests 源码阅读  
verison: v2.18.1

# 1 看文档

## 1) 主要接口
* request  (通用，第一个参数为http方法)，其他接口方法均通过调用此方法实现
```
requests.request(method, url, **kwargs)
```
* 以get为例 
```
def get(url, params=None, **kwargs):
    kwargs.setdefault('allow_redirects', True)
    return request('get', url, params=params, **kwargs)
```
* 其他几个 ：options head post put patch delete  
* 均返回Response对象

## 2) 异常类
* requests.RequestException :通用异常，继承自IOError， __init__方法中对self.request和self.response赋值。
* requests.ConnectError: 连接错误
* requests.HTTPError:Http错误
* ...

其他异常类均直接或间接继承RequestException，或继承包含RequestException在内的多个类，如：
```
class Timeout(RequestException):
    """The request timed out.

    Catching this error will catch both
    :exc:`~requests.exceptions.ConnectTimeout` and
    :exc:`~requests.exceptions.ReadTimeout` errors.
    """
```
```
class ConnectTimeout(ConnectionError, Timeout):
    """The request timed out while trying to connect to the remote server.

    Requests that produced this error are safe to retry.
    """
```

## 3）Request Sessions

class requests.Session
