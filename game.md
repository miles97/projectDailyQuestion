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
              interval: 1
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

关于日期和月就很简单，直接将new Date().getTime(24*60*60*1000)  就是一天的时间，然后fotmattingstring，取值


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

11. dataset的删除数据集和增加操作
