# VUE内容

## 介绍

1. Vue (读音 /vjuː/，类似于 **view**) 是一套用于构建用户界面的**渐进式框架**。 核心库只关注视图层 。 Vue.js 的核心是一个**允许采用简洁的模板语法来声明式地将数据渲染进 DOM 的系统** 

2. 响应式

   ```html
   <div id="app">
     {{ message }}
   </div>
   var app = new Vue({
     el: '#app',
     data: {
       message: 'Hello Vue!'
     }
   })
   //在浏览器修改 app.message 的值，就可以看到页面上的值在实时刷新
   ```

3. 指令： 指令带有前缀 `v-`，以表示它们是 **Vue 提供的特殊特性**。 它们会在渲染的 DOM 上**应用特殊的响应式行为。**  

   如 v-bind:title 、 v-if 、 v-for 

   ```html
   <div id="app-4">
     <ol>
       <li v-for="todo in todos">
         {{ todo.text }}
       </li>
     </ol>
   </div>
   var app4 = new Vue({
     el: '#app-4',
     data: {
       todos: [
         { text: '学习 JavaScript' },
         { text: '学习 Vue' },
         { text: '整个牛项目' }
       ]
     }
   })
   //控制台里，输入 app4.todos.push({ text: '新项目' })，你会发现列表最后添加了一个新项目。
   ```

4.  用 **v-on 指令**添加一个事件监听器 

   ```html
   <div id="app-5">
     <p>{{ message }}</p>
     <button v-on:click="reverseMessage">反转消息</button>
   </div>
   var app5 = new Vue({
     el: '#app-5',
     data: {
       message: 'Hello Vue.js!'
     },
     methods: {
       reverseMessage: function () {
         this.message = this.message.split('').reverse().join('')
       }
     }
   })
   ```

    **v-model 指令**，它能轻松实现表单输入和应用状态之间的双向绑定 

   ```html
   <div id="app-6">
     <p>{{ message }}</p>
     <input v-model="message">
   </div>
   ```

5. 组件化应用构建

    ![Component Tree](https://cn.vuejs.org/images/components.png)

    

   ```html
   //自定义组件
   Vue.component('todo-item', {
     // todo-item 组件现在接受一个
     // "prop"，类似于一个自定义特性。
     // 这个 prop 名为 todo。
     props: ['todo'],
     template: '<li>{{ todo.text }}</li>'
   })
   //使用组件
   <div id="app-7">
     <ol>
       <!--
         现在我们为每个 todo-item 提供 todo 对象
         todo 对象是变量，即其内容可以是动态的。
         我们也需要为每个组件提供一个“key”，稍后再
         作详细解释。
       -->
       <todo-item
         v-for="item in groceryList"
         v-bind:todo="item"
         v-bind:key="item.id"
       ></todo-item>
     </ol>
   </div>
   
   
   //组件的data必须是一个函数，以避免组件多次使用时，数据串了
   data: function () {
     return {
       count: 0
     }
   }
   ```

   ```
   // 子组件可以通过调用内建的 $emit 方法 并传入事件名称来触发一个事件
   <button v-on:click="$emit('enlarge-text')">
     Enlarge text
   </button>
   
   // 父组件中响应子组件的点击
   <blog-post
     ...
     v-on:enlarge-text="postFontSize += 0.1"
   ></blog-post>
   ```

   

## vue实例

1.  var vm = new Vue({  // 选项 }) 	

    创建一个 Vue 实例时，可以传入一个**选项对象** ; 所有的 Vue 组件都是 Vue 实例 。

   

2. **data选项。**用户定义的需要响应式的值

    `data` 对象中的所有的属性加入到 Vue 的**响应式系统**中。当这些属性的值发生改变时，视图将会产生“响应”，即匹配更新为新的值 

   **vue  前缀 为`$的自带属性和方法。`** 

3. vue生命周期钩子

    <img src="https://cn.vuejs.org/images/lifecycle.png" alt="Vue 实例生命周期" style="zoom:50%;" /> 



## 模板语法

指令缩写：

```vue
v-bind:href			->			:href
v-on:click			->			@click
```



