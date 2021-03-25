# Java Spring Boot + Vue

---

## 第一部分 	前后端分离

- 其实就是将应用的前端代码和后端代码分开写

- 如果不用分离,那么就会出现问题

  >- 传统的java web中,前端用jsp, ,jsp不是后端开发者独立完成的	前端->html->后端->jsp ,这样子的耦合度太高
  >- 这种开发方式效率低,解决的方法就是前后端分离,前端只需要写客户端代码,后端只需要写服务端代码提供数据接口即可,前端通过ajax请求来访问后端的数据接口,将Model展示到view即可
  >- 前后端开发者只需要提前约定好接口文档即可(URL,参数,数据结构等),然后独立分别开发即可,前端可以先造假数据进行测试,不需要依赖于后端,后端也不需要考虑前端,最后完成前后端集成即可
  >- 真正实现了前后端的解耦合    即单体 -> 前端(负责数据展示和用户交互) + 后端(负责提供数据处理接口)
  >- 前端 HTML -> Ajax -> RESTful后端数据接口 

- > 传统的单体应用
  >
  > ![image-20210323165100748](C:\Users\fengchuiyusan\AppData\Roaming\Typora\typora-user-images\image-20210323165100748.png)
  >
  > 前后端分离的结构![image-20210323165401710](C:\Users\fengchuiyusan\AppData\Roaming\Typora\typora-user-images\image-20210323165401710.png)

- 前后端分离就是将一个单体应用拆分成两个独立的应用,前端应用和后端应用以JSON格式进行数据交互,并且是基于RESTful 格式

---

## 第二部分 	实现前后端分离的技术

- Spring boot  +  Vue	即使用 Spring Boot 进行后端开发,使用 Vue 进行前端应用开发

---

## 第三部分	Vue 开发与语法

### 内容一	邂逅 vue.js

- **为什么要学习vue.js** 
  - vuejs目前非常火,前端对 vuejs 的要求是刚性的
  - 项目是需要使用 vuejs 的
- Vue 是一个渐进式的框架,是一个响应式的语言
- Vue 展示列表数据(也即循环),并且它是响应式的

```vue
<tr v-for="item in 数组名">
  <td>{{数组名.数组元素}} </td>
</tr>
```

- **计数器的实现**

  - 新的指令: **@click**,等价于*v-on:click*语法糖该指令用于监听某个元素的点击事件,并且当点击时一般都会执行**methods**中的方法,语法是**v-on**
  - 新的属性:**methods**,该属性用在vue中定义**方法**

  ```vue
  <template>
    <div>
      <table>
        <tr>
  <!--        显示器-->
          <td>当前计数: {{counter}}</td>
        </tr>
        <tr>
  <!--        按钮-->
          <button v-on:click="plus">+</button>
          <button v-on:click="minus">-</button>
        </tr>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    name: "Test",
    // 定义方法
    methods:{
      plus : function(){
        // 此处不再是this.data.数据
        this.counter++;
      },
      minus : function (){
        this.counter--;
      }
    },
    // 定义数据
    data(){
      return{
        counter : 0,
      }
    }
  }
  
  </script>
  
  <style scoped>
  
  </style>
  
  ```

- **Vue中的MVVM**(Model-View-ViewModel)

  - [MVVM的详解](https://baike.baidu.com/item/MVVM/96310?fr=aladdin)

  - 计数器里的MVVM

    > **view :** 
    >
    > <template>
    >
    >   <div>
    >     <table>
    >       <tr>
    > <!--        显示器-->
    >         <td>当前计数: {{counter}}</td>
    >       </tr>
    >       <tr>
    > <!--        按钮-->
    >         <button v-on:click="plus">+</button>
    >         <button v-on:click="minus">-</button>
    >       </tr>
    >     </table>
    >   </div>
    > </template>
    >
    >  
    >
    > **model :**
    >
    >  // 定义数据
    >   data(){
    >     return{
    >       counter : 0,
    >     }
    >   }
    > }
    >
    >  
    >
    > **ViewModel :** 
    >
    > export default {
    >   name: "Test",
    >   // 定义方法

- **创建vue对象时的options**
  - el
    - 类型: string | HTMLElement
    - 作用: 决定之后Vue实例会管理哪个DOM
  - data
    - 类型 : Object | function(组件中data必须是函数)
    - 作用: Vue实例对应的数据对象
  - methods
    - 类型: {[key: string] : Function}
    - 作用: 定义属于Vue的一些方法,可以在其他地方调用,也可以在指令中使用
    - 注:在前端开发中,类里的叫方法(function)和实例对象挂钩,函数(methods)
  - 生命周期函数
- **vue的生命周期**
  - 我们new出的Vue对象时,其内部进行了一系列操作,如果在new vue时写了一些生命周期函数,那就可以起到回调的效果
  - ![Vue 实例生命周期](https://cn.vuejs.org/images/lifecycle.png)

---



### 内容二   vue的基本语法

---

#### 插值操作

- 将data数据插入到html中只需要使用 **Mustache 语法(即双大括号),**此时数据是响应式的

  - ```vue
    <template>
      <div>
        <table>
          <tr>
            <td>这就是:{{test}}</td>
          </tr>
        </table>
      </div>
    </template>
    
    <script>
    export default {
      name: "Test",
      data(){
        return{
          test : "mustache语法",
        }
      }
    }
    
    </script>
    
    <style scoped>
    
    </style>
    ```

  - ![image-20210325112641891](C:\Users\fengchuiyusan\AppData\Roaming\Typora\typora-user-images\image-20210325112641891.png)

  - 