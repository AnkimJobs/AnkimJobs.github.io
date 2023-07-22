# Vue Router

## 引入Vue Router

```
npm install vue-router
        注意 vue 2 -- vue-router@3
            vue 3 ---vue-router@4
```

## 编码

### router/routes.js

```js
import Home from '@/pages/Home'

/* 
所有静态路由配置的数组
*/
export default [
  {
    path: '/',
    component: Home
  },

]
```
### router/index.js
```js
import Vue from 'vue'
import VueRouter from 'vue-router'
import routes from './routes'

// 声明使用插件
Vue.use(VueRouter)

// 向外默认暴露路由器对象
export default new VueRouter({
  mode: 'history', // 没有#的模式
  routes, // 注册所有路由
})
```
### main.js
```js
import Vue from 'vue'
import App from './App.vue'
import router from './router'

Vue.config.productionTip = false

new Vue({
  render: h => h(App),
  router, // 注册路由器
}).$mount('#app')
```

