# MYSQL Notes

## 第一部分	数据库概述

**1.****数据库：数据库管理系统，通过简单的****sql****语句进行控制**

​    **2.****有哪些数据库管理系统？**

​         Oracle 甲骨文      MYSQL       DB2     Sybase        MS SqlServer 支持标准sql的数据库管理系统

​    **3.sql****、****DB****、****DBMS****之间的关系**

​         sql：

​         DB：DataBase（数据库，数据库实际上在硬盘上以文件的形式存在）

​         DBMS：DataBase Management System（数据库管理系统，MySQL，Oracle，DB2,等）

​         SQL：结构化查询语言，是一门标准通用的语言，标准的sql语言适合于所有的数据库产品

​              我们的sql属于高级语言，只要写的出来，就可以看懂

 sql语句在执行的时候，实际上也会是先进行编译，然后执行SQL（SQL的语句的编译有所DBMS完成，我们看不见）

​         三者关系：

​             DBMS负责执行sql语句，通过执行sql语句来操作DB中的数据

​                 DBMS--(执行)-->SQL--(操作)-->DB

​    **4. 127.0.0.1****（等价于****localhost****）代表的是本机****ip**

​    **4.****什么是表（****table****）？**

​         （1）表：数据库的基本组成单元，所有的数据都以表格的形式组织，目的是可读性强

​         （2）一个表包括行和列  

​                 行：被称为数据/记录（data）

​                 列：被称为字段（column）

​         （3）每一个字段应该包含哪些属性？

​                 字段名                数据类型          相关的约束

​                 举例：                110              120              120

​                 这个字段的字段名可以是 学号，数据类型是int ，

​                     注：在数据库中字符串不是String，而是varchar，长整数不是long而是bigint

​    **5.SQL****语句的分类**

​         （1）DQL(数据查询语言，data query language)：查询语句，凡是select语句都是DQL

​         （2）DML(数据操作语言，data manipulation language)：增删改表中的数据，凡是insert、delete、update都是增删改语句

​         （3）DDL(数据定义语言，data defination language)：对表的结构的增删改，凡是create、drop、alter都是增删改表结构

​         （4）TCL(事务控制语言，transaction control language)：commit提交事务，rollback回滚事务

​        （5）DCL(数据控制语言，data control language)：grant授权、revoke撤销权限

​    **6.****导入数据**

​         第一步：在dos窗口中登陆mysql

​         第二步：查看有哪些数据库

​             show databases;     [这个不是SQL语句，是mysql的命令]

​             +--------------------+

​             | Database      |

​             +--------------------+

​             | information_schema |

​             | mysql       |

​             | performance_schema |

​             | test        |

​             +--------------------+

​         第三步：创建自己的数据库

​             create database fushengduobuyu;      [这个不是SQL语句，是mysql的命令]

​         第四步：使用fushengduobuyu这个自己创建的数据库

​             use fushengduobuyu;          [这个不是SQL语句，是mysql的命令]

​         第五步：查看当前使用的数据库中有哪些表

​             show tables;             [这个不是SQL语句，是mysql的命令]

​         第六步：初始化数据

​             source 然后将文件拖到dos窗口中，执行的是sql文件

​         注：数据初始化完成后有文件中的表数据了

​         第七步：删库跑路

​             drop database 库名;

​    **7.****对****SQL****脚本的理解**

​         （1）文件以.sql为扩展名，并编写了大量的sql语句，被称为SQL脚本

​    **8.****查看表结构以及表中的数据**

​         （1）查看表结构 

​                 desc 表名;

​                 举例：

​                 mysql> desc dept;

​                 +--------+-------------+------+-----+---------+-------+

​                 | Field | Type    | Null | Key | Default | Extra |

​                 +--------+-------------+------+-----+---------+-------+

​                 | DEPTNO | int(2)   | NO  | PRI | NULL   |    |  部门编号

​                 | DNAME | varchar(14) | YES |   | NULL  |    | 部门名称

​                 | LOC  | varchar(13) | YES |   | NULL  |    |  部门位置

​                 +--------+-------------+------+-----+---------+-------+

​         （2）查看表数据

​                 select * from 表名;

​                 举例：

​                 mysql> select * from dept;

​                 +--------+------------+----------+

​                 | DEPTNO | DNAME   | LOC   |

​                 +--------+------------+----------+

​                 |   10 | ACCOUNTING | NEW YORK |

​                 |   20 | RESEARCH  | DALLAS  |

​                 |   30 | SALES   | CHICAGO |

​                 |   40 | OPERATIONS | BOSTON  |

​                 +--------+------------+----------+

---

## 第二部分	MySQL的安装与配置

**1.MySQL****的端口壁板都是****3306**

​    **2.****登陆****MySQL****：**

​         在dos命令窗口中输入 mysql -uroot -p密码

​                 [如果不想别人看到密码可以在-p以后敲一下回车]

​             出现了mysql>的话就代表登陆成功了

​    **3.exit****代表退出****MySQL****数据库**

​    **4.****怎么删除****Mysql****比较干净？**

​         （1）用当初的安装程序选择remove选项

​         （2）强行删除C盘下的program file 和program Data（已隐藏）下的MySQL文件夹

---

## 第三部分	MySQL常用的命令

**1.****查询当前使用的是什么数据库**

​         select database();

​    **2.****查看数据库版本**

​         mysql --version[在进入mysql之前进行操作]

​    **3.****创建数据库**

​         create database 数据库名称;

​    **4.****使用数据库**

​         use 数据库名称;

​    **5.****终止一条语句**

​         \c

​    **6.****退出****MySQL**

​         exit

​    **7.****查看当前数据库**

​         show 库名;

​    **8.****使用某数据库**

​         use 库名;

​    **9.****查看当前库中的表**

​         show tables;

​    **10.****查看其它库中的表**

​         show tables from 库名;

​    **11.****查看表结构** 

​         desc 表名;

​    **12.****查看表数据**

​         select * from 表名;

​    **13.****查看表的创建语句****[****创建表的时候的****sql****语句****]**

​         show create table 表名;

​    **14.****查看都有哪些库**

​         show databases;

---

## 第四部分	SQL语句(DQL)

**1.****简单的查询语句（****DQL****）**

​         (1)查询部分字段

​         语法格式：

​             select 字段名1,字段名2,字段名3... from 表名;

​         注：任何一条sql语句以分号结尾，不见分号不执行

​             sql语句不区分大小写（windows不区分，但是linux区分）

​             同时如果数据是int，可以直接用+-*/得出数据，即字段可以参与数学运算，比如

​                 select sal * 12 from emp;| sal * 12 |

​                 给列算出来的字段重名名,用as在后面写新字段[as可以省略]，如果有中文，加单引号

​                 select sal * 12 as yearsal from emp;| yearsal |

​             sql语句中，字符串需要用单引号括起来

​             在sql语句中如果有null参与数学运算，结果直接为null，用sum等函数时不需要再用isnull()方法了，因为他们已经忽略了null

​         举例：[从员工信息表中获取员工编号和名字]

​             mysql> select ENAME,EMPNO from emp;

​                     +--------+-------+

​                     | ENAME | EMPNO |

​                     +--------+-------+

​                     | SMITH | 7369 |

​                     | ALLEN | 7499 |

​                     +--------+-------+

​         (2)查询所有字段

​         语法格式：

​             select * from 表名;

​             实际开发不建议使用*，因为需要将*转换为各种字段，效率较低，自己写着看可以使用

​    **2.****条件查询（****DQL****）**

​    语法格式：

​         select 字段,字段 from 表名 where 条件;

​    执行顺序：

​         先from 再where 最后select

​    举例：[sql中的等号不是==，而是=]

​         查询工资等于5000的员工姓名

​             select ename from emp where sal = 5000;

​                         +-------+

​                         | ename |

​                         +-------+

​                         | KING |

​                         +-------+

​         查询SMITH的工资

​             select sal from emp where ename = 'SMITH';

​                         +--------+

​                         | sal  |

​                         +--------+

​                         | 800.00 |

​                         +--------+

​    运算符号：

​         等于 =       大于 >       小于 <       大于等于 >=       小于等于 <=       不等于 <> 或者 !=      

且 and 或者 & 或者 &&     或 or 或者 ||

​         闭区间 between and(数据需要左小右大，数字和字符串[首字母]都可以用)，等价于 >= and <=

​         查null（0 和 null是不同的,在数据库中null不是一个值，代表为空，什么也没有，不能用=来衡量） is null

​         查不是null is not null

​         在这几个值中 in [作用和or一致，只不过语法不同 where sal in (1000,5000)表示薪水是1000或者5000的]

​         不在这几个值中 not in

​         

​         注：and和or同时出现时，and的优先级会比or高，因此搞不清楚优先级就加括号

​    **3.****模糊查询****like****（****DQL****）**

​         （1）模糊查询中有两个特殊符号，%和_

​                 %代表任意多个字符

​                 _代表任意一个字符

​         （2）举例：

​             找出名字中含有o的:

​                 select ename from emp where ename like '%o%';

​                         +-------+

​                         | ename |

​                         +-------+

​                         | JONES |

​                         | SCOTT |

​                         | FORD |

​                         +-------+

​             找出第二个字母是a的：

​                 select ename from emp where ename like '_a%';

​                         +--------+

​                         | ename |

​                         +--------+

​                         | WARD  |

​                         | MARTIN |

​                         | JAMES |

​                         +--------+

​             注：要找有下划线或者百分号的数据可以用转义字符\_和\%来搜索

​    **4.****数据排序（升序、降序）**

​             语法格式：

​                 select     第三步

​                     字段,字段...

​                 from         第一步

​                     表名

​                 where         第二步

​                     条件

​                 order by   第四步

​                     字段;

​                 

​             注：默认是升序排列

​                 指定时，asc[ascend]表示升序，sesc[descend]表示降序,将asc/desc写在最后

​                 要指定多个排序条件时，用逗号隔开，越靠近前面的字段，发挥排序的作用越大，后面的字段可能没有用，比如这个是先按薪资降序，如果薪资同，就按照姓名升序

​                     select ename,sal from emp order by sal desc,ename asc;

​                 可以用数字代表列来排序 order by 1是指按照第一列数据排序，但是一旦列的顺序换了就废了，所以可以自己写着用，不建议开发的时候写

​             举例：将员工按照薪资排列

​                 select ename,sal from emp order by sal;

​                 +--------+---------+

​                 | ename | sal   |

​                 +--------+---------+

​                 | SMITH | 800.00 |

​                 …

​                 | KING  | 5000.00 |

​                 +--------+---------+

​                 

​                 找出是SALESMAN的员工并按照薪资降序排序

​                 select ename,sal,job from emp where job = 'SALESMAN' order by sal desc;

​                 +--------+---------+----------+

​                 | ename | sal   | job   |

​                 +--------+---------+----------+

​                 | ALLEN | 1600.00 | SALESMAN |

​                 | TURNER | 1500.00 | SALESMAN |

​                 | WARD  | 1250.00 | SALESMAN |

​                 | MARTIN | 1250.00 | SALESMAN |

​                 +--------+---------+----------+

​    **5.****分组函数（多行处理函数）**

​         （1）常见函数关键字

​                 count 计数                 sum  求和                avg     平均值              

max  最大值              min  最小值

​         （2）函数使用方法

​                 sum 、max、min、avg、count

​                 语法：select sum 、max、min、avg、count(字段) from 表名;

​                 举例：找出工资总和

​                     select sum(sal) from emp;

​                     +----------+

​                     | sum(sal) |

​                     +----------+

​                     | 29025.00 |

​                     +----------+

​         （3）多行处理函数的特点与使用

​                 特点：输入多行，最终输出一行

​                 也即一次处理多行数据，最终输出一行的数据结果

​         （4）单行处理函数

​                 特点：输入一行，输出一行，一次只处理一行数据，也只输出一行数据

​                 ifnull()空处理函数

​                     语法：

​                         ifnull(可能为null的数据字段,被当做什么数据处理)

​                     举例：计算每个员工的年薪并降序处理

​                     select ename,(sal + ifnull(comm,0)) as yearsal from emp order by yearsal desc;

​                     +--------+----------+

​                     | ename | yearsal |

​                     +--------+----------+

​                     | KING  | 60000.00 |

​                     …

​                     | SMITH | 9600.00 |

​                     +--------+----------+

​         （5）count(*)和count(某个字段)的区别

​                 count(*)   统计的是总记录条数，和字段没有关系

​                 count(字段)    统计的是字段中不为空的数据总数

​         注：所有的分组函数都是对某一组数据进行操作的

​                 分组函数只有以上5个

​                 分组函数自动忽略null

​                 5个分组函数不可以直接使用在where子句中

​                     原因是：group by语句是在where后才执行的

​                 分组函数可以在一行里多次使用

​    **6.****分组查询**

​         (1)group by 和 having

​             group by 是按照某个字段或者某些字段进行分组

​             having 是对分组之后的数据进行再次过滤

​         (2)group by

​             语法格式：

​                 select 

​                     字段

​                 from

​                     表名

​                 group by  

​                     字段;

​             举例：找出每个工作岗位的最好工资

​             select max(sal),job from emp group by job;

​             +----------+-----------+

​             | max(sal) | job    |

​             +----------+-----------+

​             | 3000.00 | ANALYST  |

​             | 1300.00 | CLERK   |

​             | 2975.00 | MANAGER  |

​             | 5000.00 | PRESIDENT |

​             | 1600.00 | SALESMAN |

​             +----------+-----------+

​             

​             找出工资高于平均工资的员工

​             第一步：

​                 找出平均工资

​                     select avg(sal) from emp;

​                     +-------------+

​                     | avg(sal)  |

​                     +-------------+

​                     | 2073.214286 |

​                     +-------------+

​             第二步：

​                 找出高于平均工资的员工

​                     select sal,ename from emp where sal > 2073.214286;

​                     +---------+-------+

​                     | sal   | ename |

​                     +---------+-------+

​                     | 2975.00 | JONES |

​                     …

​                     | 3000.00 | FORD |

​                     +---------+-------+

​             拼接以后：[select语句中嵌套select语句]

​                 select sal,ename from emp where sal > (select avg(sal) from emp);

​                     +---------+-------+

​                     | sal   | ename |

​                     +---------+-------+

​                     | 2975.00 | JONES |

​                     …

​                     | 3000.00 | FORD |

​                     +---------+-------+

​             注：group by 一般都会和分组函数联合使用，这也是叫做分组函数的原因

​                     且所有的5个分组函数都是在group by语句执行结束后才执行的

​                 当一个sql语句没有group by的话，整张表的数据会自成一组，系统会自带一个缺省的group by

​                 当一个sql语句中有group by，那么该语句中select后面只能有参加分组的字段以及分组函数，如果出现其他的字段，就会报错

​         (3)多个字段联合分组

​                 语法格式:

​                     select

​                         字段

​                     from

​                         表名

​                     group by

​                         字段1,字段2...

​                 举例：

​                     找出不同部门的不同职位的最高工资

​                      select job,max(sal),deptno from emp group by job,deptno order by deptno desc;

​                     +-----------+----------+--------+

​                     | job    | max(sal) | deptno |

​                     +-----------+----------+--------+

​                     | MANAGER  | 2850.00 |   30 |

​                     …

​                     | CLERK   | 1300.00 |   10 |

​                     +-----------+----------+--------+

​         (4)having与where的选择

​             having用于group by以后的过滤

​             相当于在group by以后加一个where条件限制

​             举例：找出各部门的最高薪资，并显示薪资大于2900的数据

​             示例一：having 对分完组以后的数据进行再过滤

​                 select max(sal),deptno from emp group by deptno having max(sal) > 2900;

​                 //这种方式的效率比较低，建议用示例二

​                 +----------+--------+

​                 | max(sal) | deptno |

​                 +----------+--------+

​                 | 5000.00 |   10 |

​                 | 3000.00 |   20 |

​                 +----------+--------+

​             示例二：where先把不符合条件的数据剔除

​                 select max(sal),deptno from emp where sal > 2900 group by deptno;

​                 //效率较高，能用where解决的就使用where解决，如果where搞不定，那就必须使用having再处理

​                 +----------+--------+

​                 | max(sal) | deptno |

​                 +----------+--------+

​                 | 5000.00 |   10 |

​                 | 3000.00 |   20 |

​                 +----------+--------+

​             注：原数据过滤用where，计算过后的数据用having

​                 having是group by的搭档，只有出现了group by，才能用having，没有group by是无法使用having的

​    **7.****总结****DQL****语句**

​         完整的DQL语句格式，书写和执行顺序都不能发生改变

​         select     第五步

​             ..

​         from     第一步

​             ..

​         where        第二步

​             ..

​         group by  第三步

​             ..

​         having        第四步

​             ..

​         order by   第六步

​             ..

​         limit     第七步

​             ..        

​    **8.****关于查询结果集的去重****[****去除重复记录****]**

​         语法结构：

​             select distinct 字段 from 表名;

​             即在要查询的字段前面加上distinct关键字

​         注：distinct只能出现在所有字段的最前面，否则字段获取的数据可能不同就无法显示了

​             distinct如果后面有多个字段，是去除所有这些字段都相同的数据

​         举例：

​             统计岗位的数量

​             select count(distinct job) from emp;

​                 +---------------------+

​                 | count(distinct job) |

​                 +---------------------+

​                 |          5 |

​                 +---------------------+

​    **9.****连接查询**

​         （1）什么是连接查询

​             在实际开发中都是从多表联合查询，取出最终的结果。

​             一般一个业务会对应多张表，如果只使用一张表，那么就会造成数据的冗余

​         （2）连接查询的分类

​             根据语法出现的年代划分

​                 SQL92

​                 SQL99（较新的语法）

​             根据表的连接方式划分

​                 内连接

​                     等值连接

​                     非等值连接

​                     自连接

​                 外连接

​                     左外连接（左连接）[左边的表是主表]

​                     右外连接（右连接）[右边的表是主表]

​                         左右连接是可以相互转换的，左（右）连接有对应的右（左）连接的写法

​                 全连接（很少用）

​                 注：外连接和内连接的区别

​                          内连接是凡是A表和B表能够匹配上的记录查询出来，匹配补上就不查了，这就是内连接

​                              AB两个表是没有主副之分的

​                         外连接是AB表中有一张表是主表，另一个是副表，主要查询主表内容，附带查询副表

​                              当副表中的数据没有和主表数据匹配上，副表自动模拟出null与之匹配

​         （3）笛卡尔积现象（笛卡尔乘积现象）

​                 当两张表进行连接查询的时候，如果没有任何条件进行限制，最终的查询结果条数是两张表记录条数的乘积

​             举例理解：

​                 select ename,dname from emp,dept;

​                 +--------+------------+

​                 | ename | dname   |

​                 +--------+------------+

​                 | SMITH | ACCOUNTING |

​                     …

​                 | MILLER | OPERATIONS |

​                 +--------+------------+

​                 这里会有56条数据，因为我们没有指定哪些数据不要，因此会出现类似矩阵相乘的笛卡尔乘积现象 

​             如何避免笛卡尔积现象？

​                 加条件进行过滤（即使加了过滤条件，也不会减少记录匹配的次数，只是显示的是有效记录）

​                 这个条件就是两个表之间的联系

​             举例：[用以上的例子举例][以下是SQL92语法，基本不怎么用]

​                 select e.ename,d.dname from emp e,dept d where e.deptno = d.deptno;

​                 +--------+------------+

​                 | ename | dname   |

​                 +--------+------------+

​                  | CLARK | ACCOUNTING |

​                     …

​                 | JAMES | SALES   |

​                 +--------+------------+

​         （4）表的别名

​             可以在表的后面加一个空格后加一个名称，这样可以用表的别名.表中字段来访问字段

​             举例：

​                 select e.ename,d.dname from emp e,dept d;

​             表的别名的好处：

​                 执行效率高

​                 可读性好

​                 防止出现不同表但是同字段的情况

​             以后都要写表别名

​         （5）连接查询分类详解

​         

​             内连接之等值连接

​                 特点：条件是等量关系

​                 案例：上面的e.deptno = d.deptno;

​                 SQL语句语法[SQL99]：

​                     select

​                         e.ename,d.dname

​                     from

​                         emp e

​                     join

​                         detp d

​                     on

​                         e.deptno = d.deptno;

​                         

​                  ...

​                     表A

​                 (inner)join     这个join前面省略了一个inner，inner可以省略，代表是内连接，如果带上可读性会更好 

​                     表B

​                 on

​                     连接条件

​                 where

​                     ...

​                 好处在于99的语法可以做到表连接的条件和筛选过滤的where条件被用on和where分离了

​                     而92的语法则是将两个柔和在一起，结构不清晰

​             

​             内连接之非等值连接

​                 特点：连接条件中的关系是非等量关系

​                 案例：找出每个员工的工资等级，要求显示员工名和工资和工资等级

​                     select

​                          e.ename,e.sal,s.grade

​                     from

​                         emp e

​                     inner join

​                         salgrade s

​                     on

​                         e.sal between s.losal and hisal;

​                     

​                     +--------+---------+-------+

​                     | ename | sal   | grade |

​                     +--------+---------+-------+

​                     | SMITH | 800.00 |   1 |

​                     …

​                     | MILLER | 1300.00 |   2 |

​                     +--------+---------+-------+

​             

​             内连接之自连接[条件既可以是等量，也可以不等量]

​                 特点：一张表看做两张表，自己连接自己

​                 案例：找出每个员工的上级领导，要求显示员工名和对应的领导名

​                     select e1.ename as '员工',e2.ename as '上级' from emp e1 join emp e2 on e1.mgr = e2.empno;

​                     +--------+-------+

​                     | 员工  | 上级 |

​                     +--------+-------+

​                     | SMITH | FORD |

​                     …

​                     | MILLER | CLARK |

​                     +--------+-------+         

​             

​             外连接[外连接使用比内连接的多]

​                 特点:表中有一张表是主表，另一个是副表，主要查询主表内容，附带查询副表

​                              当副表中的数据没有和主表数据匹配上，副表自动模拟出null与之匹配

​                              主表数据无条件全部查询出来

​                 案例:找出每个员工的上级领导

​                     语法：

​                         假如以左边为主表，那么就把内连接的join改为left join

​                         假如以右边为主表，那么就把内连接的join改为right join

​                     //左连接

​                     select

​                         e1.ename '员工',e2.ename '上级'

​                     from 

​                         emp e1

​                     left (outer)join    //这个outer可以省略，如果不省略的可读性就会好一些

​                         emp e2

​                     on

​                         e1.mgr = e2.empno;

​                         

​                     //右连接

​                     select

​                         e1.ename,e2.ename

​                     from 

​                         emp e2

​                     right join

​                         emp e1

​                     on

​                         e1.mgr = e2.empno;

​                     +--------+-------+

​                     | 员工  | 上级 |

​                     +--------+-------+

​                     | SMITH | FORD |

​                     …

​                     | MILLER | CLARK |

​                     +--------+-------+

​         （5）三张以上表的连接查询

​             案例：找出每个员工的部门名称和工资等级和上级领导

​                 

​                 select 

​                     e.ename '员工',d.dname'部门',s.grade'薪资等级',e1.ename'上级'

​                 from

​                     emp e

​                 join

​                     dept d

​                 on

​                     e.deptno = d.deptno

​                 join

​                     salgrade s

​                 on

​                     e.sal between s.losal and s.hisal

​                 left join

​                     emp e1

​                 on

​                     e.mgr = e1.empno

​                 order by

​                     grade;

​                 +--------+------------+----------+-------+

​                 | 员工  | 部门    | 薪资等级 | 上级 |

​                 +--------+------------+----------+-------+

​                 | JAMES | SALES   |    1 | BLAKE |

​                 …

​                 | KING  | ACCOUNTING |    5 | NULL |

​                 +--------+------------+----------+-------+

​                 

​    **10****、子查询**

​         （1）什么是子查询？

​                 select语句中嵌套select语句，被嵌套的select语句叫子查询

​             子查询可以出现在那里？

​                 where后面

​                 select后面

​                 from后面

​         （2）where子句中使用子查询

​             案例：找出高于平均薪资的员工

​                 select sal,ename from emp where sal > (select avg(sal) from emp);

​         （3）from后面使用子查询

​             案例：找出每个部门平均薪水的薪资等级

​                 select s.grade,t.deptno,t.avgsal 

​                     from salgrade s

​                 join 

​                     (select avg(sal) as avgsal,deptno from emp) t 

​                 on

​                     t.avgsal between s.losal and s.hisal;

​                 +-------+--------+-------------+

​                 | grade | deptno | avgsal   |

​                 +-------+--------+-------------+

​                 |   4 |   20 | 2073.214286 |

​                 +-------+--------+-------------+

​         （4）select后面使用子查询

​             案例：找出每个员工所在的部门名称，要求显示员工名和部门名

​                 select e.ename,(select d.dname from dept d where e.deptno = d.deptno) as dname from emp e;

​                 +--------+------------+

​                 | ename | dname   |

​                 +--------+------------+

​                 | SMITH | RESEARCH  |

​                     …

​                 | MILLER | ACCOUNTING |

​                 +--------+------------+

​    **11.union[****可以将查询结果集相加****]**

​         特点：基本等同于in 和 or 但是特别是可以将两张不相干的表中数据拼接在一起显示

​         语法格式：

​             select

​             union

​             select

​         举例：

​             select ename from emp

​             union

​             select deptno from dept;

​             +--------+

​             | ename |

​             +--------+

​             | SMITH |

​             …

​             | MILLER |

​             | 10   |

​             | 20   |

​             | 30   |

​             | 40   |

​             +--------+

​         注：只显示上面一个的查询字段名

​             上下查询的字段的列数应该相同，否则无法拼接

​    **12.limit**

​         （1）limit是mysql中特有的，其他数据库中并没有，不通用（Oracle中有一个相同的机制叫rownum）

​         （2）limit取结果集中的部分数据

​         （3）语法机制：

​             limit startIndex,length

​                 startIndex 表示起始位置,0表示第一个数据

​                 length 表示取几个

​         （4）案例：取出工资前五名

​             select sal,ename from emp order by sal desc limit 0,5;

​             +---------+-------+

​             | sal   | ename |

​             +---------+-------+

​             | 5000.00 | KING |

​             | 3000.00 | SCOTT |

​             | 3000.00 | FORD |

​             | 2975.00 | JONES |

​             | 2850.00 | BLAKE |

​             +---------+-------+

​         （5）注：如果limit后面只有一个数字n，那么指的是去数据中的前n个

​                 limit是SQL语句最后执行的一个环节

​         （6）通用的标准分页SQL

​             limit (pageNo - 1) * pageSize,pageSize

---

## 第五部分	SQL语句(DDL,DML)

**1.****创建表**

​         （1）建表语句的语法格式

​                 create table 表名 (字段名1 数据类型,字段名2 数据类型 ...);

​                     表名在数据库中一般建议以：t_或者tbl_开始

​                 注：建表的时候可以在字段的数据类型后面加上default 数据 来给数据指定默认值，如果没写的话默认值就是null

 

​         （2）关于MySQL中的字段的数据类型[常见]

​                 int   (java中的int)

​                 bigint 长整型(java中的long)

​                 float (java中的float)

​                 double    (java中的double)

​                 char 定长字符串(java中的String)

​                 varchar   可变字符串(最多255个字符)(java中的StringBuffer)

​                 date 日期(对应java中的java.sql.Date类型)

​                 BLOB    二进制大对象(存储图片、视频等流媒体信息)[Binary Large Object]

​                 CLOB    字符大对象(存储大文本，可以存储4G的字符串)[Character Large Object]

​             

​             char和varchar怎么选择？

​                 在实际的开发中，当某个字段中的数据长度不发生改变即定长时（比如性别、生日），采用char

​                 当一个字段的长度不确定（比如简介，姓名）采用varchar，可以自动识别后确定长度，效率没有char高

​                 注：char和varchar在定义时都是有括号的，括号里代表了最长的字符数，如果超了就报错,char(n),varchar(n)

​             

​             BLOB和CLOB类型的使用？

​                 他们只能使用java中的io流才能加入到数据库中

​         （3）举例：创建一个学生表，信息包括学号，姓名，性别，班级编号，生日

​                 create table t_STUDENT (no bigint,name varchar(255),sex char(1),classno varchar(255),birth char(10);

​                 查看表结构

​                 desc t_student;

​    **2.****向表中插入数据**

​         （1）语法格式：

​                 insert into 表名(字段名1,字段名2...) values(值1,值2..)

​                 要求：字段的数量和值的数量相同且数据类型要对应相同

​         （2）举例：

​                 insert into t_student(no,name,sex,classno,birth) values(35,'fengchuiyusan','1','1918','1111-11-11');

​                 [

​                 select * from t_student;

​                 +------+---------------+------+---------+------------+

​                 | no  | name     | sex | classno | birth   |

​                 +------+---------------+------+---------+------------+

​                 |  35 | fengchuiyusan | 1  | 1918  | 1111-11-11 |

​                 +------+---------------+------+---------+------------+

​                  ]

​                 注：可以只插入一个字段，其他没有数据的字段会自动成为null

​         （3）注意：

​                 当一条insert语句执行成功以后，表格中一定会多一行记录，即使多的这一行记录中某些字段为null，后期也无法执行insert进行更新，只能使用update更新

​                 insert into后面的字段是可以省略的，但前提是后面的value需要数量以及顺序都与原表格中的一致，不能少

​         （4）一次插入多行数据

​                 insert into t_student values(),(),()....;

​    **3.****删除表**

​         语法格式:

​             drop table if exists t_student;(如果存在这个表，就删除)[MySQL可以用，Oracle不支持]

​             drop table 表名;[都支持]

​    **4.****表的复制**

​         （1）语法格式:

​                 create table 表名 as select语句;

​                 即将查询结果作为表创建出来

​         （2）举例：

​                 create table t_student2 as select * from t_student;

​    **5.****将查询结果插入到一张表中**

​         语法格式：

​             insert into 表名 select 语句

​         注：需要满足表的结构有一致型，例如字段数应该相同

​    **6.****修改表中数据**

​         （1）语法格式：

​             update 表名 set 字段名1=值1,字段名2=值2... where 条件

​             注：没有where条件整张表的数据全部更新

​         （2）案例：

​             将学号是35的学生的1918班级改为1915

​                 update t_student set classno='1915' where no = 35;

​                 +------+---------------+------+---------+------------+

​                 | no  | name     | sex | classno | birth   |

​                 +------+---------------+------+---------+------------+

​                 |  35 | fengchuiyusan | 1  | 1915  | 1111-11-11 |

​                 +------+---------------+------+---------+------------+

​    **7.****删除数据**

​         （1）语法格式：

​                 delete from 表名 where 条件

​             注：没有where条件时整张表的数据全部删除

​         （2）怎么删除大数据量的表格中的数据[表未被删除]？

​                 

​                 注：这个方法删除就再也找不到数据了，危险性较高

​                     truncate table 表名;

​                         表被截断，不可回滚，数据永久丢失

​    **8.****表结构的修改**

​         由于这种对表结构的修改出现的情况很是少见，因此在这里就不详细写了，使用工具即可

​         出现在java代码中的sql包括增删改查 insert delete update select（都是对表中的数据增删改查）

​             增删改查有一个术语叫做CRUD[create retrieve[检索] update delete]

---

## 第六部分	约束

**1.****什么是约束？常见的约束是那些？**

​         约束是创建表的时候可以保证表中数据的合法性，有效性，完整性等

​         常见的约束：

​             非空约束 not null        约束的字段不能为null

​             唯一约束 unique            约束的字段不能重复

​             主键约束 primary key    约束的字段既不能为null，也不能重复[简称PK]

​             外键约束 foreign key [简称FK]

​             检查约束 check         

​             注：Oracle数据库有检查约束但是目前mysql不支持，mysql没有检查约束

​    **2.****非空约束** **not null**

​         （1）语法格式：

​                 create table 表名(字段 数据类型 not null);

​             代表着再用insert语句进行数据的插入的时候不能将这个字段的数据值赋值为null，一定要有除了null的值

​         （2）举例：

​                 drop table if exists t_user;

​                 create table t_user(id int not null);

​                 insert into t_user(id) values(35 );

​                 //这个表的属性：id是不允许为null的，所以显示no

​                 +-------+---------+------+-----+---------+-------+

​                 | Field | Type  | Null | Key | Default | Extra |

​                 +-------+---------+------+-----+---------+-------+

​                 | id  | int(11) | NO  |   | NULL  |    |

​                 +-------+---------+------+-----+---------+-------+

​             注：not null只有列级约束，没有表级约束，只能加载字段后面

​    **3.****唯一性约束**

​         （1）唯一性约束修饰的字段具有唯一性，不能重复但是可以为null，可以有多个null

​                 null不是值，不同的null是不同的

​         （2）举例：给某一列添加unique，此时id不能相等[列级约束]

​                 drop table if exists t_user;

​                 create table t_user(id int unique);

​                 insert into t_user(id) values(null);

​                 insert into t_user(id) values(null);

​                 

​                 +------+

​                 | id  |

​                 +------+

​                 | NULL |

​                 | NULL |

​                 +------+

​         （3）举例：给两个列或多列添加unique,此时age和id不能都相等[表级约束]

​                 drop table if exists t_user;

​                 create table t_user(id int,age int,unique(id,age));

​                 insert into t_user(id,age) values(35,53);

​                 insert into t_user(id,age) values(35,35);

​                 注：注意unique前面的逗号

​                     列级约束可以转换成表级约束

​                 +------+------+

​                 | id  | age |

​                 +------+------+

​                 |  35 |  35 |

​                 |  35 |  53 |

​                 +------+------+

​    **4.****主键约束**

​         （1）怎么给一张表添加主键约束？

​                 drop table if exists t_user;

​                 create table t_user(id int primary key,username varchar(255),email varchar(255));

​                 insert into t_user(id,username,email) values(3,'syqh','0');

​         （2）主键约束语法：

​                 字段 数据类型 primary key,  这个是列级约束

​             主键字段中的数据不能为null，也不能重复

​             一个表的主键约束只能有一个

​         （3）主键相关的术语

​                 主键约束 primary key

​                 主键字段 上例为id

​                 主键值       上例为3

​         （4）主键有什么用?

​                 表的设计三范式中有要求，第一范式就要求任何表都应该有主键

​                 主键的作用是

​                     主键值是这行记录在这张表中的唯一标识，就像一个人的身份证一样

​         （5）主键的分类

​             根据主键字段的字段数量分类

​                 单一主键[推荐使用且常用]

​                 复合主键(多个字段联合添加一个主键约束)[不建议使用，违背三范式]

​             根据主键的性质划分

​                 自然主键(主键值最好就是一个和业务没有任何关系的自然数)[推荐使用]

​                 业务主键(主键值和系统的业务挂钩)[不建议使用，最好不用和业务挂钩的字段做主键]

​         （6）使用表级约束定义主键

​             语法格式：

​                 字段 数据类型，字段 数据类型，primary key(字段)

​             复合主键的语法格式：

​                 primary key(字段1，字段2...)

​         （7）mysql提供主键值自增

​             语法格式：

​                 字段 int primary key auto_increment,

​             举例：

​                 id int primary key auto_increment,

​                 指的是id字段自动维护一个自增的数字，从1开始，以1递增

​             注：Oracle中也提供了一个自增机制，叫做：序列(sequence)对象

​    **5.****外键约束**

​         （1）外键约束的相关术语

​                 外键约束[foreign key]

​                 外键字段[添加有外键约束的字段]

​                 外键值[外键字段的每一个值]

​         （2）什么是外键约束

​             当表A的某个字段引用了表B的某个字段，此时A字段的数据只能是B字段中的内容，也即内容受限制，如果

​                 数据不是B字段中的内容，就会报错，此时表A叫做子表，表B叫做父表

​             注：操作顺序要求：

​                 创建表时先创建父表，再创建子表

​                 删除表时先删除子表，再创建父表

​                 添加数据的时候，先添加父表，再添加子表

​                 删除数据的时候，先删除子表，再删除父表

​         （3）外键约束的语法格式

​                 foreign key(子表字段名) references 父表名(父表字段名)

​         （4）其他外键知识

​                 外键可以为null

​                 外键字段引用别的表的字段时，被引用的字段必须有唯一性，一般都是主键，不一定是主键

---

## 第七部分	存储引擎

**1.****不同的存储引擎决定了底层存储表数据时采用了不同的存储方式**

​         创建表的时候如果没有指定，存储引擎默认innoDB，字符集默认UTF8

​    **2.****完整的建表语句**

​         CREATE TABLE `test` (

​          `id` int(11) DEFAULT NULL

​         ) ENGINE=InnoDB DEFAULT CHARSET=utf8;

​         注：在mysql中，凡是标识符是可以用飘号```括起来的，不过最好别用，因为只能在mysql中使用

​             建表的时候可以指定存储引擎，也可以指定字符集

​                 存储引擎默认innoDB，字符集默认UTF8

​    **3.****什么是存储引擎？**

​         只有在mysql中存在存储引擎，Oracle中有对应的机制，但是不叫存储引擎，直接叫存储方式

​         mysql支持很多存储引擎，每个存储引擎都对应了一种不同的存储方式，各有优缺点，需要合理选择

​    **4.****查看当前****mysql****支持的存储引擎（共****9****个）**

​         show engines \G     

​                 

​    **5.****常见的存储引擎**

​         （1）    Engine: MyISAM

​                  Support: YES

​                  Comment: MyISAM storage engine

​             Transactions: NO

​                      XA: NO

​              Savepoints: NO

​             

​             MyISAM这种搜索引擎不支持事务，它是mysql中最常用的存储引擎，但不是默认的

​             它的表管理有以下特征：

​                 使用三个文件表示每个表

​                     格式文件 存储表结构的定义[后缀frm]

​                     数据文件 存储表内容[后缀MYD]

​                     索引文件 存储表索引[后缀MYI]

​             可以转换为压缩、只读表来节省空间

​             （2）Engine: InnoDB

​                  Support: DEFAULT

​                  Comment: Supports transactions, row-level locking, and foreign keys

​             Transactions: YES

​                      XA: YES

​              Savepoints: YES

​              

​              每个表以.frm文件存储表示

​              数据存储在tablespace这样的表空间中（逻辑概念），无法被压缩，无法被转换成只读

​             优点：支持事务、行级锁、外键等

​                  这种存储引擎最为安全

​                  在mysql数据库崩溃后提供自动恢复机制

​                  支持级联删除和级联更新

​             缺点：数据存在与表空间中，无法压缩

​                 （3）Engine: MEMORY

​                  Support: YES

​                  Comment: Hash based, stored in memory, useful for temporary tables

​             Transactions: NO

​                      XA: NO

​              Savepoints: NO

​              

​              以前叫做HEPA引擎

​              缺点：不支持事务，数据容易丢失，因为所有数据和索引是存储在内存中

​                     不能存储CLOB和BLOB字段

​              优点：查询速度最快，适合查询

---

## 第八部分	事务

**1.****事务概述**

​         （1）什么是事务

​             一个事务是一个完整的业务逻辑单元，不可再分。

​             比如银行账户转账，A向B转账1000，那么需要执行两条update语句

​                 update t_act set balance = balance - 1000 where actno = 'act01';

​                 update t_act set balance = balance + 1000 where actno = 'act02';

​             以上DML语句需要同时成功或失败，不能一个成功，一个失败，为了达到这种要求，就需要使用事务机制

​         （2）只有DML才支持事务，和事务相关的语句只有DML(insert delete update)，因为他们都是和数据库中的表数据相关的

​                 事务是为了保证数据的完整与安全才存在的

​             假设所有的业务都可以用一条DML语句解决，那么就不需要事务机制了，但是这是不可能的

​         （3）事务的原理

​             事务开始以后，所有的DML语句都依次放到了历史操作(缓存)中，之后事务结束的时候可以提交事务和回滚事务

​                 提交事务[commit]是将历史操作全部执行后再清空历史操作，保证全部执行

​                 回滚事务[rollback]是将历史操作全部清空但不执行，保证全不执行

​             事务可以设置设置回滚点，也就是可以将回滚的位置一下，不全部回滚，类似于游戏里的实时存档

​         （4）事务的四大特性 ACID

​                 A：原子性

​                     事务是最小的工作单元，不可再分

​                 C：一致性

​                     事务必须保证多条DML语句同时成功或者失败

​                 I：隔离性

​                     事务A和B之间具有隔离

​                 D：持久性

​                     最终数据必须持久化到硬盘文件中，事务才算成功的结束

​         （5）事务的隔离性

​             事务之间的隔离性存在隔离级别，理论上隔离级别包括4个

​                 第一级别：读未提交[read uncommitted]

​                     对方未提交的数据我们当前事务可以读到，隔离性低

​                     存在脏读[dirty read]现象，表示读到了脏的数据（数据是不稳定的）

​                 第二级别：读已提交[read committed]

​                     对方提交的数据我们可以读到

​                     解决了脏读现象

​                     存在的问题：不可重复读取（读到相同的数据叫做重复读取）

​                 第三级别：可重复读[repeatable read]

​                     这种隔离级别解决了不可重复读的问题，它无法读取提交后的数据，只能读取事务刚开始时的数据

​                         因此数据是一个固定的情况

​                     存在的问题：读取到的数据是幻象

​                 第四级别：序列化读（串行化读）

​                     解决了所有问题，但是效率低，需要事务排队

​                 

​                 Oracle默认是第二级别，mysql默认是第三级别

​         （6）演示事务

​             mysql下事务是默认自动提交的

​                 只要执行任意一条DML语句，就会提交一次

​             怎么关闭自动提交？

​                 start transaction;

​             举例：

​                 drop table if exists t_user;

​                 create table t_user(

​                     id int primary key auto_increment,

​                     username varchar(255)

​                     );

​                 

​                 insert t_user(username) values('syqh');

​                 //此时是自动提交事务，即使用rollback回滚，此时数据已经写入了文件，回不去了

​                 //使用start transaction 关闭自动提交机制

​                 start transaction;

​                 insert t_user(username) values('qhmm');

​                 //此时是有两条数据

​                 rollback;

​                  //此时只有一条数据，并且事务已经结束了，要再重新关闭自动提交事务

​                 

​                 start transaction;

​                 insert t_user(username) values('yzm');

​                 select * from t_user;

​                 //此时有两条数据

​                 commit;

​                 select * from t_user;

​                 //此时还是两条数据

​         （7）mysql可以用一个账户开两个dos窗口登陆两个位置

​             设置全局隔离事务级别

​                 set global transaction isolation level 英文(read uncommitted);

​             查看全局隔离级别

​                 select @@global.tx_isolation;

---

## 第九部分	索引

**1.****什么是索引？索引有什么用？**

​         索引相当于一本书的目录，通过目录可以快速的找到对应的资源，索引是添加给字段的

​         在数据库中查询一张表的时候有两种方式

​             第一种：全表扫描

​             第二种：根据索引检索（效率很高）

​                 效率很高的原理是缩小了扫描的范围

​         索引虽然可以提高检索效率，但是不可以随意添加，因为索引也是数据库的对象，数据改变后需要不断维护，有维护成本

​         举例：

​             select ename,sal from emp where ename = 'SMITH';

​          如果ename没有索引，那么就会进行对ename全表扫描，直到找到'SMITH'这个值

​          如果ename有索引，那么就会根据索引进行扫描，快速定位

​    **2.****怎么创建索引对象？怎么删除索引对象？**

​         创建：create index 索引名 on 表名(字段名);

​         删除：drop index 索引名 on 表名;

​    **3.****什么时候给字段添加索引？**

​         数据量庞大（根据客户的需求，根据线上的环境）

​         该字段中的数据很少的DML操作，增删改很少（因为字段进行修改，索引需要维护）

​         该字段经常出现在where子句中（经常根据哪个字段查询）

​    **4.****注意：主键和具有****unique****约束的字段会自动添加索引**

​         因此根据主键查询效率较高，尽量根据主键检索

​    **5.explain sql****语句****;****可以看出执行该语句的整体逻辑和步骤**

​         这个只有在mysql中才有，别的数据库中没有

​         举例：

​         explain select sal,ename from emp where sal = 5000;

​         +----+-------------+-------+------+---------------+------+---------+------+------+-------------+

​         | id | select_type | table | type | possible_keys | key | key_len | ref | rows | Extra    |

​         +----+-------------+-------+------+---------------+------+---------+------+------+-------------+

​         | 1 | SIMPLE   | emp  | ALL | NULL     | NULL | NULL  | NULL |  14 | Using where |

​         +----+-------------+-------+------+---------------+------+---------+------+------+-------------+

​                                    全表扫描

​         字段加索引语法格式

​         create index 索引名 on 表名(字段名);

​          

​         给sal字段加入索引

​         create index emp_sal_index on emp(sal);

​         explain select sal,ename from emp where sal = 5000;

​         +----+-------------+-------+------+---------------+---------------+---------+-------+------+-------------+

​         | id | select_type | table | type | possible_keys | key      | key_len | ref  | rows | Extra    |

​         +----+-------------+-------+------+---------------+---------------+---------+-------+------+-------------+

​         | 1 | SIMPLE   | emp  | ref | emp_sal_index | emp_sal_index | 9    | const |  1 | Using where |

​         +----+-------------+-------+------+---------------+---------------+---------+-------+------+-------------+

​    **6.****索引的实现原理**

​         索引底层的数据结构是 B + Tree

​         表中每一行数据都会有一个物理地址，在mysql中没有名字就叫物理地址，但是在Oracle中就叫做rowid

​         

​         通过B Tree缩小了扫描的范围，底层索引进行了排序、分区，索引会携带数据在表中的物理地址

​             最终通过索引检索到数据以后，获得了关联的物理地址，通过物理地址定位到了表中的数据，这样的效率最高

​             select ename from emp where ename = 'SMITH';

​             通过索引转换为：

​             select ename from emp where 物理地址 = 0x111111111;

​    **7.****索引的分类**

​         单一索引 给单个字段添加索引

​         复合索引 给多个字段联合添加一个索引

​         主键索引 主键上会自动添加索引

​         唯一索引 有unique约束的字段上会自动添加索引

​    **8.****索引什么时候失效？**

​         模糊查询时如果第一个是%时索引会失效，因此使用模糊查询时会降低效率

---

## 第十部分	视图(view)

**1.****什么是视图？**

​         站在不同的角度去看待数据，同一张表的数据，通过不同的角度去看待

​    **2.****怎么创建和删除视图？**

​         创建视图：

​             create view 视图名 as select 字段1,字段2... from 表名;

​         删除视图：

​             drop view 视图名;

​         注：只有DQL语句才可以以视图对象的形式创建出来，但是可以对视图CRUD

​    **3.****对视图进行增删改查会影响到原表数据，通过视图影响数据，不是直接操作原表数据**

​    **4.****面向视图操作**

​         create view myview as select ename,sal from emp;

​         //创建视图对象

​         select * from myview;

​         //面向视图操作，查询视图

​                      +--------+---------+

​                     | ename | sal   |

​                     +--------+---------+

​                     | SMITH | 800.00 |

​                     …

​                     | MILLER | 1300.00 |

​                     +--------+---------+

​         update myview set ename = '水原千鹤',sal = 12000 where ename = 'SMITH';

​         //通过视图就更改了原表的数据

​    5.视图有什么用？

​        视图可以隐藏表的实现细节，保密级别比较高的系统可能只对外提供相关的视图，java程序员只对视图对象进行CRUD

​         视图是很少用的，视图不会提高检索效率

---

## 第十一部分	DBA命令

**1.****将数据库中的数据导出**

​         在Windows的dos命令窗口中执行;

​             mysqldump 数据库名称>路径和文件(D:\sjfsagjsag.sql) -u用户名 -p密码

​             导出整个库

​             mysqldump 表名>路径和文件(D:\sjfsagjsag.sql) -u用户名 -p密码

​             导出一个表

​    **2.****将数据库中的数据导入**

​         先创建出一个库

​             create database 库名;

​             use 库名;

​         再导入数据

​             source 将文件拖过来;

---

## 第十二部分	数据库设计三范式

**1.****什么是设计范式？**

​         设计表的依据

​         按照这个三范式设计出的表不会出现数据冗余

​    **2.****三范式都是哪些？**

​         第一范式：任何一张表都应该有主键，并且每一个字段原子性不可再分

​         第二范式：所有非主键字段完全依赖主键，不能产生部分依赖

​             多对多时出现了部分依赖以后，解决方法:

​             三张表，关系表两个外键

​             举例：

​             t_student学生表

​             sno(pk)       sname

​             1            张三

​             2            李四

​             3            王五

​             

​             t_teacher讲师表

​             tno(pk)        tname

​             1            张老师

​             2            李老师

​             3            王老师

​             

​             t_student_teacher_relation 关系表

​             id(pk)        sno(fk)            tno(fk)

​             1            1                3

​             2            1                1

​             3            2                2

​             4            2                3

​             5            3                1

​             6            3                3

​         第三范式：所有的非主键字段直接依赖主键，不能产生传递依赖

​             一对多时出现了传递依赖，解决方法：

​             两张表，多的表加外键

​             举例：

​             班级 t_class

​             cno(pk)       cname

​             1            班级1

​             2            班级2

​             学生 t_student

​             sno(pk)       sname        classno(fk)

​             101          张1          1

​             102          张2          1

​             103          张3          2

​             104          张4          2

​             105          张5          2

​    

​    注：在实际的开发中，以满足客户的需求为主，有时会拿冗余换执行速度

​         表越是连接，查询速度就会慢，因为这是笛卡尔积

​    **3.****一对一怎么设计？**

​         两种方案：

​             **主键共享**：将一个表的主键作为另一个表的外键，从而那个表的主键和外键共享

​             **外键唯一**：一个表将另一个表的主键单独列出并用unique约束