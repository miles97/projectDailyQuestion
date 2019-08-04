## end game

1.关于项目中使用缺少代码评审的规范性问题

2.IOS13体验版不适合开发测试，同时除了好用的音量icon变化，其他的软件适配不怎么样，甚至强烈影响了软件使用体验.使用体验最好的还是faceID解锁的速度，不过还是觉得十分闹心，关于电池的机器学习充电习惯等等，偶尔还是不能接受，觉得4个小时没充满电量的心情难以平和

3.关于是否动态渲染的问题，很多时候对于接口的渲染有一定的要求，还是不能直接无脑`v-for`，同样也许要看对应的要求。然后关于:key的问题，除了不适用index。其他的便是与后台朋友沟通，希望在接口内加上相应指标的唯一参数，前端做一些内容比较麻烦

4.关于经常性的视图不刷新问题,很多时候vue视图不会更新，使用watch也不能使得监听更新视图
(vuejs数组渲染的问题)[https://v1-cn.vuejs.org/guide/list.html]
```
因为 JavaScript 的限制，Vue.js 不能检测到下面数组变化：
直接用索引设置元素，如 vm.items[0] = {}；
修改数据的长度，如 vm.items.length = 0。
```
所以只能使用this.$set(arr,index,!arr[index])方法来检测更新

5.关于echarts全屏的问题，新建页面，然后setlocalstorage,getLocalstorage.
横屏全屏的解决方案有
```java
      tooltip: {
          trigger: 'axis',
          extraCssText: 'transform: rotate(90deg)'
      },
      xAxis: {
          type: 'value',
          axisLine: {lineStyle: {color: '#ccc'}},
          axisTick: {show: false},
          nameRotate: -90,
          axisLabel: {
              rotate: 90
          },
          position: 'top',
          scale: true,

      },
      yAxis: {
          type: 'category',
          boundaryGap: false,
          axisLine: {lineStyle: {color: '#ccc'}},
          axisTick: {
              interval: 5,
          },
          inverse: true,
          axisLabel: {
              rotate: -90,
              margin: 15,
              interval: 1,
          },
      },
```
以及dataset里面的encode，可以直接将y轴和x轴映射，tooltips翻转，效果一致。

6.关于拿到字符串里面的数值问题  
let o='第29周' ;let num = o.split('')[1] + o.split("")[2];
如果想要数字格式的，let num = Number(num)

7.关于周数的问题
要对于一个区间的周，年进行往前推到12周，实现是关于echarts的问题，

参数只有year:2019,weekOfYear:24;
如何判断年和周。。。。
当weekofyear<12的时候，接口请求判断year-1的周数，然后 
currentWeekOfYear = weekOfyear + cureentweek -12

关于日期和月就很简单，直接将new Date().getTime(24 * 60 * 60 * 1000)  就是一天的时间，然后fotmattingstring，取值


8. 关于对数据的控制问题

接口返回很多二维数组，开发需要控制每一个Item单独的选中状态。

index === acitveIndex? 'avtive-css':''

9. 在渲染文件中同一个button控制的问题

通过不同状态的判断进入两个不同的执行函数或者直接if判断 Flag的true/false

10. 监听问题，如果遇到组件的数值value变了，但是activeText没变的情况，在组件内部添加监听valueChange的事件，然后动态赋值activeText
**在页面内监听无用
```javascript
  watch:{
      //监听startValue变化更改avtiveText对应的值
      startValue: {
          handler(newValue, oldValue) {
              this.activeText = newValue
          }
      },
      //以上同理
      endValue:{
          handler(newvalue,oldvalue){
              this.activeText2=newvalue
          }
      }
  }
```

11. dataset的删除数据集和增加操作 tooptips的显示问题

目前的操作是通过for...in循环删除每个i中的index的数值，替换成NaN,不过具体的实现还没找到，这样而且有问题，如果替换成NULL或者undefined会引起一些报错的问题，如果直接删除tooltips仍然还是有显示到问题。

解决方案：使用series:this.series赋值，然后通过同步的splice series数组，引起整个option数值的更改。完成tooltips的更新。

12.优化样式问题

对于既定的样式问题的再次修改，以及样式的覆盖问题。

13.使用mac进行开发的问题
首先就是package.json的问题，很多依赖并不能直接从windows环境过来，所以配置文件仍然需要修改一些内容，然后即使npm的速度以及效率问题
切换到yarn进行安装之后好了很多

不过yarn的一些东西仍然不习惯，还是避免不了npm的日常使用

14.深拷贝问题，当我使用splice操作数组的时候，发现concat(),或者是[...Array]都不能深拷贝一个对象或是对数组影响并不能杜绝，具体的问题还未知出现在什么地方

15.react-native环境安装
Node ， JDK ， python2 , Android Studio , yarn
[RN环境搭建](https://reactnative.cn/docs/getting-started.html)
```javascript
react-native run-android
```
以上需要依赖代理

16.关于对于影响数组方法的构建
??? [...[]],concat()

17.关于隐式类型转换的问题，==

18.rn原生环境以及Mac OS的配置

19.webstrom自动格式化的问题，实践发现webstorm会自动格式化空格以及制表符，对于合并代码什么的带来的影响还是很大的，所以当我们需要在主分支上面改动，或者在其他branch中改动较少的东西的话，为了避免冲突，使用sublime进行改动为好，缺点即是需要手动保存

20.判断的===
在测试相等性时，基本类型通过它们的值（value）进行比较，而对象通过它们的引用（reference）进行比较。JavaScript 检查对象是否具有对内存中相同位置的引用。
作为参数传递的对象引用的内存位置，与用于判断相等的对象所引用的内存位置并不同。
```javascript
function checkAge(data) {
  if (data === { age: 18 }) {
    console.log('You are an adult!')
  } else if (data == { age: 18 }) {
    console.log('You are still an adult.')
  } else {
    console.log(`Hmm.. You don't have an age I guess`)
  }
}

checkAge({ age: 18 })
```
所以{age:19}==={age:19}不成立

21.webpack打包相关
设置启动页面
```javascript
plugins:[
      template: '/trendAnalysis', //启动页面
      inject: true, //要把script插入到标签里
      multihtmlCache: true // 解决多页打包的关键！
]
```
22.计算数组中true的个数

arrayLike.filter(Boolean).length

23.使用Picker自定义的start以及end问题
mint-ui里面的picker 是关于solts插槽的数据展示问题，所以核心思想即是处理展示的数据问题，并且及时做到组件内部的监听，并及时清空数值

24.需求解构

接口返回从日，到月，最多达到1000条数据。筛选进入图表展示

通过预先处理数组，拿到一个唯一的值，date或者name。
然后push出来进行处理，并进行去重Array.from(new Set(ArrayLike))
然后一个for(var i=0;i<ArrLike.length;i++){
      if(ArrayLike[i]===item.figuer){
            arr.push([item.figuer])
      }
}

25.关于mock数据和真实数据的差异性问题以及前后端分离中的差异问题

即是对于mock数据需要较真且复杂，然后关于mock数据的构建也要达到相应的标准。目前由于后台相关因素，造成前端难以开发，所以调试的难度也加大。

26. 同一接口需要请求多次
原来是通过get，传递多个参数的请求需要使用for

27. 内容
