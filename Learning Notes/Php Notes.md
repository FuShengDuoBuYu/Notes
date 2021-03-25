# Php Notes

## 前言

- **可以开发网页的语言:**

  - php,jsp,asp,python,c/c++

- **WAMP架构解读**

  - Windows + Apache + mysql + php
  - Apache是服务器,这个软件运行在你的电脑上,那么你电脑上的某个一磁盘就是对外可见的,别人可以通过IP或者域名来访问这个磁盘
  - 服务器/客户端是相对概念,也即服务器是资源提供方,客户端是资源受益方,这两者可以随时相互转换,判断方式是资源的方式

- **服务器的安装**

  - (集成开发环境)

    ​         常见的: WAMP(window,apache,mysql,php),LAMP(linux,Apache,mysql,php),PHPnow(apache,mysql,php)

    ​         phpnow下面有一个htdocs这个文件夹是服务器的根目录,是对外可见的

    ​             localhost以及本机IP以及127.0.0.1直接访问本地电脑服务器根目录,通过别的IP可以访问别人的电脑的服务器根目录

    ​             默认访问到的是index.php,index.html,index.jsp

---

## 第一部分: PHP的语法

php所有的内容都必须包含在一个PHP标签中,也即<?php  内容  ?>

​    php的语法是十分严格的,必须有分号

​    **1.php****的输出**

​         (1)  echo "内容";

​             或者

​             echo("内容");

​             举例: 

​                 echo "<h1> hello world </h1>"

​             如果PHP输出语句中有标签的话会自动解析

​             注:php兼容html和css的所有的代码

​         (2) print_r("内容");

​             等价于(1)

​         (3) var_dump(内容);

​             等价于js中的console.log();

​             可以输出很多细节信息

​             举例:

​                 var_dump(100);

​             结果:

​                 int(100)

​             使用一般用于测试程序

​    **2.php****的变量定义**

​         php变量的声明是需要通过$符号进行声明的,它是弱数据类型

​         php变量在使用的时候,其前面永远都会跟着$,例如for($i = 0;$i < 10;$i++){}

​         举例:

​             $username = "浮生多不虞"; //此时username就是一个string类型的数据

​         注: php在进行字符串拼接的时候,不是用+,而是用 . 

​             php在进行字符串拼接时,用占位符的方式拼接,也即{变量/表达式}

​                 两者表达出来的效果大致相同

​    **3.php****的函数**

​         函数定义语法:

​             function 函数名(){

​                 函数体

​             }

​         函数调用语法:

​             函数名();

​    **4.php****的数组**

​         (1)索引数组:下标是数字的数组

​             生成索引数组的语法:

​                 $a = array("1","2","3");

​             利用var_dump($a);来查看信息如下:

​                 array(3) { [0]=> string(1) "1" [1]=> string(1) "2" [2]=> string(1) "3" }

​             输出对应下标的数据:

​                 print_r($a[i]);

​             获取数组长度:

​                 调用count($a);方法,返回数组$a的长度

​         (2)关联数组(键值数组):下标是字符串的数组(类似于集合类型,也即键值对类型)

​             生成关联数组的语法:

​                 $a = array("a" => "1", "b" => "2");

​             利用var_dump($a);来查看信息如下:

​                 array(2) { ["a"]=> string(1) "1" ["b"]=> string(1) "2" }   

​             遍历关联数组

​                 foreach($a as $key => $value){

​                     echo "下标:{$key},数据:{$value}<br/>";

​                 }

​         (3)全局数组:$_GET和$_POST(是系统提供给我们的天生存在的数组)

​             $_GET数组是用来接收通过get提交过来的所有数据

​             $_POST数组是用来接收通过post提交过来的所有数据

​                 也即他们是用来接收从前台传输到后台的数据的

​         (4)多维数组:索引数组与关联数组相互结合,可以构成多维数组

​             举例:

​                 二维数组的定义语法:

​                 $arr = array(

​                     //最里层是关联数组

​                     array("name" => "A", "grade" => "100"),

​                     array("name" => "B", "grade" => "200"),

​                     array("name" => "C", "grade" => "300")

​                 );

​                 想要访问name为"C"的grade:

​                     echo($arr[2]["grade"]);

​         (5)数组函数

​             (a)array_push(数组名,要加入的数据1,要加入的数据1);

​                 在数组的最后位置插入要加入的数据

​    **5.php****中常用的函数**

​         (1)字符串函数

​             md5编码:

​                 功能:md5将任何的数据,变成一个32为的16进制的字符串,该加密是不可逆的.

​                     相同数据加密以后产生的加密字符串是一致的

​             md5函数调用语法:

​                 md5(字符串变量);

​             使用方法:

​                 可以在注册的时候将密码进行md5加密,最终将这个加密后的数据存在数据库里面

​         (2)日期函数

​             (a)date("Y年m月d日 H:i:s");

​                 获取当前的系统时间,必须传进去参数

​                 其表现形式为:

​                     2020年12月09日 15:55:56

​                 由于中国是东八区,因此需要设置中国的时区

​                 date_default_timezone_set("PRC");

​                 这样的话,其表现形式就是

​                     2020年12月09日 23:57:30

​             (b)time();

​                 直接获取当前时间戳,是距离1970年的秒数

---

## 第二部分 认识AJAX

**1.****什么是****AJAX**

​         Asynchronous JavaScript and XMl(异步JavaScript和XML),也即异步的JavaScript和数据传输格式

​         (1)其中xml是一种数据传输格式,其内容是通过用户自定义标签的内容进行传输

​             xml的优点:

​                 种类丰富

​                 传输量大

​             xml的缺点:

​                 解析时麻烦

​                 不适合轻量级数据

​         (2)其中json也是一种数据传输格式(字符串) 95%的移动端应用

​             json的优点:

​                 轻量级数据

​                 解析比较轻松

​             json的缺点:

​                 数据种类比较少

​                 传输量比较小

​         (3)什么是同步和异步

​             同步:当前程序运行的条件是前一个程序已经运行完成

​             异步:当前程序的运行与前一个程序的运行毫无关系

​         (4)ajax其实是前后端数据交互的搬运工,所有操作都可以异步执行,也即传输时不会影响页面的任何执行

​    **2.AJAX****语法**

​         (1)想要将服务器文件夹中的数据拿到,可以在html中写如下的代码

​             注:假设该数据文件为1.txt,内容是 I am a String!,默认已经有了按钮oBtn

​             

​             <scipt>

​                 oBtn.onclink = function(){

​                     //ajax也是一个对象,应该先new对象

​                     //第一步:创建ajax对象

​                     var xhr = XMLHttpRequest();

​                     

​                     //第二步:调用open方法

​                     //第一个参数:  请求方式 get/post

​                     //第二个参数:  url(绝对路径相对路径都可以)

​                     //第三个参数:  是否异步

​                     xhr.open("get","1.txt",true);

​                     

​                     //第三步:调用send方法

​                     xhr.send();

​                     

​                     //第四步:等待数据响应

​                     xhr.onreadystatechange = function(){

​                         if(xhr.readyState == 4){

​                              alert(xhr.responseText);

​                         }

​                     }

​                 }

​         (2)try..throw..catch代码

​             基本逻辑同java里的try catch,不再 赘述

​             更多应用于代码的调试和后期维护

​         (3)onreadystatechange事件

​             事件类型:也即xhr.readystate发生变化时才会触发这个事件

​                 readystate的值一共有4个

​                     0 : 调用open方法之前

​                     1 : 已经调用send方法后,正在发送请求的时候

​                     2 : send方法完成,已经收到全部响应内容的时候

​                     3 : 正在解析相应内容的时候

​                     4 : 相应内容解析完成,可以在客户端使用的时候

​         (4)get与post请求

​             1)html中form的两种提交请求

​                 (a)$_GET 是一个全局数组,是用来存储通过get提交后提交的所有数据的,并且数据是以

​                     键值对的形式存放于这个全局关联数组里的

​                         提交的一个例子就是html中的submit按钮,其提交表单的时候,有以下代码:

​                         html:

​                         <form action="1.php" method="get">

​                              <input typt="text" name="age" placeholder="年龄"/>

​                         </form>

​                         

​                         1.php:

​                         $age = $_GET['age'];

​                         那么此时变量$age就可以获得html中输入的数据了

​                 (b)$_POST 是一个全局数组,是用来存储通过get提交后提交的所有数据的,并且数据是以

​                     键值对的形式存放于这个全局关联数组里的

​                     其提交表单的时候,有以下代码:

​                         html:

​                         <form action="1.php" method="post" enctype="application/x-www-form-urlencode">

​                         <!--最后一个属性照抄即可-->

​                              <input typt="text" name="age" placeholder="年龄"/>

​                         </form>

​                         

​                         1.php:

​                         $age = $_POST['age'];

​                         那么此时变量$age就可以获得html中输入的数据了

​                 (c)get提交的提交方式:

​                     是直接将数据拼接在url后面进行提交,而且是通过?进行拼接,键与值之间用等号连接,

​                     键值对之间用&连接

​                     好处:简单 缺点:不安全,地址栏里面的数据是有上限的,最大2kb,也即无法实现上传

​                 (d)post提交的提交方式:

​                     是通过浏览器内部进行提交的

​                     好处:安全,理论上大小长度没有上限,可以上传  缺点:底层实现较为复杂

​             2)ajax中的两种提交请求

​                 (a)ajax中的get提交

​                     由于get提交是直接将数据拼接在url后面的,因此只需要将url的后面拼接上数据即可

​                     方式是查询字符串:search,即数据前面有问号

​                     举例:

​                         xhr.open("get","1.php?age=18",true);

​                 (b)ajax中的post提交

​                     由于post提交不是将数组写在url后面,因此我们选择将其写在send方法里,

​                     方式是查询字符串:querystring,也即数据前面没有问号

​                     举例:

​                         xhr.open("post","1.php",true);

​                         //如果使用post提交,必须多写这句话

​                         xhr.setRequestHeader("content-type","application/x-www-form-urlencoded");

​                         xhr.send("age=18");

​         (5)将对象转成查询字符串的函数封装

​             html:

​                 function querystring(obj){

​                     var str = "";

​                     //遍历这个对象的每一个键

​                     for(var attr in obj){

​                         //obj[attr]是对象中对应键的值,将他们一次加入到str字符串里

​                         str += attr + "=" + obj[attr] + "&";

​                     }

​                     //截取字符串,使得字符串最后的那个&截去

​                     return str.substring(0,str.length - 1);

​                 }

​         (6)回调函数

​             由于我们最后要对不同的数据进行不同的操作形式,因此我们不能将拿到数据的第四个步骤给

​             写死,所以需要使用到回调函数

​             回调函数就是将一段代码当做参数,然后传到某个函数里,最后在合适的地方调用

​             举例:

​                 在一个方法中,参数有success和error

​                 function test(success,error){

​                 //如果success这个方法存在,就调用这个方法,参数是获取到的数据

​                     if(success){

​                         success(xhr.responseText);

​                     }

​                     else{

​                     //如果error这个方法存在,就调用这个方法,参数是获取到的数据

​                         if(error){

​                              error(xhr.responseText);

​                         }

​                     }

​                 }

​                 

​                 在调用这个text方法时,传参数时,是将success和error作为函数定义与声明传进去

​                 test(

​                     success:function(result){

​                         //与result有关的函数体

​                     },

​                     error:function(result){

​                         //与result有关的函数体

​                     },

​                 )

​    **3.http** **状态码** **status code**

​         (1) 200 : 代表交易成功

​         (2) 404 : 没有发现文件,查询或者URL

​         (3) 400 : 错误请求,比如存在语法错误

​    **4.JSON****对象**

​         (1)JSON和XML是数据传输格式,其实就是将数据结构转换为字符串用来方便数据的传输

​             因此JSON其实就是字符串的一种格式,JSON也是一个对象

​         (2)系统会内置JSON对象,其中有两个常用方法

​         

​             对于前端html而言,有以下两个方法

​             (a)JSON.stringify(数据结构参数);

​                 将数据结构 => 字符串(JSON格式)

​             (b)JSON.parse(JSON字符串参数);

​                 将字符串(JSON格式) => 数据结构

​                 

​             对于后端php而言,有以下两个方法

​             (a)JSON_encode(数据结构参数);

​                 将数据结构 => 字符串(JSON格式)

​             (b)JSON_decode(JSON字符串);

​                 将字符串(JSON格式) => 数据结构

​         (3)前后端交互流程

​             1.通过ajax下载数据

​             2.分析数据,转成对应的数据结构

​             3.处理数据

 

---

## 第三部分 用PHP连接数据库

一共有八个步骤:

​    

​         **//1.****连接数据库**

​         //使用mysqli_connect这个方法,里面有三个参数

​         //分别是数据库连接ip,数据库的用户名,数据库密码

​         //返回值是连接成功与否的Boolean值

​         $flag = mysql_connect("localhost","root","20011024yangshuo");

​         

​         **//2.****判断是否连接成功**

​         if($flag == false){

​             print_r("连接失败");

​             exit();

​         }

​         

​         **//3.****设置字符集**

​         mysql_set_charset("utf8");

​         

​         **//4.****选择数据库****(****也即选择一个****DB)**

​         mysql_select_db("fushengdubuyu");

​         

​         **//5.****准备****sql****语句**

​         $sql = "SELECT * FROM DEPT";

​         

​         **//6.****发送****sql****语句**

​         $res = mysql_query($sql);

​         

​         **//7.****处理结果**

​         $res2 = mysql_fetch_assoc($res);

​         //写几行就是取第几个数据,因此可以使用循环来处理

​         while($res2 = mysql_fetch_assoc($res)){

​             var_dump($res2);

​         }

​         

​         **//8.****关闭数据库**

​         mysql_close();