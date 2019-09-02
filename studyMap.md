## javaScript权威指南学习以及React同步学习

* 组件的编码方式以及思想

* 关于实现的问题

* 项目编码的时候DOMtree消失

发现是if条件渲染时候吃掉了部分dom tree，并且重新部分加载数据，导致异常。v-if的条件加载类似于create的周期函数，但是不完全一致。

* 关于webstorm以及VScode，因为团队中仅一人使用webstorm，为了代码合并的时候不冲突，还是回退到了vscode，此外。编码中减少代码格式化的习惯对于生产，stage，均有好处。

* 项目管理流程相关的问题，开发设计，项目开发，提交测试，缺陷修复，stage，Online。

主要阶段即是开发，需求确认，测试，上线。

* 组件化的思维方式，参考vant，将可复用的任何内容都以组件化的形式进行展现，减少重复劳动。

* 使用return语句代替if else
```
function(arr){
  if(arrgument){
    return;
  }
  //如果arrgument为true,这里不执行
}
```
* 使用history完成时间旅行
通过该将每次的操作数据放到一个数组集合内，并且记录每一步的时间以及tickCount，完成恢复操作

* 通过监听滑动操作完成移动端的左滑删除

* 原型链  监听  绑定事件

## begin of real hard Work

* 给注释增加 FIXME 或 TODO 的前缀，来自airbnb语法规范

* 增加参数的注释
```js
/**
 * 函数描述
 *
 * @param {Object} option 参数描述
 * @param {string} option.url option项描述
 * @param {string=} option.method option项描述，可选参数
 */
function foo(option) {
    // TODO
}
```
