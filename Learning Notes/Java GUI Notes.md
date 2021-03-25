# Java GUI Notes

## 前言

组件包括:

​         窗口,弹窗,面板,文本框,列表框,按钮,图片,监听事件,鼠标,键盘事件,破解工具

​    简介:

​         GUI(用户图形界面)的核心技术:

 Swing AWT,但是不流行,因为界面不美观,同时又因为必须有JRE

​         学习的原因:

​         了解MVC架构,了解监听器

---

## 第一部分 AWT

\1.   AWT介绍

a)AWT(abstract window tools)包含许多的类和接口,可以new出很多实例化的类

b)AWT中含有许多的元素,包括按钮,窗口,文本框等等

c)位于java.awt包里,有两个重要的部分:

​     组件(component) : 基本组件不是光new出来就行了,还需要放到容器(container)里才能显示

基本组件[可以直接使用]:按钮(button),文本域(TextArea),标签(label)…

​             容器[存放组件]:窗口(window)[分为窗口(frame)和弹窗(dialog)],面板(panel)[分为小程序(applet)]

\2.   AWT中的类的使用

a)    Frame对象的使用(此时右上角的关闭按钮不起作用,关闭窗口只能停止java程序)

​    //先new出一个frame对象,其中的title代表了窗口的标题

![img](file:///C:/Users/FENGCH~1/AppData/Local/Temp/msohtmlclip1/01/clip_image002.jpg)    Frame frame = new Frame("My first frame!");

​    //需要设置可见性才能看到这个窗口

​    frame.setVisible(true);

​    //再为这个窗口设置大小

​    frame.setSize(400,400); 

​    //设置背景颜色

​    Color color = new Color(127, 63, 63); 

​    frame.setBackground(color);

​    //弹出的初始位置

​    frame.setLocation(200,200);

​      //设置弹窗大小固定

​    frame.setResizable(false);

b)    Panel对象的使用(窗口只有一个,而面板可以有多个,因此我们经常把东西都写在面板里)

​    //panel面板可以看成是一个空间,但是不能单独存在,必须放在Frame上

![img](file:///C:/Users/FENGCH~1/AppData/Local/Temp/msohtmlclip1/01/clip_image004.jpg)    Frame f1 = new Frame();

​    //panel里面有布局的概念

​    Panel p1 = new Panel();

​    //设置布局,如果没有这句话,panel会直接占满整个frame

​    f1.setLayout(null);

​    //先设置frame的位置和颜色

​    f1.setBounds(300,300,500,500);

​    f1.setBackground(new Color(40,160,35));

​    //panel去设置坐标,但是其坐标是相对frame的,不是相对屏幕左上角的

​    p1.setBounds(50,50,400,400);

​    //设置panel的颜色

​    p1.setBackground(new Color(190,15,60));

​    //将panel放到frame里面去

​    f1.add(p1);

​    //设置可见性为true

​    f1.setVisible(true); 

c)    ![img](file:///C:/Users/FENGCH~1/AppData/Local/Temp/msohtmlclip1/01/clip_image006.jpg)利用监听事件监听窗口关闭事件,使得右上角的关闭键起作用

//f1.addWindowListener(new WindowListener());

f1.addWindowListener(new WindowAdapter() {

  //窗口关闭时要做的事情

  @Override

  public void windowClosing(WindowEvent e) {

​    System.exit(0);

  }

})

\3.   三种布局管理器

a)    流式布局:从左到右结构

//流式布局

Frame f = new Frame();

![img](file:///C:/Users/FENGCH~1/AppData/Local/Temp/msohtmlclip1/01/clip_image008.gif)//组件-按钮

Button bn1 = new Button("b

Button bn2 = new Button("b

//设置frame的布局是流式布局并让按钮靠左对齐

f.setLayout(new FlowLayout

f.setSize(200,200);

f.setVisible(true);

//将按钮添加到frame中

f.add(bn1);

f.add(bn2);

 

b)    东南西北中:上下结构

//东西南北中

Frame f = new Frame();

//组件-按钮                                      

![img](file:///C:/Users/FENGCH~1/AppData/Local/Temp/msohtmlclip1/01/clip_image010.gif)Button bn1 = new Button("East");

Button bn2 = new Button("West");

Button bn3 = new Button("South");

Button bn4 = new Button("North");

Button bn5 = new Button("Center");

f.setSize(200,200);

f.setVisible(true);

//将按钮以东西南北中的形式添加到frame中

f.add(bn1,BorderLayout.EAST);

f.add(bn2,BorderLayout.WEST);

f.add(bn3,BorderLayout.SOUTH);

f.add(bn4,BorderLayout.NORTH);

f.add(bn5,BorderLayout.CENTER);

c)    网格布局;类似三行两列的结构

f.setSize(200,200);

![img](file:///C:/Users/FENGCH~1/AppData/Local/Temp/msohtmlclip1/01/clip_image012.gif)f.setVisible(true);

//设置frame的行列数和行列距

f.setLayout(new GridLayout(3,2));

//将按钮放入其中

f.add(bn1);

f.add(bn2);

f.add(bn3);

f.add(bn4);

f.add(bn5);

f.add(bn6);

​      d)  注:java中自带一个frame.pack()方法,它可以自动智能的为你选择最优的布局方式

​             众多复杂的布局都是由着三种布局嵌套组合而成的,嵌套一般是由面板嵌套实现的,不论是面板,还是按钮还是一系列的

​             他们都继承了completent类,因此其实都是一种东西,因此可以相互嵌套

\4.   总结(1)

a)    Frame是一个顶级窗口

b)    Panel无法单独显示,必须添加到某个容器当中

c)    三个布局管理器

d)    大小定位颜色可见性等一系列属性

e)    监听初步

\5.   事件监听

定义: 当某个事情发生的时候,干某件事情

a)    举例:按钮的事件监听

Frame f = new Frame();

![img](file:///C:/Users/FENGCH~1/AppData/Local/Temp/msohtmlclip1/01/clip_image014.gif)//按下按钮的时候触发事件

Button btn = new Button("btn1");

//按钮也会有listener

//因为addActionListener需要一个ActionListener

//所以我们构造一个ActionListener,而其是接口,故需要写

//它的实现类

btn.addActionListener(new MyActionListener());

//将button放到frame上

f.add(btn);

f.setVisible(true);

f.setBounds(200,200,500,500);

CloseWindow.closeWindow(f);

 

class MyActionListener implements ActionListener{

  @Override

  public void actionPerformed(ActionEvent e) {

​    System.out.println("aaa");

  }

}

注: ActionEvent e 有以下有关的方法

(1)  e.getActionCommand()

获得按钮的信息,可以在按钮中用setActionCommand()来设置自定义信息,也可以不设置默认输出按钮的名称

通过这样的方式,可以通过按钮的信息比对在监听类的重载方法里不停的if else,从而可以多个按钮只写一个监听类

b)    输入框的事件监听

![img](file:///C:/Users/FENGCH~1/AppData/Local/Temp/msohtmlclip1/01/clip_image016.gif)    Frame f = new Frame();

​    f.setVisible(true);

​    f.setBounds(200,200,50,50); 

​    //输入框的监听事件

​    //new出一个输入框

​    TextField tf = new TextField();

​    //将输入框放到frame里

​    f.add(tf);

​    //监听文本框里输入的东西

​    //按下回车会触发其监听事件

​    tf.addActionListener(new MyActionListener());

​    CloseWindow.closeWindow(f);

  }

}

 

class MyActionListener implements ActionListener{

  @Override

  public void actionPerformed(ActionEvent e) {

​    //e.getSource可以获得一些资源,返回一个Object老祖宗类,

​    //强制转换为TextField

​    TextField tf = (TextField)e.getSource();

​    //输出tf的文本信息,其实以上等价于e.getActionCommand()的作用

​    System.out.println(tf.getText());

//用户输入回车以后清空输入框

tf.setText("");

  }

}

注: textField还有一些常用的方法,例如tf.setEchoChar('*'),此时你输入的东西在输入框里显示的就是*,类似密码保护



 