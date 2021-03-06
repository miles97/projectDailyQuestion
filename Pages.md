## 页面构建指南

1.分页和loadmore

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
  
  15.使用各种工具需要换行或者排版文字格式无果时
  
  例如使用Toast，messageBox时文字的排版问题，没有自带样式，只能通过Js进行操作时；
  ```js
MessageBox.alert(`${'&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'}专业版功能，请联系业务员开通!${'&nbsp;&nbsp;&nbsp;'}
 联系方式:110110110${this.commondCellphone}`)
 ```
通过```&nbsp;```来进行操作，手动居中对齐黑科技。
同理，在其他一些情况下可以用/n等进行文字排版，如echarts的formatter中，需要通过js格式文字。

16.二维码扫描场景

在一般的推广场景中，扫描二维码推广下载应用时，一般来说都是跳转到一个引导页进行判断浏览器环境，如果是微信则引导至浏览器打开链接，跳转至正确的下载链接，如果是浏览器环境，直接打开链接下载。

17.使用注册账号页面的风险控制
对于手机号的风险控制直接从获取二维码阶段便开始。

用户打开注册页便进行服务端通讯，返回扫描工具，时间戳，用户手机,id等等信息，作为日志记录。

18.使用img src进行静态资源请求的拦截
```js
    onloadimg() {
      var newImg = new Image();
      newImg.src = apiConfig.autostreetsImages + this.qrcode;
      console.log(this.$refs.imgChange,newImg,'123123')
      newImg.onerror = () => {
        // 图片加载错误时的替换图片
        Toast("加载失败，请返回重试！");
      };
      newImg.onload = () => {
        // 图片加载成功后把地址给原来的img
        // this.url = newImg.src;
        this.$refs.imgChange.src = newImg.src;//替换加载资源QRcode
        // Toast('加载中')
      };
```
19.使用checklist避免重复bug

20.直接赋值对象的子元素问题
建议直接赋值对象 = {
  item : this.data
}
或者Object.assign(???,item)

21.sessionStorage.setItem('newDate',new Date().getTime())
这种原生方法后不能使用return false 或者return true;

22.需要同一台浏览器环境进行控制时使用sessionStorage进行控制。
判断是重新进入页面还是刷新页面操作。

23.使用web构建原生应用时需要考量的架构问题。

24.使用elementUI做vue的PC后台管理项目

25.filter: grayscale(100%);
直接让页面过滤彩色变成灰色科科
blur：直接让页面失焦，作为过渡动画有很好滴效果
invert(1):反转颜色
brightness(0.5)：调整亮度 智能夜间模式科科
还有一些突出效果，过滤颜色为指定的效果等，都可以用filter实现。

26.生产力优化
实际上可以直接用zencode方法提升页面编码效率，对于一些需要加入特性的标签直接先赋值class,不管用不用先

