# Vue
Vue学习与练习
##在根组件引入子组件：
1. 用import来引入所需要的第三方的js。 
2. 函数用function XXX() 来实现。 
3. 用export来暴露function 方法，例如export {XXX}。 
4. 那我们有多个function 方法要进行暴露怎么办？我们可以使用指定一个export default {XXX}来进行默认，其他的均使用export {XXX} 。 
5. 在其他文件中我们怎么使用这些方法？export default {XXX} 我们可以直接 import XXX from ‘XXX’ 
其他使用  import {XXX} from ‘XXX’。

在ES6中，export与export default均可用于导出常量、函数、文件、模块等
export、import可以有多个，export default仅有一个。
例如：
父：export const str = 'hello world'
export function f(a){
    return a+1
子：import { str, f } from 'demo1' //也可以分开写两次，导入的时候带花括号
例如：
父：export default const str = 'hello world'
子：import str from 'demo1' //导入的时候没有花括号
***************************************************
##父组件向子组件传值：
父组件通过v-bind传递参数msgname(属性名随便起)，值为value(根组件中的属性)，
在利用props实现传值的过程中理论上是要实现单向传递，即父组件改变相关参数的值，子组件也相应变化，但是子组件对参数的改变不应该影响父组件。
但是当props中接收的是父组件传递的引用类型（对象或者是数组）时，在子组件中对数据改变时，父组件中的数据也会相应的改变，因为两者是指向的同一地址内存。
如果不想子组件的改变影响父组件可以利用深拷贝。
***********************************************************
##子组件向父组件传值：
子组件通过this.$emit()派发事件，父组件利用v-on对事件进行监听。
当子组件触发事件中，有$emit时，就会向父组件中寻找changeCare的自定义事件，然后父组件触发这个事件的函数。
 this.$emit('changeCart',event.target)向父组件派发事件，同时传递参数event.target,后面的参数的个数不限
