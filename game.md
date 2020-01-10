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

27. 对于项目中的流程把控

项目阶段的进行过程以及各种测试点的把握，主要功能点的细节测试，项目中的问题(Icon.接口数据格式问题)

28. chorme断点调试以及mock,本地模拟数据的工程化

因为团队中很复杂的问题，每次后台修改的发版都会导致前端的联调出现500错误，造成开发时间的浪费，又由于接口数据的复杂化，不能简单的使用静态的mock数据进行模拟，甚至很多接口之间也由依赖问题，

30. 根据特定数据，处理数组，
```
that.chartsData.forEach((item, index) => {
    for (let i = 0; i < arrDate.length; i++) { //对应日期数据时的处理
        if (item.currDate == arrDate[i]) {       //根据同日期进行操作
            if (!!item.elementData) {           //对于没有数据的处理
                if (!!mathArr2[i]) {            //新建二维数组,判断有无
                    mathArr2[i].push(item.elementData)   //有时，进行渲染操作
                } else {                        //当数组为无时，新建数组
                    mathArr2[i] = []
                    mathArr2[i] = [item.elementData]
                }
            } else {                           //对应日期无数据时的处理
                if (!!mathArr2[i]) {           //进行操作
                    mathArr2[i].push('0')      //进行数据填充
                } else {
                    mathArr2[i] = []           //关于数据的
                    mathArr2[i] = ['0']        //填充数据
                }
            }
            if (!!resArr[i]) {                  //新建一个resArr，用于显示每次渲染的列表长度，进而判断何时unshift日期
                resArr[i].push(item.currDate)
            } else {
                resArr[i] = []                  //
                resArr[i] = [item.currDate]     //
            }
            if (resArr[i].length == 1) {
                mathArr2[i].unshift(arrDate[i])  //根据列表长度当且仅当为一时，填充一次数据
            }
        }
    }
})
```
31. 目前中的疑难问题一览

对于dataset数据集的处理，以及添加，删除。处理dataset数组的注意事项

dimension是最好处理的，只要把Name单独push出来，然后根据每一个的纬度进行数据的Push.

数据之前是legend，x轴横坐标的name取值。

由于data是一一对应的，所以需要创建二维数组，而二维数组的新建就需要在一维数组里面使用这种方法```arrLike[i]=[]```新建效率最高.用其他的fill等不行。
然后再去填充数据，判断初始值的大小.具体实例如.30

同时请求多次同接口不同参数的情况，并对于数据整合进行处理，concat(),在最后一次渲染的时候进行处理。

接口逻辑;请求list的先后数据，依赖的接口以及无用的接口

32.safari浏览器以及chorme之间的区别

hybird开发中发现safari不能在参数中进行进行数据处理，只能接受一个指定的对象传递，而chorme就可以直接传递。解决方案较为简单，即是创建参数，重新处理后再指向该对象。this.dataForUrl

33. 当接口无数据的时候默认填充或者处理

```javascript
suc.data.forEach(()=>{
if (!item.elementData && item.elementData !== 0) {  //当数据没有的时候变成'-'空缺，数据为零时除外,正常处理
      item['elementData'] = '-'
         } else {
      }
})
```

34. SPA单页面切换路由时候的相关哲学

关闭所有选项卡;关闭弹出框;清空数据;

通过组件内监听一个flag的数据，flag=!flag,然后在组件的watch的handler函数内中  
if(this.clickon){
      this.clickon=false
}

35. 对于接口依赖的promise

emmmmm暂时并没有什么强烈的可以书面表述的经验之谈

36.跳转过程中使用的组件，页面等问题

关于特定的页面展示，可以直接通过组件的方式引入，如果新页面的数据过多，跳转比较适合。
然后对于缓存还是url传参，或者是直接通过组件的props方式传参。
组件向父传参,父页面使用方法@xxx='xxx'
子组件this.$emit(xxx,this.xxx)

37.echarts使用心得

所有的属性都可以使用方法遍历，然后赋值改变状态。
```
    that.series.forEach(item => {
        item['showSymbol'] = false
        item['yAxisIndex'] = '0'
    })
```

38.对于接口字段新增的问题
字段配置统一规范嗷嗷

39.关于桌面版页面的适配性

由于目前都是移动有限的策略，对于页面的响应式构建甚至在H5中即昙花一现的存在。除了个别适配不同分辨率和大小的显示器外，单独的移动版页面仍然需要重新请求才能获得。

40.使用移动框架依赖性的问题
出于性能考量，很多耦合的语言都会使用一些简单的框架语言进行功能的实现。

41.相比之下通过引入简单的插件语言比JS框架效果更好且更容易实现功能
