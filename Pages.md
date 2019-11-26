## 页面构建指南

1. 分页和loadmore

使用fixed-bottom时候，考虑iphonex兼容性问题，按照主流处理方案，采用touchbar附近的内容填充，撑起按钮高度处理。其他设备不做处理

2.分类导航以及正确问题描述

3.社区贡献指南

4.react-native start-up

5.使用vue进行keepalive时，需要注意滚动位置

6.构建组件时，如果组件的某些值需要重置，并且不能使用emit回调该参数或者包含赋值该字段的值

7.页面路由保护逻辑，进入不同的页面时候本页面是应该销毁或者保留，
在相应的to.path以及from.path的路由地址进行定义，判断keepalive条件销毁。

8.编写文档以及整理项目代码时的规范
* 使用//备注需要重构或者修复的bug
* 使用规范的共用方法声明方法使用，以及参数的数据格式
* 将代码模块化，并通过数组规范将可以优化算法的代码重构

[数组的优化](https://mp.weixin.qq.com/s/RXT2bsm2EglOoLSXC8zRNw)

9. 弱网情况下的接口请求顺序以及生命周期钩子的顺序

10. 当路由改成为alive时需要注意的各种问题！

11. 组件的编写时注意  编辑页面时带进来的值需要在组件内定位

12. 组件的初始化清空问题

13. 字符串IOS端的处理可能导致接口编辑时将Null处理为'null'或者<null>等等情况，使用一个统一的检测为空方法
  ```js
isEmpty(){
    if (typeof obj == "undefined" || obj == null || obj == "" || obj == "null" || obj == "<null>" || obj == "undefined") {
      return true;
   } else {
      return false;
     }  
  }
  ```
  然后再根据需求统一赋值成空字符串或者其他
  ```js
  if(argument){
  self.saveInfo[saveInfoItem] = clueInfo[saveInfoItem] || '';
      } 
  
  ```
  
  14. vue项目起步脚手架懒人版
  actually经常会用到只有一个页面构建的H5,出于性能考量，引入资源越少越好。
  而大型的SPA项目脚手架拓展性等应更强。
