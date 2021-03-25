# JDBC Notes

**1.JDBC****是什么？**

​         java datebase connectivity （java语言连接数据库）

​    **2.JDBC****的本质是什么？**

​         本质是SUN公司制定的一套接口（interface）

​         接口都有调用者和实现者，我们面向接口调用，面向接口写实现类，这都属于面向接口编程

​             为什么面向接口编程？

​                 解耦合：降低程序的耦合度，提高程序的扩展力

​                 多态就是非常典型的面对抽象编程

​    **3.****为什么要制定一套****JDBC****的接口？**

​         因为每一个数据库底层的实现原理都不一样，Oracle和mysql的原理等都不一致

​         各个数据库厂商都写了一套JDBC的实现类的class文件，我们把他们叫做驱动，所有的数据库驱动只是一个jar包，其中有很多的.class文件

​             驱动不是SUN提供的，是数据库厂商提供的，需要从官网下载

​    **4.JDBC****编程的六步**

​         （1）注册驱动              [告诉Java程序，即将连接的是哪个品牌的数据库]

（2）获取连接              [表示JVM的进程和数据库进程之间的通道打开了，属于进程之间的通信，重量级的，使用完后需要关闭通道]

​             注册驱动：

​                 注册驱动，使用一个静态方法，用类名调用

​               try{

​                     DriverManager.registerDriver(new com.mysql.cj.jdbc.Driver());

​                 }

​                 catch(SQLException e){

​                     e.printStackTrace();

​                 }

​             获取连接：

​                 String url = "jdbc:mysql://127.0.0.1:3306/fushengduobuyu?serverTimezone=UTC";

​                 String user = "root";

​                 String password = "20011024yangshuo";

​                 try{

​                     Connection conn = DriverManager.getConnection(url,user,password);

​                     System.out.println("it is " + conn);

​                 }catch(SQLException e){

​                     e.printStackTrace();

​                 }

​                 

​             url概述：

​                 URL是统一资源定位符（网络中某个资源的固定路径）

​                 URL包括了协议、ip、PORT、资源名等信息

​                     http://182.61.200.7:80/index.html

​                     http://         通信协议

​                     182.61.200.7   服务器ip地址

​                     80           服务器软件端口号

​                     index.html 服务器上某个资源名

​                 

​                 jdbc:mysql://127.0.0.1:3306/fushengduobuyu?serverTimezone=UTC

​                     jdbc:mysql://        协议

​                     127.0.0.1          ip地址

​                     3306             数据库端口号

​                     fushengduobuyu     数据库实例名

​                     ?serverTimezone=UTC    控制时区一致

​                     

​                 注：localhost和127.0.0.1都是本机ip地址

​             什么是通信协议？有什么用？

​                 通信协议是通信之前就提前订好的数据传输格式

​         （3）获取此处导包也可以数据库操作对象     [专门执行SQL语句的对象]

​             try{

​                 Statement stmt = conn.createStatement();

​                 //Statement对象可以将sql语句发送到数据库中

​             }catch(SQLException e){

​                 e.printStackTrack();

​             }

​         （4）执行sql语句           [主要执行DQL和DML]

​             String sql = "insert into dept(deptno,dname,loc) values(50,'HR','SH')";

​             int count = stmt.executeUpdate(sql);

​             //专门执行DML语句的（insert delete update ），返回值是影响数据库中的记录条数

​             System.out.println(count == 1 ? "true" : "false");

​         （5）处理查询结果集             [只有当第四步执行的是select语句时，才有第五的处理查询结果集]

​         （6）释放资源              [使用完资源以后一定要关闭资源]

​                 由于抛出的异常都是一致的，所以我们都在一个try catch中写代码，为了保证资源一定释放，我们一般

​                     在finally语句块中关闭资源，并遵循从小到大依次关闭（先stmt，再conn），分别对其try catch

​         (7)在mysql中如果第一次和第二次执行的代码完全一样,那么就会只执行一次的编译,第二次的时候就不会再编译而直接执行了

​    **5.JDBC****完成****insert****的代码**

​    import java.sql.*;

public class codes{

​    public static void main(String[] args){

​         try{

​             DriverManager.registerDriver(new com.mysql.cj.jdbc.Driver());

​             String url = "jdbc:mysql://127.0.0.1:3306/fushengduobuyu?serverTimezone=UTC";

​             String user = "root";

​             String password = "20011024yangshuo";

​             Connection conn = DriverManager.getConnection(url,user,password);

​             System.out.println("it is" + conn);

​             Statement stmt = conn.createStatement();

​             String sql = "insert into dept(deptno,dname,loc) values(50,'HR','SH')";

​             int count = stmt.executeUpdate(sql);

​             System.out.println(count == 1 ? "true" : "false");

​         }

​         catch(SQLException e){

​             e.printStackTrace();

​         }

​    }

}  

 

​    **6.JDBC****完成****delete****或者****update****的代码**

​    

​    import java.sql.*;

public class codes{

​    public static void main(String[] args){

​         Connection conn = null;

​         Statement stmt = null;

​         try{

​             //注册驱动

​             DriverManager.registerDriver(new com.mysql.cj.jdbc.Driver());

​             //获取链接

​             String url = "jdbc:mysql://127.0.0.1:3306/fushengduobuyu?serverTimezone=UTC";

​             String user = "root";

​             String password = "20011024yangshuo";

​             conn = DriverManager.getConnection(url,user,password);

​             //获取数据库操作对象

​             stmt = conn.createStatement();

​             //执行SQL语句

​             String sql = "delete from dept where deptno = 50";

​             //此处可以改成update/insert语句

​             int count = stmt.executeUpdate(sql);

​             System.out.println(count == 1 ? "true" : "false");

​         }catch(SQLException e){

​             e.printStackTrace();

​         }finally{           //释放资源

​             if(conn != null){

​                 try{

​                     conn.close();

​                 }catch(SQLException e){

​                     e.printStackTrace();

​                 }

​             }

​             if(stmt != null){

​                 try{

​                     conn.close();

​                 }catch(SQLException e){

​                     e.printStackTrace();

​                 }}}}} 

 

​    注:JDBC中的sql语句不需要写分号结尾

​    

​    **7.****注册驱动的另一种方式****(****常用****)**

​         注册驱动的第一种写法:

​             DriverManager.registerDriver(new com.mysql.cj.jdbc.Driver());

​         注册驱动的第二种写法:(常用,因为可以写到配置文件中)

​             Class.forName("com.mysql.jdbc.Driver");

​         

​         注:第一种写法的代码是这个类中的静态代码块,因此可以通过反射机制来使得只让这个类的静态代码块执行

​             第二种写法需要抓两个异常,SQLException和ClassNotFoundException

​    **8.****处理查询结果集**

​         (1)遍历查询结果集

​             int executeUpdate用于insert delete update,ResultSet executeQuery用于select

​             resultSet中有一个方法是next();如果此时有数据,那么光标会下移一格并且返回true

​             

​             while(rs.next()){

​                 String empno = rs.getString(1);

​                 //String方法的特点是不论数据库中的数据是什么类型,都会以String的形式取出

​                 //参数中的数字是下标,代表的是第几列,在JDBC中所有的下标都是从1开始,不是从零开始

​                 //但是这个数字可以用最终查询语句中的字段中的名字代替,建议不用数字,可以增强健壮性,

​                 //注:这个列名称不是表中的列名称,而是查询结果集中的列名称

​                 String ename = rs.getString("ename");

​                 String sal = rs.getString(3);

​                 System.out.println(empno + ename + sal + "\n");

​             }

​             

​             想要使用double或者int等类型取出数据时可以用getInt,getDouble 等方法

​         (2)JDBC完成delect的代码

​         [int executeUpdate用于insert delete update,ResultSet executeQuery用于select]

​         import java.sql.*;

public class codes{

​    public static void main(String[] args){

​         Connection conn = null;

​         Statement stmt = null;

​         ResultSet rs = null;

​         //多了这个结果集

​         try{

​             //注册驱动

​             DriverManager.registerDriver(new com.mysql.cj.jdbc.Driver());

​             //获取链接

​             String url = "jdbc:mysql://127.0.0.1:3306/fushengduobuyu?serverTimezone=UTC";

​             String user = "root";

​             String password = "20011024yangshuo";

​             conn = DriverManager.getConnection(url,user,password);

​             //获取数据库操作对象

​             stmt = conn.createStatement();

​             //执行SQL语句中的DQL

​             String sql = "select sal,ename,empno from emp";

​             //此处使用select语句,下面要改成executeQuery,返回resultSet对象

​             rs = stmt.executeQuery(sql);

​             //处理查询结果集

​             while(rs.next()){

​                 String empno = rs.getString("empno");

​                 //String方法的特点是不论数据库中的数据是什么类型,都会以String的形式取出

​                 //参数中的数字是下标,代表的是第几列,在JDBC中所有的下标都是从1开始,不是从零开始

​                 String ename = rs.getString("ename");

​                 String sal = rs.getString("sal");

​             System.out.println(empno + ename + sal + "\n");

​         }

​         }catch(Exception e){

​             e.printStackTrace();

​         }finally{           

​             //释放资源

​             if(rs != null){

​                 try{

​                     rs.close();

​                 }catch(SQLException e){

​                     e.printStackTrace();

​                 }

​             }

​             if(conn != null){

​                 try{

​                     conn.close();

​                 }catch(SQLException e){

​                     e.printStackTrace();

​                 }

​             }

​             if(stmt != null){

​                 try{

​                     stmt.close();

​                 }catch(SQLException e){

​                     e.printStackTrace();

​         }}}}}

​    **9.SQL****注入现象****(****黑客经常使用****)**

​      使用一个随便输入的账号加上密码格式为[账号' or '1'='1]   会出现登陆成功

​      **导致****SQL****注入的原因****:**

用户输入的信息中含有SQL语句的关键字,并且这些关键字参与了SQL语句的编译过程,导致SQL语句的原意被扭曲,进而达到sql注入

​      **怎么解决****sql****注入****:**

​        只要用户提供的信息不参与SQL语句的编译过程,问题就解决了

​        要想用户信息不参与sql语句的编译,那么必须使用java.sql.PreparedStatement这个接口继承了Statement

​          它是属于预编译的数据库操作对象,它的原理是预先对SQL语句的框架进行预编译,然后再给SQL语句传值

​      改动方式:

​      (1)将

​        Statement stmt = null;

​        改为

​        PreparedStatement ps = null;

​      (2)在第三步获取预编译的数据库操作对象

​            String sql = "里面单引号所扩住的输入值变成问号?[?是占位符,一个?将来接受一个值,不能写成'?',整个SQL语句只是一个框架]"

​        ps = conn.prepareStatement(sql);

​        //假设SQL语句中有两个占位符,接下来给占位符传值,那么第n个问号下标为n,JDBC中下标从1开始

​        ps.setString(1,loginName);

​        ps.setString(2,password);

​        //同样有setInt等方法

​      (3)在第四步执行SQL时

​        rs = ps.executeQuery();

  **10.Statement****和****PreparedStatement****的对比**

​    (1)前者有SQL注入问题,后者解决了这个问题

​    (2)前者编译一次执行一次,后者编译一次执行n次,后者的效率较高

​    (3)后者会在编译阶段做类型的安全检查,传的数值不符合就会直接就会标红

​    后者使用较多,只有少数的时候需要前者

​    什么时候必须用前者呢?

​      业务需要必须支持SQL注入的时候,需要将用户的数据拼接到SQL语句中的时候.

​      比如让用户自己选择时升序还是降序的时候 desc还是asc的时候

  **11.****用****PreparedStatement****实现数据的增删改**

​    (1)增数据

​          String sql = "insert into dept(deptno,dname,loc) values(?,?,?)";

​          ps = conn.prepareStatement(sql);

​          ps.setInt(1,60);

​          ps.setString(2,"sales");

​          ps.setString(3,"sh");

​    (2)改数据

​          String sql = "update dept set dname = ?, loc = ? where deptno = ?";

​          ps = conn.prepareStatement(sql);

​          ps.setString(1,"HR");

​          ps.setString(2,"Shanghai");

​          ps.setInt(3,60);

​    (3)删数据

​          String sql = "delete from dept where deptno = ?";

​          ps = conn.prepareStatement(sql);

​          ps.setInt(1,60);

  **12.jdbc****的事务机制**

​    (1)JDBC中的事务是自动提交的

​      只要执行任意一条DML语句,就自动提交一次,这是JDBC默认的事务行为,但实际业务中,都是多条DML语句共同联合才能完成

​        需要保证这些DML语句在同一个事务中同时成功或者同时失败

​    (2)更改为手动提交

​      第一步:在获取连接后,获取数据库操作对象前要使用

​        conn.setAutoCommit(false);

​        来开启事务自动提交机制

​      第二步:在事务的最后一个SQL语句后使用

​        conn.commit();

​        来提交事务

​      第三步:在catch语句块中使用

​        if(conn != null){

​          conn.rollback();}

​        来回滚事务

​    注:工具类中的构造方法一般都是私有的

  **13.JDBC****的行级锁**

​    **悲观锁****(****行级锁****):**

​      在select语句后面加一个 for update以后,查出来的数据将会整行都被锁定,直到本事务结束

​        前都不可以被修改,也即事务必须排队执行,数据被锁住了,不允许并发

​    **乐观锁****:**

​      支持并发,事务也不需要排队,但是需要一个行数据的版本号,事务在执行前后都会读取一下行数据的

​        版本号,每次数据改动都会使得版本号递增,当行数据的版本号执行前后不一致时,事务不会提交

​        会发生回滚