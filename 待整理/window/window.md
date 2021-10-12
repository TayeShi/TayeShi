# window

## window.location 浏览器定位和导航

window.location 其实指向的就是一个Location对象

### 理解

location即一个位置信息，那么浏览器的Location，则是当前在万维网中的哪里。位置信息，即哪个协议哪个服务器哪个端口哪个目录哪个文件。

### 常用

#### 1. 解析URL

访问页面：https://mall.jd.com/index-1000004123.html?from=pc

![image-20211013005619932](https://cdn.jsdelivr.net/gh/TayeShi/Twinkle/assets/img/image-20211013005619932.png)

可以获得各个部分，包括：

- href 整个链接
- protocol 协议
- host 
- hostname
- port
- pathname
- search ?后面的参数

通过search就可以获得URL中的参数，以下是一个简单的解析参数的方法

```javascript
/**
 * 通过window.location.search获取请求参数
 */
function urlArgs() {
  let search = window.location.search
  let searchArr = window.location.search.substring(1).split('&')
  let args = {}
  searchArr.forEach(item => {
    let index = item.indexOf('=')
    if (index == -1) return
    let name = item.substring(0, index)
    let value = item.substring(index+1)
    args[name] = value
  })
  return args
}
```

#### 2. 载入新的文档

载入新文档有两种方式：

- Location.assign(url) 跳转后可以返回，可以返回上个路由。
- Location.replace(url) 删除当前的URL，跳转到新的URL。如replace，会替换掉当前的url，但是可以返回上上个路由

也可以通过修改window.location的值来直接进行页面跳转（可返回的），如：

```javascript
// 当前路径 https://search.jd.com/search?keyword=%E5%B0%8F%E7%B1%B3&wq=%E5%B0%8F%E7%B1%B3&ev=559_66902%5E
window.location = 'https://www.baidu.com' // 跳转到百度
window.location = '/search?keyword=小米&wq=小米&ev=559_66902%5Eexbrand_黑鲨%5E' // 跳转到https://search.jd.com/search?keyword=%E5%B0%8F%E7%B1%B3&wq=%E5%B0%8F%E7%B1%B3&ev=559_66902%5Eexbrand_%E9%BB%91%E9%B2%A8%5E
window.location = '#xxx' // 跳转到指定锚点
window.location.search = '?xxx=aaa&zzz=bbb' // 更改search的值
```

#### 3. 浏览历史

通过window.history就可以访问当前窗口的浏览历史

但是由于安全，window.history只能访问到当前路由的length长度

使用以下方法进行路由跳转：

- history.back() 返回上个路由
- history.forward() 前进到下个路由
- history.go(num) 如果为1是跳转到下个路由，-2是返回到上上个路由

