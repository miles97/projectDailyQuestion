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