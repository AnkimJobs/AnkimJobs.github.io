# 搭建项目
## 使用Vue CLI 3(脚手架)搭建项目

1. Vue CLI是Vue官方提供的用于搭建基于Vue+Webpack+ES6项目的脚手架工具
2. 在线文档: <https://cli.vuejs.org/zh/>
3. 操作:
``` shell
# 使用vue-cli3
npm install -g @vue/cli
vue create shop-client
cd shop-client
npm run serve
```

``` shell
# 降级到vue-cli2
npm install -g @vue/cli-init
vue init webpack gshop-client2
cd shop-client
npm run serve
```
##  编码测试与打包发布项目

1. 编码测试

```shell
npm run serve  
编码, 自动编译打包(HMR), 查看效果
```

2. 打包发布

```shell
npm run build
npm install -g serve
serve dist -p 5000
访问: http://localhost:5000
```

## 其他配置

创建脚手架项目指令：vue create 项目名字【都是英文的】

node_modules:项目依赖的地方
public:放置静态资源地方【静态页面】,public文件夹里面静态资源，原封不动打包到dist里面。
src:程序员源代码区域
        assets文件夹:也是放置静态资源的地方,webpack打包的时候，这里面的静态资源会当作webpack模块，打包js文件里面。最后看不见了。
        vue.config.js:配置代理跨域。
```js
        const { defineConfig } = require('@vue/cli-service')
        module.exports = defineConfig({
        transpileDependencies: true,
        //让浏览器自动打开
         devServer:{
        //设置本地服务器打开的域名
        host:'127.0.0.1',
        //设置本地服务器打开端口号
        port:8080,
        }
        })
```        
package.json文件  
```json
 "scripts": {
    "serve": "vue-cli-service serve --open",
    "build": "vue-cli-service build",
    "lint": "vue-cli-service lint"
}
```