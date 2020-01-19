## 项目灵感一览

目前来说后端以及原生开发能力并不完善，只能制作一些重前端的内容或者简单结合三方接口的easy应用。不过大抵上仍然不影响创造demo的灵感。

### 原生项目逻辑

首先自然是先使用vue搭建简单的demo框架，等待fultter或者rn称为本人的主技术栈后重构为正式版本，每月进行简单的维护。后端直接使用nodejs或者golang构建。
项目工期预计3个月之内。

### first project [国人自律指南]

通过vue + elementui 构建一个国人适用版本的日历以及行程手账等。

研究整体项目实现逻辑以及简单商用用户交互逻辑和2C||css动画过渡效果

#### 项目进行

1.构建项目的时候可以简单的尝试一下webpack,除非特别拓展需要，否则目前阶段[起手开源项目中]不谈论webpack打包机制等，均使用vue懒人包直接构建项目，专注需求实现等逻辑。

2.搭建项目环境时发现很多配置的问题，需要重新对照package.json以及install以及webpack.base.config.js对照，main.js反而没什么东西

3.一个成熟的需求池应该先对于主要流程以及产品有所理解，暂不为完成某些特定需求服务。

4.手账  天气  以及个人管理方面的使用需要理论支撑，调研相关内容或者应用处理方案。

5.突出UI设计的相关，由于目前不涉及移动端，考虑PC浏览器的友好交互性。

6.使用vuex进行全局的夜间模式切换，发现的mutations由于数据格式不同导致$store.commit('stateFn')无法正常setter,
多层对象或者数据形式使用stateFn，简单的对象直接使用Object.assign.同时如果需要监听,直接在该页面使用
```js
watch:{
'$store.state.stateObject.triggerItem':function(newFlag, oldFlag){
   //handler methods
 } 
},```