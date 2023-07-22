# Ajax 前后台交互
## 1. 下载依赖包
```
npm install axios nprogress
```

## 2. 封装ajax请求模块

1. api/ajax.js

```js
/* 
对axios进行二次包装
1. 配置通用的基础路径和超时时间
2. 显示请求进度条
3. 成功返回的数据不再是response, 而直接是响应体数据response.data
4. 统一处理请求错误, 具体请求也可以选择处理或不处理
*/
import axios from 'axios'
import NProgress from 'nprogress'
import 'nprogress/nprogress.css'

// 配置不显示右上角的旋转进度条, 只显示水平进度条
NProgress.configure({ showSpinner: false }) 

//可以到 GitHub上面的 axios 官网去找用法   
const service = axios.create({
  baseURL: "/api", // 基础路径
  timeout: 15000   // 连接请求超时时间
})

service.interceptors.request.use((config) => {
  // 显示请求中的水平进度条
  NProgress.start()

  // 必须返回配置对象
  return config
})

service.interceptors.response.use((response) => {
  // 隐藏进度条
  NProgress.done()
  // 返回响应体数据
  return response.data
}, (error) => {
  // 隐藏进度条
  NProgress.done()

  // 统一处理一下错误
  alert( `请求出错: ${error.message||'未知错误'}`)

  // 后面可以选择不处理或处理
  return Promise.reject(error)
})

export default service
```

1. api/index.js

```js
/* 
包含所有接口请求函数的模块
*/
import ajax from './ajax'

//获取商品的三级分类列表
export const reqBaseCategoryList = ()=>ajax.get('/product/getBaseCategoryList')
```



## 12.3. App.vue

```js
import {reqBaseCategoryList} from '@/api'

async mounted () {
    const result = await reqBaseCategoryList()
    console.log('result', result)
},
```



## 12.4. 配置代理

- vue.config.js    //在这个文件里面配置

```js
//跨域的问题  如何处理跨域 跨域的三种方式
//跨域问题常见的错误 'Access-Control-Allow-Origin
//加到module.exports = {}中
devServer: {  //只用于开发环境
  proxy: {
    '/api': { // 只对请求路由以/api开头的请求进行代理转发
      target: 'http://182.92.128.115', // 转发的目标url
      changeOrigin: true // 支持跨域
       // pathRewrite: {‘^/api’: ‘’} //后台接口有api
    }
  }
},

//本地也需要改  改变出发地址？？
//   //baseURL:'http://39.98.123.211:8510/api',
//     baseURL:'/api', //用代理。
//实际发的网络要求 
// Request URL: http://localhost:8080/api/product/getBaseCategoryList



