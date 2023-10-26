axios个人常用整理

github地址：

[axios/axios: Promise based HTTP client for the browser and node.js (github.com)](https://github.com/axios/axios)

## axios安装导入

```bash
# 安装
npm install axios --save
# 导入
import axios from 'axios'
```

## 全局方式（项目中不会这么使用，后面会自行封装）

axios本身返回promise。

### 1.基本使用

```javascript
axios({
  url: 'http://127.0.0.1:8000/xxx',
  method: 'get',
  params: {
    page: 1
  }
}).then(res => {
  console.log(res)
}).catch(err => {
  console.log(err)
})
```

### 2.并发请求

```javascript
axios.all([
  //请求1
  axios({
    url: "http://127.0.0.1:8000/xxx"
  }),
  //请求2
  axios({
    url: "http://127.0.0.1:8000/yyy",
    method: "post",
    data: {
      userName: 'zhangshan'
    }
  }),
]).then(res => {
  //两次请求都完成
  console.log(res[0])
  console.log(res[1])
})
```

### 3.全局的配置

```javascript
比如：
axios.defaults.baseURL = 'http://127.0.0.1:8000'
axios.defaults.timeOut = 5000
```

但是项目中有时不可能只有一个baseURL或者其他配置不相同，这时候我们就需要实例化axios

## 实例化方式（项目中也不会这么使用，后面会自行封装）

```javascript
//实例化axios
const sl1 = axios.create({
  //全局配置
  baseURL="http://127.0.0.1:8000",
  timeOut: 5000
})
//发送请求
sl1({
  url: "/xxx"
}).then(res => {
  console.log(res)
})
```

## 拦截器

```javascript
请求拦截：
axios.interceptors.requset.use(
  (config) => {
    //请求拦截，config就是axios(config)中的config
    console.log(config)
    //拦截后进行操作完需要  返回config
    return config
  },
  (err) => {
    console.log(err)
  }
)

响应拦截：
axios.interceptors.response.use(
  (res) => {
    //响应结果res
    console.log(res)
    //拦截后进行操作完需要  返回res（真正需要的是res.data中的数据）
    return res.data
  },
  (err) => {
    console.log(err)
  }
)
```

## axios封装（常用）

每个人封装不同，一下为本人常用封装

封装request.js

```javascript
import axios from "axios"

export function request(option){
  // 1.实例化axios
  const sl1 = axios.create({
    baseURL: "http://127.0.0.1:8000",
    timeOut: 5000
  })
  // 2.拦截器
  /**
   * 为什么拦截？
   * 1.比如config中的一些信息不符合服务器要求
   * 2.每次发送网络请求时，界面显示一个加载图标
   * 3.某些网络请求（比如登录时需要token），必须携带一些特殊信息
   * 
   */
  // 请求拦截
  sl1.interceptors.request.use(
    (config) => {
      //请求拦截，config就是axios(config)中的config
      console.log(config)
      //拦截后进行操作完需要  返回config
      return config
    },
    (err) => {
      console.log(err)
    }
  )
  //响应拦截
  sl1.interceptors.response.use(
    (res) => {
      //响应结果res
      console.log(res)
      //拦截后进行操作完需要  返回res（真正需要的是res.data中的数据）
      return res.data
    },
    (err) => {
      console.log(err)
    }
  )
  //3.发送请求
  return sl1(option)
}
```
