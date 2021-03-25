# HTML

## 第一部分 	系统架构

**1.B/S****架构**

​         Browser / Server 架构,浏览器和服务器的交互形式

​         浏览器支持哪些语言?

​             HTML,Css,JavaScript

​         服务器端的语言?

​             C C++ Java Python等

​         B/S架构的优缺点?

​             优点:升级方便,只升级服务器端代码即可,维护成本低

​             缺点:速度慢,体验不好,界面不炫酷

​         B/S架构的代表?

​             京东,百度,天猫等

​    **2.C/S****架构**

​         Client / Server 架构,客户端[app]和服务器的交互形式

​         缺点:升级麻烦.维护成本较高

​         优点:速度快,体验好,界面炫酷,多用于娱乐性的系统

---

## 第二部分	HTML概述

​    **1.****什么是****HTML?**

​         HTML: Hyper Text Markup Language  (超文本标记语言)

​         由大量的标签组成,每一个标签都有开始标签和结束标签

​         <标签>

​             <标签>

​                 <标签 属性名="属性值" 属性名="属性值">

​                 </标签>

​             </标签>

​         </标签>

​         

​         超文本:图片/声音/视频/流媒体等        

​    **2.****怎么开发****HTML?**

​         使用普通的文本编辑器即可,但是也有专业的开发工具,例如 Dreamweaver等

​         文件扩展名是.html或者.htm

​    **3.****怎么运行****HTML?**

​         直接用浏览器打开HTML文件就是运行

​    **4.HTML****是谁制定的****?**

​         W3C 世界万维网联盟

​         它指定了HTMl规范,每个浏览器生产厂家都会遵守这个规范,HTMl程序员也会按照这个规范写代码

​         HTML目前最高的版本是HTML5.0,简称h5

​         为了方便中国程序员进行web开发,有一个w3school的网站专门提供web前端的帮助文档

​    **5.HTML****基本概念**

​         (1)注释格式:

​             <!--

​                 注释

​                 注释

​             -->

​         (2)如果在最顶头加上

​             <!doctype html>

​             那么就是h5,如果不加那就是html4.0

​         (3)<html></html>

​             这是根,写在最前头

​         (4)<head></head>

​             这是头,写在根的里面

​         (5)<body>xxxxxxxxx</body>

​             这是体,写在根的里面,xxxxxxxxx会出现在网页的主体位置

​         (6)<title>xxxxxxxx</title>

​             这是标题,xxxxxxxx会显示在标签页的标签位置

​         (7)html不区分大小写,语法松散不严格

​         

​         <html>

​             <head>

​                 <title>网页的标题</title>

​             </head>

​             <body>

​                 网页的主体内容:欢迎学习HTML

​             </body>

​         </html>



---

## 第三部分	HTML的基本标签

**1.****段落标记**

                 <p>内容</p>

​         这样"内容"就会成为一个自然段显示

                 <p>我想给你个拥抱像朋友一样可以吗?</p>

                 <p>我忍不住从背后抱了一下,尺度掌握在不能说想你啊</p>

​    **2.****标题字****[html****预留的格式****]**

​         类似于Word中预留的标题字,是固定大小和格式的六种,分别是h1到h6

​         

​         <h1>标题字</h1>

​         <h2>标题字</h2>

​         <h3>标题字</h3>

​         <h4>标题字</h4>

​         <h5>标题字</h5>

​         <h6>标题字</h6>

​    **3.****换行****[****独目标记****]**

​         内容1<br>内容2

​         这样内容1 和 内容2 之间就换行了

​         注:不能写成<br></br>

​    **4.****水平线****[****独目标记****]**

​         <hr>

​         这样就会打印出一条横线

​         在其中可以加入属性

​         <hr color = "red" width = "50%">

​         (颜色为红并且宽度为页面的50%)

​             注:color 和 width都属于hr标签的属性,单双引号都可以也可以不写      

​    **5.****预留格式**

                 <pre>内容</pre>

​         这样内容中的所有格式,包括空格,回车等都会保留

​    **6.****字体格式**

​         (1)删除字

​             <del>xxx</del>

​             xxx会有一个删除线拦腰截断

​         (2)插入字

​             <ins>xxx</ins>

​             xxx会有下划线

​         (3)粗体字

​             <b>xxx</b>

​             xxx是粗体

​         (4)斜体字

​             <i>xxx</i>

​             xxx是斜体

​         (5)右上角加字[例如平方]

​             10<sup>2</sup>

​             这是10^2

​         (6)右下角加字[例如下标]

​             O<sub>2</sub>

​             这是氧气

​         (7)字体标签

​             <font> color="red" size = "50">xxx</font>

​             xxx此时颜色红色,大小为50

---

##	第四部分	HTML实体符号

**1.****小于号用** **<** **替代**

​         注:less than

​    **2.****大于号用** **>** **替代**

​         注:greater than

​    **3.****空格用** ** ** **替代**

​         注:pre标签可以使用

​    **4.****所有的实体符由****&****开始****,****由****;****结尾**

---

## 第五部分	HTML 的表格

**1.****表格标签**

                 <table border = "1px" width = "200px"></table>

​         border = "1px"表示设置表格边框为1像素宽度

​         width = "200px"表示表格总宽度为200像素,同样可以是窗口百分比

​         height同理

​    **2.****表格的行标签**

​         <tr align = "center"></tr>

​         注:table row

​         align = "center" 表示对齐方式是居中对齐

​         <center></center>也可以作为标签使得内容居中显示

​    **3.****表格的行中数据**

​         <td>></td>

​         注:table data

​    **4.****举例**

                 <table border = 1px width = 30% align = center>

​             <tr>

​                 <td>水原千鹤</td>

​                 <td>七海麻美</td>

​             </tr>

​             <tr>

​                 <td>更科琉夏</td>

​                 <td>樱泽墨</td>

​             </tr>

​         </table>

​    **5.html****的单元格合并**

​      上下的单元格合并

​         (1)先找到需要合并的单元格,删除后面的单元格只剩下最头的一个

​         (2)在剩下的一个单元格里加上rowspan属性,rowspan=数字,数字是几就是合并几个单元格

​         举例:

​             <td rowspan = 2>36</td>

​             此时是合并了两个单元格

​         注:row合并的时候,删除后面的单元格

​         

​      左右的单元格合并

​         (1)和上下的单元格合并完全一致,只是此时的rowspan变成了colspan

​         注:此时删除哪一个没有限制

​    **6.th****标签****[table headline]**

​         th可以替代td,此时输入的数据会自动居中并加粗

​         th标签也是单元格标签,一般会用在表格的第一行

​    **7.thead tbody tfoot****标签****[****在****table****中不是必须的只是便于后期****js****代码的编写****]**

​         <thead></thead>这之间的内容就是表格头

​         相应的表格身和表格尾

​    表格总代码

​         <!doctype html>

​         <html>

​             <head>

​                 <title>表格总结</title>

​             </head>

​             <body>

                                  <table align = center border = 1px width = 50%>

​                     <thead>

​                         <tr align = center >

​                              <td colspan = 4>女朋友</td>

​                         </tr>

​                     <tbody>

​                         <tr align = center>

​                              <td>水原千鹤</td>

​                              <td>七海麻美</td>

​                              <td>樱泽墨</td>

​                              <td>更科琉夏</td>

​                         </tr>

​                     </thead>

​                 </table>

​             </body>

​         </html>

---

## 第六部分	HTML 的背景色和背景图片

**1.<meta charset="utf-8">****代表告诉浏览器使用的是****utf-8****编码格式****,****并不是设置当前文件是什么编码**

​    **2.****背景颜色****:**

​         属性: bgcolor = 颜色

​         这个属性是出现在body标签当中的

​             <body bgcolor = blue>

​    **3.****背景图片****:**

​         属性: background = 图片路径

​             <body background = C:\壁纸\991136.jpg>

​    注:背景色和背景图片都有时,背景色在背景图片的下面

---

## 第七部分	图片 img 标签

1.img标签里面可以有高度/宽度等图片属性,但是高宽度只能选一个,否则不会等比例缩放导致失真

​    2.<img src=路径 width = 100px height = 200px></img>

​    3.img标签就是图片标签,src属性就是图片的路径

​    4.width设置宽度,和height设置高度

​    5.title属性在img标签中用来设置鼠标悬停在图片上时悬停的信息

​    6.alt属性是设置图片加载失败时显示的提示信息

​    7.开始标签和结束标签之间如果没有任何内容,那么可以在开始标签的最后加一个/,这样结束标签就可以省略不写

​         例如:<img src=路径 width = 100px height = 200px/>

---

## 第八部分	HTML 超链接

**1.****文字超链接**

​         (1)格式:

                         <a href="网址">显示在自己网页中的名字</a>

​         (2)举例:

                         <a href = "http://www.baidu.com">百度首页</a>

​         (3)href : hot reference 热引用

​             href这个属性后面添加的一定是一个资源的地址,这个地址可以是绝对路径,可以是相对路径

​                 可以是网络中的资源路径,也可以是本地资源路径

​         (4)超链接的特点

​             有下划线

​             鼠标停留在超链接上会显示小手形状

​             点击超链接后会跳转页面

​         (5)在浏览器中F12后会出现前端的源代码,可以修改里面的源代码进行调试

​    **2.****图片超链接**

​         (1)格式:

                         <a href = "网址">一个<img>标签</a>

​    **3.****其他属性**

​         在a中除了href属性外,还有target属性

​         target属性可取值:

​             _blank

​                 超链接网址是一个新窗口

​             _self

​                 超链接网址是当前窗口,不会开新窗口[默认方式]

​             _top

​                 顶级窗口

​             _parent

​                 父窗口

​    **4.****超链接的作用**

​         通过超链接可以从浏览器向服务器发送请求,浏览器发送数据叫做请求(request)

​         服务器向浏览器发送数据叫做响应(response)

​         B/S结构的系统,每一个请求都会对应一个响应

---

## 第九部分	HTML列表

**1.****无序列表**

​         <ul></ul>代表这是一个无序列表

​         在里面可以加<li>数据</li>表示列表中数据

​         如果列表中还有列表,那么就在<li>数据 后面再加<ul><li>数据2</li></ul

​         指定列表数据前的标志可以在ul中加属性 type circle disc square

​    **2.****有序列表** **order**

​         <ol></ol>代表是一个有序列表

​         在里面数据的前面的标志不是圆形方形等,而是数字或者罗马或者字母,它是由type属性控制的

---

## 第十部分	HTML 表单[form]

**1.****表单有什么用****?**

​         收集用户信息

​         表单展现之后,用户填写表单,点击提交后会将数据提交给服务器

​    **2.****怎么画一个表单****?**

​         使用form 标签

​         <form></form>

​    **3.****一个网页中可以有多个表单标签**

​    **4.****表单****form****中的属性**

​         (1)action = "服务器地址"

​             指定将数据提交给的服务器

​             action和href一样,都可以向服务器发送request

​         (2)method = post或者get

​             当为post的时候,用户提交的信息不回显示在地址栏上,被隐藏了

​             当为get的时候,用户提交的信息会显示在地址栏上

​             建议采用post方法保护隐私

​             method的属性不指定时默认是get

​    **5.****提交数据**

​         (1)可以画一个提交按钮,这个按钮使用input输入域,type = "submit"的时候表示这个按钮是提交按钮,可以提交表单

​             <form>

​                 <input type = "submit"/>

​             </form>

​             type有多种选择[text(文本),password(密码),reset(清空)],不同的选择的按钮功能不同

​         (2)input 按钮标签除了type属性,还有value属性可以显示设置按钮上显示的文本

​             除此之外,input还有name属性和value属性

​             表单是以action?name=value&name=value...的格式提交的

​                 因此input中的数据想要提交,必须有name和value数据(当type是text时,value由用户输入,程序员不用写)

​                 <input type = text name = password />

​                 此时提交的name是password,value是用户输入值    password=输入值

​         (3)input按钮和href有什么区别?

​             input按钮可以将表单的数据提交给超链接中的网址

​             <form action "a">

​                 <input type = "text"/>

​            <input type = "submit"/>

​           </form>

​             此时的第一个type中的用户输入的文本会一起提交到a这个服务器中并跳转

​             即:两者都可以向服务器发送请求,但是表单在发送请求的时候可以携带数据

​         (4)form里面可以直接在<input>前面写上汉字,例如用户名密码等

​             用户名 <input type = "text"/><br>

​             密码 <input type = "text"/><br>

​             <input type = submit value = 登录 />

​         注:表单项写了name属性的,一律会提加给服务器,不想提交这一项,就不要写name属性

​             当name没写的时候数据不会被提交,当value没有写的时候,value的默认值是空字符串会提交 String s = "";

​             单选按钮的value必须程序员自己指定

​             超链接也可以提交数据给服务器,但是提交的数据是固定不变的,超链接是get请求,不是post请求

​         (5)总代码

​             <!doctype html>

​             <html>

​                 <head>

​                     <title>注册表单</title>

​                 </head>

​                 <body>

​                     <form http://localhost:8080/jd/register>

​                         用户名<input type = text name = "username" />

​                         <br>

​                         密码<input type = password name = "userpassword" />

​                         <br>

​                         确认密码<input type = password />

​                         <br>

​                         性别

​                         <br>

​                         <input type = radio name = sex value = man checked>男

​                         <br>

​                         <!--radio是一个单选按钮,name一样保证只能选一个,value需要程序员自己写

​                              在最后加入checked可以使得默认选择该选项-->

​                         <input type = radio name = sex value = woman>女

​                         <br>

​                         兴趣爱好<!--checkbox是多选按钮-->

​                         <input type = checkbox name = hobby value eat/>吃

​                         <input type = checkbox name = hobby value drink/>喝

​                         <input type = checkbox name = hobby value firehair checked/>玩

​                         <br>

​                         <!--在最后加入checked可以使得默认选择该选项-->

​                         学历<!--select是选择栏框,后面加selected是默认选择-->

​                         <select name = grade>

​                              <option value = xxs>小学<option/>

​                              <option value = zxs selected>中学<option/>

​                              <option value = dxs>大学<option/><br><br><br>

​                         <!--textarea是文本域,文本域没有value属性,用户自己填的就是-->

​                        简介<textarea rows = 20 cols = 40 name = introduce></textarea>

​                         <br>

​                         <input type = submit value = 提交>

​                         <input type = reset value = 清空>

​                     </form>

​                 </body>

​             </html>

​             (6)select下拉列表怎么支持多选?

​                 在select标签中加入属性 multiple = multiple,多选时按住Ctrl键

​                 在select标签中加入属性 size = 梳子 可以显示出能显现出条目数量

​             (7)form的file控件

​                 <input type = file>这样出现的按钮点击后可以进行文件的选择,文件上传专用

​             (8)隐藏域hidden控件

​                 隐藏域:网页上看不到,但是表单提交的时候会自动提交给服务器

​                 也就是如果这个数据不想让用户看见,但是还要给服务器传过去,就用这个

​                 <input type=hidden name=userid value = 111>,这里value是程序员自己赋值

​             (9)在input中的readonly和disabled

​                 在input标签的最后加上readonly或者disabled时

​                 

​                 两者都是只读,不能修改,但是readonly可以提交给服务器,而disabled数据不会提交,即使有name属性也不会提交

​             (10)input控件的maxlength属性

​                 <input type=text maxlength=n />

​                 此时代表文本框中可输入的字符数量为n

---

## 第十一部分	HTML 中的元素的id属性

**1.****在****HTMl****文档中****,****任何元素****[****标签****](****节点****)****都有****id****属性****,id****属性是该节点的唯一表示**

​         因此在同一个HTML文件中,id值不能重复,id就相当于是节点的什么证号码

​    **2.****表单在提交数据的时候****,****只和****name****有关系****,****和****id****无关**

​    **3.id****有什么用****?**

​         id是为了让我们更加方便的获取这个元素

​    **4.HTML****是一棵树****,****树上有很多节点****,****每个节点都有唯一的****id,****这个树叫做****dom****树****[document]**

---

## 第十二部分	div 和 span 在网页中的应用

**1.div****和****span****的用处****?**

​         他们都可以称为图层,图层的作用是保证页面可以灵活的布局

​    **2.****图层是一个一个的盒子****,div****嵌套****div****就是盒子套盒子****,div****和****span****是可以定位的****,****只要定下****div****的左上角的****xy****坐标即可**

​    **3.****默认情况下****div****会独自占用一行****,****而****span****不会独自占用一行**

​    **4.div****也可以进行嵌套**

                 <div id = "div1">

                         <div id = "div2">

​             </div>

​         </div>

---

# CSS

## 第一部分	CSS 概述

**1.****什么是****CSS?****有什么用****?**

​         CSS:层叠样式表语言[Cascading Style Sheet]

​         CSS的作用是修饰HTML的页面中的元素的样式等,让其更美观

​         HTML相当于是主体,CSS依赖于HTML,因此新建的文件还是xxx.html

---

## 第二部分	在HTML中嵌套CSS的三种方式

**1.****内联定义**

​         即在标签的内部使用style属性来设置元素的CSS样式

​         语法格式:

​         <标签 style="样式名:样式值;样式名:样式值;..."></标签>

​    **2.****定义内部样式块对象**   

​         即在head标签中使用style块

​         语法格式:

​         <head>

                         <style type="text/css">

​                 选择器 {

​                     样式名:样式值;

​                     样式名:样式值;

​                     样式名:样式值;

​                     ...

​                 }

​                 选择器 {

​                     样式名:样式值;

​                     样式名:样式值;

​                     样式名:样式值;

​                     ...

​                 }

​             </style>

​         </head>

​    **3.****链入外部样式表文件****[****最常用****]**

​         将样式写到一个独立的xxx.css文件中,在需要的网页上直接引入css文件

​         语法格式:

​         <link type="text/css" rel="stylesheet" href="css文件路径" /> 

​         优点:易于维护,维护成本低

---

## 第三部分	内联法嵌套CSS

**1.****代码举例****:**

​         <body>

                         <div style = "width : 300px; height : 300px; background-color : blue; display:none; border:1px solid red; "></div>

​         </body>

​         注:display是布局样式,当为block时显示,none表示隐藏

​             border的三个参数是宽度 样式 颜色

---

## 第四部分	样式块嵌套 CSS

**1.CSS****中的注释格式****:/\*  \*/**

​    **2.****代码举例****:**

​         <!doctype html>

​         <html>

​             <head>

​                 <title>Css嵌套html</title>

                                  <style type=text/css>

​                 /*

​                 */

​                     \#123{

​                         color : blue;

​                         font-size : 20px;}

​                 </sytle>

​             </head>

​             <body>

​                 <span id="123">水原千鹤</span>

​             </body>

​         </html>

​    **3.****选择器**

​         (1)id选择器:

​             \#id{

​                 样式名:样式值;

​                 ...}

​         (2)标签选择器:

​             标签名{

​                 样式名:样式值;

​                 样式名:样式值;

​                 ...}

​             注:这个选择器的范围比id选择器的范围广

​         (3)类选择器:

​             .类名{

​                 样式名:样式值;

​                 样式名:样式值;

​                  ...}

​             注:每一个标签都可以用class属性定义一个自己的class名,从而人工确定.class的对象

​             优点是可以跨标签,class相同的标签可以认为是同一类标签

---

## 第五部分	引入外部独立的CSS文件

实质上就是写一个css文件在外部.利用语法:

​         <link type="text/css" rel="stylesheet" href="css文件路径" /> 

​    将css文件的路径写下来就可,这个<link>需要写在<head></head>里面

---

## 第六部分	常用的样式

**1.****列表样式**

​         在<head></head>里加上

                         <style type="text/css">

​                 ul{

​                     list-style-type : xxxx;

​                 }

​             当xxxx为none时,此时是将小圆点等等去掉了,毫无格式

​    **2.****样式的绝对定位**

​         选择器{

​             position : absolute;

​             left : 100px;

​             top : 100px;

​         }

​         注:此时代表某个标签显示出来的东西左上角为基准,距离左边和上面都是100px

---

