## Vue
Vue学习与练习
## 在根组件引入子组件：
1. 用import来引入所需要的第三方的js。 
2. 函数用function XXX() 来实现。 
3. 用export来暴露function 方法，例如export {XXX}。 
4. 那我们有多个function 方法要进行暴露怎么办？我们可以使用指定一个export default {XXX}来进行默认，其他的均使用export {XXX} 。 
5. 在其他文件中我们怎么使用这些方法？export default {XXX} 我们可以直接 import XXX from ‘XXX’ 
其他使用  import {XXX} from ‘XXX’。

在ES6中，export与export default均可用于导出常量、函数、文件、模块等
export、import可以有多个，export default仅有一个。
例如：
```
父：export const str = 'hello world'
export function f(a){
    return a+1
子：import { str, f } from 'demo1' //也可以分开写两次，导入的时候带花括号
例如：
父：export default const str = 'hello world'
子：import str from 'demo1' //导入的时候没有花括号
```
***************************************************
## 父组件向子组件传值：
父组件通过v-bind传递参数msgname(属性名随便起)，值为value(根组件中的属性)，  
在利用props实现传值的过程中理论上是要实现单向传递，即父组件改变相关参数的值，子组件也相应变化，但是子组件对参数的改变不应该影响父组件。  
但是当props中接收的是父组件传递的引用类型（对象或者是数组）时，在子组件中对数据改变时，父组件中的数据也会相应的改变，因为两者是指向的同一地址内存。  
如果不想子组件的改变影响父组件可以利用深拷贝。  
***********************************************************
## 子组件向父组件传值：
子组件通过this.$emit()派发事件，父组件利用v-on对事件进行监听。  
当子组件触发事件中，有$emit时，就会向父组件中寻找changeCare的自定义事件，然后父组件触发这个事件的函数。  
 this.$emit('changeCart',event.target)向父组件派发事件，同时传递参数event.target,后面的参数的个数不限  
## 路由
路由，其实就是指向的意思，当我点击页面上的home按钮时，页面中就要显示home的内容，如果点击页面上的about 按钮，页面中就要显示about 的内容。Home按钮  => home 内容， about按钮 => about 内容，也可以说是一种映射. 所以在页面上有两个部分，一个是点击部分，一个是点击之后，显示内容的部分。   
路由中有三个基本的概念 route, routes, router。  
+ 1， route，它是一条路由，由这个英文单词也可以看出来，它是单数， Home按钮  => home内容， 这是一条route,  about按钮 => about 内容， 这是另一条路由。    
+ 2， routes 是一组路由，把上面的每一条路由组合起来，形成一个数组。[{home 按钮 =>home内容 }， { about按钮 => about 内容}]    
+ 3， router 是一个机制，相当于一个管理者，它来管理路由。因为routes 只是定义了一组路由，它放在哪里是静止的，当真正来了请求，怎么办？ 就是当用户点击home 按钮的时候，怎么办？这时router 就起作用了，它到routes 中去查找，去找到对应的 home 内容，所以页面中就显示了 home 内容。    
## vue关于class和样式的使用
+ 1.对象语法：  
  我们可以传给v-bind:class一个对象，以动态的切换class。注意：v-bind:class指令可以与普通的class特性共存:    
`<div class="mySelf" v-bind:class="{'class-a':isA,'class-b':isB}"></div>`  
`data:{
   isA:true,
   isB:false
}`    
此时渲染：  
`<div class="mySelf class-a"></div>`    
`<div class="mySelf" v-bind:class="classObject"></div>  
data:{
    classObject:{
      'class-a':true,
      'class-b':false
    }
}`  
+ 2.数组语法：  
`<div v-bind:class="[classA,classB]"></div>`  
`data: {
 classA: 'class-a',
 classB: 'class-b'
}`    
渲染：  
`<div v-bind:class="class-a class-b"></div>`  
+ 3.绑定内联样式  
`<div v-bind:style="{color:bgColor,fontSize:fontSize+ 'px'}"></div>`  
`data:{
  bgColor:'white',
  fontSize: 16
}`  
渲染：    
`<div v-bind:style="styleObject"></div>`  
`data:{
  styleObject:{
    color:'white',
    fontSize:'16px'
  }
}`
## 引入 vue-router
+ `npm install vue-router --save`
+ `import Router from 'vue-router`
+ `Vue.use(Router)`
+ 在router文件夹index.js中配置路由，在 main.js 中使用路由。  
## $route
+ `$route.path` 当前路由对象的路径，如 搜索页面 '/search',订单页面 '/order'
+ `$rotue.params` 关于动态片段（如 /user/:username )的键值对信息,如 {username: 'paolino'}
+ `$route.query` 请求参数，如 /foo?user=1 获取到 query.user = 1
+ `$route.hash` 当前路由的 hash 值 (带 #) ，如果没有 hash 值，则为空字符串
+ `$route.fullPath` 完成解析后的 URL，包含查询参数和 hash 的完整路径
+ `$route.matched` 一个数组，包含当前路由的所有嵌套路径片段的路由记录。路由记录就是 routes 配置数组中的对象副本 (还有在 children 数组)
+ `$route.name` 当前路由的名称
+ `$route.redirectedFrom` 如果存在重定向，即为重定向来源的路由的名字
## $router
+ `this.$router.replace()`  描述：同样是跳转到指定的url，但是这个方法不会向history里面添加新的记录，点击返回，会跳转到上上一个页面。上一个记录是不存在的。  
+ `this.$router.go(n)`  相对于当前页面向前或向后跳转多少个页面,类似 window.history.go(n)。n可为正数可为负数。正数返回上一个页面  
![image](./images/01.png)  
+ `this.$router.push()` 跳转到不同的url，但这个方法回向history栈添加一个记录，点击后退会返回到上一个页面。  
![image](./images/02.png)    


