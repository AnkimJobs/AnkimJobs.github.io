# 搭建项目
## 使用Vue CLI 3(脚手架)搭建项目

1. Vue CLI是Vue官方提供的用于搭建基于Vue+Webpack+ES6项目的脚手架工具
2. 在线文档: https://cli.vuejs.org/zh/
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
## 1.3. 编码测试与打包发布项目

1. 编码测试

```shell
npm run serve  
访问: http://localhost:8080
编码, 自动编译打包(HMR), 查看效果
```

2. 打包发布

```shell
npm run build
npm install -g serve
serve dist -p 5000
访问: [http://localhost:5000](http://localhost:5000)