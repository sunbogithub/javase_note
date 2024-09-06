java是95年sun公司推出的高级语言，09年被oracle公司收购，java之父是詹姆斯高斯林。

java源文件经过编译成class文件，再通过jvm解释执行
解释执行是指：一行一行地编译，一行编译完就立即执行
编译执行是指：一次编译全部代码，保存编译结果，每次执行的对象都是第一次的编译结果
java执行的过程，既有解释执行，又有编译执行
jdk全称java开发工具包，包括jre运行时环境和开发工具，jre包括jvm虚拟机和核心类库。
java的跨平台原理：一次编译，处处执行，只要os安装了对应的jvm即可运行
jdk需要配置JAVA_HOME和Path环境变量，分别是jdk的根目录和bin目录。
验证jdk配置成功，java -version和javac -version。

idea的下载、安装
    学生可以申请旗舰版免费使用，b站黑马程序员JavaSE和JavaEE教程都使用的是2021.1.1旗舰版，安装只需勾选64bit快捷方式即可

JavaSE项目的搭建
    首先创建一个名为Java的空项目，接着在里面添加名为JavaSE的模块即可创建基本框架，之后在src下新建包，使用公司域名倒写，再在包下创建类

idea快捷键
ctrl+R 替换
ctrl+alt+L 格式化代码
ctrl+alt+T 包围代码
ctrl+alt+V 自动补全
alt+shift+↑ 移动代码
shift+enter 换行
alt+enter 快速处理强制类型转换

```java
//单行注释
/*多行注释*/
/**文档注释，最后可以提取为注释文档 */
```

字面量就是指数据在程序中应该怎么书写。包括整数、小数、字符、字符串、布尔值、空值
二进制、八进制、十六进制的字面量分别以0b、0、0x开头来表示

类名命名规则：DataFactory
方法命名规则：getDataFactory()
变量命名规则：dataFactory
包名一般全小写

变量里的数据在计算机中都是以二进制存储的，且是补码，底层运算的操作对象也是补码。

字符编码方式：ascii、gbk（中文字符占2个字节，数字和英文字符占1个字节）、utf-8（中文字符占3个字节，数字和英文字符占1个字节）等
编码就是把字符变为字节，解码就是把字节变为字符

数据类型：整型（byte,short,int,long）、布尔类型(boolean)、字符(char)、浮点型(float,double)、引用类型，其中byte能表示的数据范围为-128-127
变量的类型：变量包括成员变量（全局变量）和局部变量，其中成员变量包括实例变量和类变量

自动类型转换：byte----->short----->int----->long----->float----->double
                 						char 
表达式的自动类型转换：在表达式中，小类型会自动转为大类型再进行运算，最终结果的类型是其中最高的数据类型，byte、short、char直接转换成int再参与运算
byte，short，char----->int----->long----->float----->double

逻辑运算符： & | ！ ^ 	 短路与&&  	 短路或||
&&的优先级大于||
三元运算符： (59>60) ? "及格" : "不及格"
==在比较基本类型时比较对象是值，在比较引用类型时比较对象是地址

switch的穿透：其中某几个case不写break
switch里的表达式的类型可以为 byte,short,int,char,String,枚举，不支持float,double,long
case只能是字面量，不能是变量

```java
int[] a =  {1,2,3,4}; //数组静态初始化 
int[] a = new int[]{1, 2, 4};//数组静态初始化 
int[] a = new int[3]; //数组动态初始化 
//动态初始化会有一个默认值
byte,short,char,int,long的默认值是0
boolean是false
float,double是0.0
引用类型是null
//注意
''java里没有这种写法，也不代表空字符，空字符用'\0'
""代表空字符串
' '代表空格字符
" "代表空格字符串
    
int i = 0;
System.out.println((char) i);
char c = '0';
System.out.println((int) c);//  字符'0'的ascii码为48
System.out.println((int) '\0');
System.out.println('\0');//空字符'\0'的ascii码为0
// System.out.println('');
System.out.println((int)' ');//空格字符' '的ascii是32

int[] a = null;//没有在堆中开辟空间
int[] b ={};//已经在堆中开辟空间，但是没有元素
System.out.println(b);//[I@776ec8df
System.out.println(b.length);//0
System.out.println(Arrays.toString(b));//[]
System.out.println(a);//null
System.out.println(Arrays.toString(a));//null

String s = "helloworld";
System.out.println(s.toCharArray());//helloworld
System.out.println(s.toCharArray().toString());//[C@776ec8df
```

字节码文件是提取到jvm中执行的，jvm内存区域划分：方法区、栈、堆；字节码文件放在方法区，方法和局部变量放在栈，new出来的东西和字符串常量池放在堆，对象的实例变量和类变量放在堆

方法传参都是值传递，对于基本类型传的是副本，对于引用类型传的是地址
方法签名：由方法名称和方法的形参列表（形参类型和形参顺序、个数）共同组成，不包括方法的返回值类型和访问修饰符
方法重写的要求：方法名称和方法的形参列表相同，即方法签名一样
方法重载的要求：方法名称相同，形参列表（形参类型和形参顺序、个数）不同

面向对象：开发一个个的对象，把数据交给对象，再调用对象的方法来完成对数据的处理。

this的用途
    this代表当前对象
    用在构造方法中，解决变量名称冲突
    在一个构造方法中调用另一个构造方法

构造器
    默认会为类提供一个无参构造器，若自己提供了有参构造器，则不再提供默认的无参构造器

封装：用类设计对象处理某一个事物的数据时，应该把要处理的数据，以及处理这些数据的方法，设计到一个对象中去。封装的设计规范：合理隐藏，合理暴露。实体类JavaBean包括成员变量、getset方法、有参构造器和无参构造器。实体类仅仅是用来存取数据的类。

String是不可变对象
    每次试图改变字符串对象实际上是产生了新的字符串对象
    变量每次都是指向了新的字符串对象
    之前字符串对象的内容确实是没有改变的
字符串常量池
    放在堆中
    只要是"..."给出来的字符串都放在常量池中

```java
//字符串创建方式一
String s1 = new String();
//字符串创建方式二
String s2 = new String("abc");
//字符串创建方式三
byte[] b = {97, 98, 99};
String s3 = new String(b);
//字符串创建方式四
char[] c = {'a', 'b', 'c'};
String s4 = new String(c);
//字符串创建方式五
String s5 = "abc";
//这行代码创建了2个String对象
String s = new String("abc");
//这两行代码创建了3个String对象
String s1 = "123";
s1+="456";
//其中"123"和"456"放在堆的常量池中，"123456"放在堆的非常量池中
String s2 = "red" + "blue";//创建了3个字符串对象放到字符串常量池中
String s3 = "redblue";
//这里由于编译优化机制，s2和s3指向同一个对象
```

![image-20240830203126422](C:\Users\sunbo\AppData\Roaming\Typora\typora-user-images\image-20240830203126422.png)

static的注意事项
	类变量最好用public修饰，代表对外完全公开暴露
	类变量放在堆内存中，属于类，对象没有该成员，但是可以访问
	类方法可以直接访问类成员（变量和方法），不可以直接访问实例成员（变量和方法）
    实例方法可以直接访问类成员（变量和方法），也可以直接访问实例成员（变量和方法）
    实例方法中可以出现this，类方法中不可以出现this
	静态代码块只在类加载时执行一次，用来初始化类变量。
	实例代码块在每次使用构造器创建对象之前执行，用来初始化实例变量。

```java
//单例设计模式，懒汉式
public class A {
    //定义一个类变量记住类对象
    private static A a;
    //构造方法私有
    private A() {
    }
    //获取方法
    public static A getInstance() {
        if (a == null) {
            a = new A();
        }
        return a;
    }
}
//单例设计模式，饿汉式
public class B {
    //定义一个类变量记住类对象
    private static B b = new B();
    //构造方法私有
    private B() {
    }
    //获取方法
    public static B getSingleInstance() {
        return b;
    }
}
```

继承
    使用继承的好处，提取子类公共的代码到父类中
    类只能单继承，但可以多层继承
    子类只能继承父类的非私有成员（继承指的是在子类中可以直接用）
    子类的对象是由子类和父类这两张设计图共同创建完成的
	子类的对象只能直接访问子类和父类对外暴露的那些成员
	子类构造器第一行默认都会调用父类的无参构造器（写或者不写），若父类没有无参构造器，则使用super显示调用父类有参构造器
	在任意类的构造器中，都可以通过this去调用该类的其他构造器

```java
public class ExtendsDemp {
    public static void main(String[] args) {
        Student s = new Student("张三", 12, "羽毛球");
        System.out.println(s.getName());
        System.out.println(s.getAge());
        System.out.println(s.getSkill());
    }
}
class Person{
    private String name;
    private int age;
    
    public Person() {
    }
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
class Student extends Person{
    private String skill;
    
    public Student(){
        super();//可以省略，写或者不写
    }

    public Student(String name, int age, String skill) {
        super(name, age);
        this.skill = skill;
    }

    public String getSkill() {
        return skill;
    }

    public void setSkill(String skill) {
        this.skill = skill;
    }
}
```

```java
//在子类方法中访问其他成员（成员变量和成员方法），是按照就近原则的。
public class Test {
    public static void main(String[] args) {
        Zi zi = new Zi();
        zi.showName();
        zi.showMethod();
    }
}

class Fu {
    String name = "父类名字";
    public void pt() {
        System.out.println("父类方法");
    }
}

class Zi extends Fu {
    String name = "子类名字";
    @Override
    public void pt() {
        System.out.println("子类方法");
    }
    public void showName() {
        String name = "局部名字";
        System.out.println(name);//局部名字
        System.out.println(this.name);//子类名字
        System.out.println(super.name);//父类名字
    }
    public void showMethod() {
        pt();//子类方法
        super.pt();//父类方法
    }
}
```

权限修饰符是指类的成员在哪些地方可以被访问
                    						  本类   			同包的其他类    任意包的子类 	任意包的任意类
	private修饰的方法             可以
	缺省修饰的方法    			 可以       			可以
    protected修饰的方法         可以      			 可以        		   可以
	public修饰的方法               可以       			可以        	      可以      			可以    

```java
package com.p1;
public class Fu {
    // 1、私有:只能在本类中访问
    private void privateMethod(){
        System.out.println("==private==");
    }
    // 2、缺省：本类，同一个包下的类
    void method(){
        System.out.println("==缺省==");
    }
    // 3、protected: 本类，同一个包下的类，任意包下的子类
    protected void protectedMethod(){
        System.out.println("==protected==");
    }
    // 4、public： 本类，同一个包下的类，任意包下的子类，任意包下的任意类
    public void publicMethod(){
        System.out.println("==public==");
    }

    public void test(){
        privateMethod();
        method();
        protectedMethod();
        publicMethod();
    }
}

package com.p1;
public class Demo {
    public static void main(String[] args) {
        // 目标：掌握不同权限修饰符的作用。
        Fu f = new Fu();
        // f.privateMethod();
        f.method();
        f.protectedMethod();
        f.publicMethod();
    }
}

package com.p2;
import com.p1.Fu;
public class Zi extends Fu {
    public void test(){
        // privateMethod(); // 报错
        // method(); // 报错
        protectedMethod();
        publicMethod();
    }
}

package com.p2;
import com.p1.Fu;
public class Demo2 {
    public static void main(String[] args) {
        Fu f = new Fu();
        // f.privateMethod(); // 报错
        // f.method();
        // f.protecedMethod();
        f.publicMethod();
        
        Zi zi = new Zi();
        // zi.protectedMethod();
    }
}
```

方法重写
    权限修饰符尽可能变大
    返回值类型尽可能变小
	私有方法和静态方法不能重写，但静态方法可以被继承

多态
    前提：有继承或者实现接口关系，存在父类引用指向子类对象，存在方法重写
    行为多态----------------一种方法对于不同的对象表现不一样
    对象多态----------------一个父类引用可以指向多个子类对象
    对于实例方法 编译看左边运行看右边
    对于成员变量（实例变量和类变量）和类方法 编译运行都看左边
    若想调用子类的独有实例方法 则需要向下转型

```java
public class Test {
    public static void main(String[] args) {
        Fu f = new Zi();
        f.pt();//父类方法，编译看左边，执行看左边
        System.out.println(f.name);//父类名字，编译看左边，执行看左边
        System.out.println(f.age);//12，编译看左边，执行看左边
    }
}

class Fu {
    int age = 12;
    static String name = "父类名字";
    public static void pt() {
        System.out.println("父类方法");
    }
}

class Zi extends Fu {
    int age = 13;
    static String name = "子类1名字";
    //    @Override 静态方法不能重写
    public static void pt() {
        System.out.println("子类1方法");
    }
}
```

final
	使用static和final修饰的成员变量成为常量，即final修饰类变量时，类变量为常量。
	final修饰引用类型变量，其地址是不能改变的，但地址指向的内容是可以改变的
	修饰变量，方法，类   是最终的意思

类的五大成员
    成员变量，方法，构造器，代码块，内部类
	代码块分为静态代码块（类加载时执行一次，对类变量初始化）和实例代码块（创建对象时，且在构造器前执行，对实例变量初始化）
	匿名内部类常用来创建实现类或子类的对象

抽象类是用来被继承的，其中不一定有抽象方法，类该有的五大成员抽象类都可以拥有
抽象类的场景，每个子类继承的行为要求不一样，就把这个行为弄成抽象方法，来更好的支持多态
有抽象方法的类一定是抽象类 

```java
//模板方法设计模式，解决重复代码问题，把相同代码放到模板方法中
public abstract class TemplateMethod{
    //抽象方法
    public abstract void sing();
    //模板方法
    public final void go(){
        System.out.println("开始");
        sing();
        System.out.println("结束");
    }
}
//实现类A
public class A extends TemplateMethod{
    @Override
    public void sing() {
        System.out.println("好久不见");
    }
}
//实现类B
public class B extends TemplateMethod{
    @Override
    public void sing() {
        System.out.println("青花瓷");
    }
}
//测试类
public class Test{
    public static void main(String[] args) {
            new A().go();
            new B().go();
    }
}
```

接口是比抽象类抽象的更加彻底的一种结构，可以单继承、多继承；类可以实现多个接口

```java
//接口，接口里的方法默认都是public
public interface MyInterface {
    int A = 1;//常量 相当于 public static final int A = 1;
    void go();//抽象方法 相当于public abstract void go();
 //    静态方法 相当于 public static void md3(){}
    static void md3(){
        System.out.println("接口静态方法");
    }
//    私有方法
    private void md2(){
        System.out.println("接口私有方法，用来减少重复代码");
    }
//    默认方法可以被实现类继承，可以重写或者不重写，使用实现类的对象访问
    default void md1(){
        System.out.println("接口默认方法");
        md2();
    }
}
//实现类
public class MyInterfaceImp implements MyInterface{
    @Override
    public void go() {
        System.out.println("实现类的go()");
    }

    /*@Override
    public void md1() {
        System.out.println("重写的默认方法");
    }*/
}
//测试类
public class TestMyInterface {
    public static void main(String[] args) {
        MyInterface.md3();//接口名直接调用
        MyInterface myInterfaceImp = new MyInterfaceImp();
        myInterfaceImp.go();
        myInterfaceImp.md1();
    }
}
```

接口其他注意事项（了解）--方法签名包括：方法名和参数列表
1、一个接口继承多个接口，如果多个接口中存在方法签名冲突，则此时不支持多继承。
2、一个类实现多个接口，如果多个接口中存在方法签名冲突，则此时不支持多实现。
3、一个类继承了父类，又同时实现了接口，父类中的方法和接口中的默认方法有相同方法签名，实现类会优先用父类的。

```java
public class Test extends A implements B{
    public static void main(String[] args) {
        Test test = new Test();
        test.go();//a
    }
}
class A {
    public void go(){
        System.out.println("a");
    }
}
interface B {
    default void go() {
        System.out.println("b");
    }
}
```

4、一个类实现多个接口，多个接口中存在相同方法签名的默认方法，可以不冲突，这个类重写该方法即可。

```java
interface MyInterface1 {
    default void md() {
        System.out.println("接口默认方法1");
    }
}

interface MyInterface2 {
    default void md() {
        System.out.println("接口默认方法1");
    }
}

public class Test implements MyInterface1, MyInterface2 {
    public static void main(String[] args) {
        Test test = new Test();
        test.md();//重写的默认方法
    }
    @Override
    public void md() {
        System.out.println("重写的默认方法");
    }
}
```

```java
//枚举是一种特殊的类
//枚举都是最终类，不可以被继承。
public enum A {
    //枚举类的构造器都是私有的（写不写都只能是私有的），因此，枚举类对外不能创建对象。
    //枚举类的第一行只能罗列一些名称，这些名称都是常量，并且每个常量记住的都是枚举类的一个对象。
    X,Y,Z;
    // 枚举类中，从第二行开始，可以定义类的其他各种成员。
}
//相当于  下面这样的结构
public final class A extends java.lang.Enum<A> {
    public static final A X = new A();
    public static final A Y = new A();
    public static final A Z = new A();
    public static A[] values();
    public static A valueof(java.lang.string);
}
//测试类
public static void main(String[] args) {
        A x = A.X;
        System.out.println(x);//X
    //继承java.lang.Enum类的一些方法
        System.out.println(x.name());//X
    	System.out.println(x.ordinal());//0
    //编译器为枚举类新增了几个静态方法
        A[] values = A.values();
        System.out.println(Arrays.toString(values));//[X, Y, Z]
        A y = A.valueOf("Y");
        System.out.println(y);//Y
    }
```

```java
//枚举常用来做信息标志和分类
public enum Constant {
    BOY,GIRL;
}
public class Test {
    public static void main(String[] args) {
        check(Constant.GIRL);
    }
    private static void check(Constant sex) {
        switch (sex){
            case BOY://这里写Constant.BOY反而报错
                System.out.println("男孩");
                break;
            case GIRL:
                System.out.println("女孩");
                break;
        }
    }
}
```

```java
//定义类、接口、方法时，同时声明了类型变量<E>，称为泛型类、接口、方法，统称为泛型，E只支持引用类型
//泛型类
public class ArrayList<E>{...}
//泛型接口
public interface List<E>{...}
//泛型方法
public static <T> T test(T t){
    return t;
}  
//调用泛型方法
String s = test("java")
//它不是泛型方法，而是泛型类里的一个方法，注意区分
public T get(int i){
    return null;
}  
//既不是泛型方法，也不是泛型类里的一个方法，只是一个普通方法，形参是一个泛型类
public void go(ArrayList<String> names){...}
//泛型上下限
<T extends Car> T能接Car或Car的子类
<T super Car>  T能接Car或Car的父类
//泛型通配符，在使用泛型时可以用？代替任意类型
public static void go (ArrayList<? extends Car> cars){}//该方法是一个普通方法，形参是一个泛型类
ArrayList<cars> cars = new ArrayList();
ArrayList<benchi> bcs = new ArrayList();
ArrayList<bwm> bwms = new ArrayList();
go(cars);go(bcs);go(bwms);
```

Object
    equals  默认比较地址，重写比较内容
    toString 默认返回地址，重写返回内容
    hashCode 获取对象的hashCode值	hashCode默认根据地址计算，重写根据内容计算
		String类是不可变对象，重写了Object的equals和hashcode
		ArrayList重写了equals和hashcode，一般在重写equals的时候也要重写hashcode
		StringBuilder是可变对象，没重写Object的equals和hashcode

```java
StringBuilder s1 = new StringBuilder("aa1");
StringBuilder s2 = new StringBuilder("aa").append(1);
System.out.println(s1==s2);//false
System.out.println(s1);//aa1
System.out.println(s2);//aa1
System.out.println(s1.equals(s2));//false
```

​	getClass    获取类对象，进而获取全类名

```java
//获取String的类对象
String s = "asd";
Class aClass = s.getClass();
Class aClass = String.class;
//将类对象转换为字符串
System.out.println(aClass);//class java.lang.String 
```

​    clone 是protected修饰的 当对象调用该方法时，会返回一个一模一样的新对象，原对象和新对象内容一样，地址不一样

```java
//浅克隆，基本类型数据直接拷贝值，引用类型数据拷贝地址
//需要让该类实现Cloneable接口，这个接口是一个标记接口，并且重写Object中的clone
package base.demo1;
public class A implements Cloneable{
    private int id=1;
    private String name="hello";
    private int[] arr={1,2,3};
    @Override
    protected Object clone() throws CloneNotSupportedException {
         A a1 = (A) super.clone();//Object的clone()
        return a1;
    }
    public void pt(){
        System.out.println(id+name+arr);
    }
}
package base.demo1;
public class Test {
    public static void main(String[] args) throws CloneNotSupportedException {
        A a = new A();
        A a1 = (A) a.clone();
        a.pt();//1hello[I@5f184fc6
        a1.pt();//1hello[I@5f184fc6
        System.out.println(a);//base.demo1.A@3feba861
        System.out.println(a1);//base.demo1.A@5b480cf9
    }
}
```

```java
//深克隆，基本类型数据直接拷贝值，String类型数据拷贝地址，其他引用类型数据（比如说数组）不会拷贝地址，会在堆创建新数组
package base.demo1;
public class A implements Cloneable{
    private int id=1;
    private String name="hello";
    private int[] arr={1,2,3};
    @Override
    protected Object clone() throws CloneNotSupportedException {
        A a1 = (A) super.clone();
        a1.arr = a1.arr.clone();
        return a1;
    }
    public void pt(){
        System.out.println(id+name+arr);
    }
}
package base.demo1;
public class Test {
    public static void main(String[] args) throws CloneNotSupportedException {
        A a = new A();
        A a1 = (A) a.clone();
        a.pt();//1hello[I@5f184fc6
        a1.pt();//1hello[I@3feba861
        System.out.println(a);//base.demo1.A@5b480cf9
        System.out.println(a1);//base.demo1.A@6f496d9f
    }
}
```

Objects类

```java
//Objects的equals方法比Object的equals方法更加安全
String s1 = null;
System.out.println(Objects.equals(s1,"123"));//Objects类的equals不会有空指针异常，直接返回false
System.out.println(s1.equals("123"));//Object类的equals会有 NullPointerException
System.out.println(Objects.isNull(s1));
System.out.println(Objects.nonNull(s1));	
```

```java
//字符串和包装类互转
Double d1 = 0.1;
// Double转String
String s = String.valueOf(d1);
// String转Double
Double d2 = Double.valueOf(s);
```

```java
//StringBuilder是可变对象，常用来做拼接，支持链式编程，线程不安全
StringBuilder s = new StringBuilder("begin");
System.out.println(s.append(1).append(1.2).append('a').append(true));//begin11.2atrue
System.out.println(s.reverse());//eurta2.11nigeb
System.out.println(s.length());//14
//StringBuilder转为String
String s1 = s.toString();
System.out.println(s1);//eurta2.11nigeb
//StringBuffer的用法与StringBuilder一模一样，但是线程安全
//StringJoiner，更适合做拼接，速度比StringBuffer和StringBuilder都快
StringJoiner s = new StringJoiner(",", "[", "]");
System.out.println(s.add("hello").add("world").add("java"));//[hello,world,java]，add的参数必须是字符串
System.out.println(s.length());//18
//StringJoiner转为String
String s1 = s.toString();
System.out.println(s1);//[hello,world,java]
```

```java
//Math工具类
System.out.println(Math.abs(-1));//1
System.out.println(Math.ceil(1.1));//2.0
System.out.println(Math.floor(1.1));//1.0
System.out.println(Math.round(1.1));//1
System.out.println(Math.max(1, 2));//2
//返回double值，形参也是double类型
System.out.println(Math.pow(2, 3));//8.0
//返回double随机值，范围[0.0,1.0)
System.out.println(Math.random());//0.1907705675729846
```

```java
//System类
//返回当前系统的时间毫秒值
System.out.println(System.currentTimeMillis());//1714187288456
for (int i = 0; i < 5; i++) {
    System.out.println(i);
    if (i==4) {
        System.out.println(System.currentTimeMillis());//1714187288456
        System.exit(1);//终止当前运行的jvm，非零状态代码表示异常终止
    }
}
```

```java
//Runtime代表程序运行的环境，是一个单例类，构造器是私有的
Runtime runtime = Runtime.getRuntime();
System.out.println(runtime.availableProcessors());//16
runtime.exit(1);//非0表示异常终止
System.out.println(runtime.totalMemory());//257949696
System.out.println(runtime.freeMemory());//254927712
//启动微信程序，返回代表微信程序的对象
Process p = runtime.exec("D:\\ProgramFiles\\Tencent\\WeChat\\WeChat.exe");
Thread.sleep(5000);
p.destroy();//关闭微信
```

```java
//BigDecimal，解决浮点运算结果失真问题
double a = 1.1;
double b = 2.2;
double v = a + b;
System.out.println(v);//3.3000000000000003

BigDecimal a1 = BigDecimal.valueOf(a);//double转成BigDecimal
BigDecimal b1 = BigDecimal.valueOf(b);
BigDecimal v1 = a1.add(b1);//subtract,multiply,divide
System.out.println(v1.toString());//3.3，其实BigDecimal也重写了toString（）

BigDecimal b1 = BigDecimal.valueOf(10.0);
BigDecimal b2 = BigDecimal.valueOf(3.0);
BigDecimal b3 = b1.divide(b2,3, RoundingMode.HALF_UP);//3位小数，四舍五入
double v2 = b3.doubleValue();//BigDecimal转成double
System.out.println(v2);//3.333
```

------

```java
//jdk8之前的日期时间
//Date(可变对象)，代表的是日期和时间
Date d1 = new Date();
d1.setTime(1713425653100L);
System.out.println(d1.getTime());//1713425653100
Date d2 = new Date(1713425653200L);
System.out.println(d2.getTime());//1713425653200
Date d3 = new Date();
System.out.println(d3);//Tue Jul 02 20:29:49 CST 2024
//SimpleDateFormat
public class SimpleDateFormatDemo {
public static void main(String[] args) throws ParseException {
	//将Date对象和时间毫秒值格式化为字符串
	Date d1 = new Date();
	SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
	String s1 = sdf.format(d1);
	System.out.println(s1);//2024-07-02 20:31:48
	String s2 = sdf.format(1713425653200L);
	System.out.println(s2);//2024-04-18 15:34:13
	//将字符串解析为Date对象
	Date date = sdf.parse("2024-04-18 15:34:13");
	System.out.println(date);//Thu Apr 18 15:34:13 CST 2024
    }
}
//Calendar代表系统此刻时间对应的日历(可变对象)
Calendar c = Calendar.getInstance();// Calendar是一个抽象类
Date date = c.getTime();
System.out.println(date);
System.out.println(date.getTime());
System.out.println(c.getTimeInMillis());
System.out.println(c.get(Calendar.YEAR));
System.out.println(c.get(Calendar.DAY_OF_YEAR));
c.set(Calendar.YEAR, 2025);
c.add(Calendar.YEAR, 1);
System.out.println(c.getTime());
```

```java
//jdk8之后的日期时间(不可变对象) -----主要学会LocalDateTime和DateTimeFormatter
//jdk8之后的优点：1.不可变对象 2.线程安全 3.精确到纳秒
//不可变是指，每次修改都生成一个新的对象。可变是指每次修改的都是同一个对象，每次修改会覆盖上一次的记录
//LocalDate,LocalTime,LocalDateTime用来代替Calendar，获取对象都是调用静态方法now或者of
//它们三个都有下列方法：now,getXX,withXX,plusXX,minusXX,of,equals,isBefore,isAfter
//LocalDate（年月日、星期）和LocalTime（时分秒、纳秒）类似
public static void main(String[] args) {
    LocalDate ld = LocalDate.now();
    System.out.println(ld);
    System.out.println(ld.getYear());//年
    System.out.println(ld.getMonthValue());//月
    System.out.println(ld.getDayOfMonth());//日
    System.out.println(ld.getDayOfYear());//一年的第几天
    System.out.println(ld.getDayOfWeek().getValue());//星期几
    LocalDate ld1 = ld.withYear(2025);
    System.out.println(ld1);
    LocalDate ld2 = ld.plusYears(2);
    System.out.println(ld2);
    LocalDate ld3 = ld.minusYears(2);
    System.out.println(ld3);
    LocalDate ld4 = LocalDate.of(2022, 4, 25);
    System.out.println(ld4);
    System.out.println(ld4.equals(ld3));//true,LocalDate重写了equals方法
    System.out.println(ld.isAfter(ld2));//false
    System.out.println(ld.isBefore(ld3));//false
}
//LocalDateTime（年月日、星期、时分秒、纳秒）
public static void main(String[] args) {
        LocalDateTime ldt = LocalDateTime.now();
        System.out.println(ldt);
		//LocalDateTime可以转换为LocalDate
        LocalDate ld = ldt.toLocalDate();
        System.out.println(ld);
    	//LocalDateTime可以转换为LocalTime
        LocalTime lt = ldt.toLocalTime();
        System.out.println(lt);
		//后两个也可以再转回去
        LocalDateTime ldt1 = LocalDateTime.of(ld, lt);
        System.out.println(ldt.equals(ldt1));//true
    }
```

```java
//DateTimeFormatter它是线程安全的，用来代替SimpleDateFormat
//将对象格式化为字符串
DateTimeFormatter formatter = DateTimeFormatter.ofPattern( "yyyy年MM月dd日 - HH时mm分ss秒");
LocalDateTime ldt = LocalDateTime.now();
System.out.println(ldt);
System.out.println(formatter.format(ldt));
//或者（推荐）
System.out.println(ldt.format(formatter));
//将时间字符串解析为对象
String res = "2024年01月23日 - 16时51分58秒";
LocalDateTime ldt1 = LocalDateTime.parse(res,formatter);
System.out.println(ldt1);
```

```java
//拓展知识：ZoneId(时区),ZonedDateTime（带时区的时间，和LocalDateTime的功能几乎一样）
public static void main(String[] args) {
    ZoneId zoneId = ZoneId.systemDefault();
    System.out.println(zoneId);
    Set<String> availableZoneIds = ZoneId.getAvailableZoneIds();
    System.out.println(availableZoneIds);
    ZoneId zoneId1 = ZoneId.of("America/Cuiaba");
    System.out.println(zoneId1);
    ZonedDateTime zonedDateTime = ZonedDateTime.now(zoneId1);
    System.out.println(zonedDateTime);//2024-04-25T04:06:45.727931300-04:00[America/Cuiaba]
    System.out.println(ZonedDateTime.now());//2024-04-25T16:06:45.727931300+08:00[Asia/Shanghai]
}
```

```java
//Instant（时间戳）用来代替Date
System.out.println(LocalDateTime.now().getNano());//437292200
Instant instant = Instant.now();
System.out.println(instant);//2024-08-31T14:47:11.437292200Z
System.out.println(instant.getEpochSecond());//1725115631
System.out.println(instant.getNano());//437292200
```

```java
//Period（年月日间隔）
LocalDate localDate1 = LocalDate.now();
LocalDate localDate2 = localDate1.withYear(2025);
Period period = Period.between(localDate1, localDate2);
System.out.println(period.getYears());
// Duration（时分秒纳秒间隔）
LocalTime localTime1 = LocalTime.of(12, 2, 33);
LocalTime localTime2 = LocalTime.of(13, 3, 31);
Duration duration = Duration.between(localTime1, localTime2);
System.out.println(duration.toHours());
```

------

```java
// 标准的冒泡排序
    public static void main(String[] args) {
        int[] arrs = {2, 72, 1, 4, 5, 223, 52, 521, 22, 12, 34};
        int temp;
        for (int j = 0; j < arrs.length - 1; j++) {
            for (int i = 0; i < arrs.length - 1 - j; i++) {
                if (arrs[i] > arrs[i + 1]) {
                    temp = arrs[i + 1];
                    arrs[i + 1] = arrs[i];
                    arrs[i] = temp;
                }
            }
        }
        System.out.println(Arrays.toString(arrs));
    }
//标准的选择排序
    public static void main(String[] args) {
        int[] arr = {2, 72, 1, 4, 5, 223, 52, 521, 22, 12, 34};
        int minIndex,temp;
        for (int i = 0; i < arr.length-1; i++) {
            minIndex = i;
            for (int j = i+1; j < arr.length; j++) {
                if(arr[j]<arr[minIndex]){
                    minIndex = j;
                }
            }
            if (minIndex!=i) {
                temp = arr[minIndex];
                arr[minIndex] = arr[i];
                arr[i] = temp;
            }
        }
        System.out.println(Arrays.toString(arr));
    }
//标准快速排序，写法一，推荐
public class QuickSort {
    public static void main(String[] args) {
        int[] arrs = {5, 2, 9, 1, 5, 6};
        System.out.println(Arrays.toString(arrs));
        quickSort(arrs, 0, arrs.length - 1);
        System.out.println(Arrays.toString(arrs));
    }

    public static void quickSort(int[] arr, int begin, int end) {
        if (begin < end) {
            int left = begin;
            int right = end;
            int base = arr[left];
            while (left < right) {
                while (left < right && arr[right] >= base) {
                    right--;
                }
                if (left < right) {
                    arr[left++] = arr[right];
                }
                while (left < right && arr[left] <= base) {
                    left++;
                }
                if (left < right) {
                    arr[right--] = arr[left];
                }
            }
            arr[left] = base;
            quickSort(arr, begin, left - 1);
            quickSort(arr, left + 1, end);
        }
    }
}
//标准快速排序，写法二，将写法一拆开，本质一样都是分治法
public class QuickSort {
    public static void main(String[] args) {
        int[] arrs = {5, 2, 9, 1, 5, 6};
        System.out.println(Arrays.toString(arrs));
        quickSort(arrs, 0, arrs.length - 1);
        System.out.println(Arrays.toString(arrs));
    }

    public static void quickSort(int[] arrs, int begin, int end) {
        if (begin < end) {
            int pos = partition(arrs, begin, end);
            quickSort(arrs, begin, pos - 1);
            quickSort(arrs, pos + 1, end);
        }
    }

    public static int partition(int[] arrs, int left, int right) {
        int pivot = arrs[left];
        while (left < right) {
            while (left < right && pivot <= arrs[right]) {
                right--;
            }
            arrs[left] = arrs[right];
            while (left < right && pivot >= arrs[left]) {
                left++;
            }
            arrs[right] = arrs[left];
        }
        arrs[left] = pivot;
        return left;
    }
}
```

```java
//Arrays用类打印数组、拷贝数组、数组扩容、数组排序
public static void main(String[] args) {
        int[] a = {1, 2, 3, 4, 5, 6};
        int[] b = Arrays.copyOfRange(a, 2, 4); //数组拷贝
        System.out.println(Arrays.toString(b));// 打印数组，[3, 4]
        int[] c = Arrays.copyOf(a, 10); //数组扩容
        System.out.println(Arrays.toString(c));//[1, 2, 3, 4, 5, 6, 0, 0, 0, 0]
        double[] d = {32.4, 54.3, 51.6};
        //对数组d打八折，把数组中的原数据改成新数据
        Arrays.setAll(d, new IntToDoubleFunction() {
            @Override
            public double applyAsDouble(int value) {
                return d[value] * 0.8;
            }
        });
        System.out.println(Arrays.toString(d));//[25.92, 43.44, 41.28]
        Arrays.sort(d);//默认升序排序
        System.out.println(Arrays.toString(d));
}
```

```java
//方法一，让类实现Comparable接口，重写compareTo方法
public class Student implements Comparable<Student>{
    private String name;
    private int age;

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public Student() {
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }


    @Override
    public int compareTo(Student o) {
        return getAge()-o.getAge();
        //如果是浮点数进行比较，使用Double.compare()和Float.compare()，它们的返回值都是int
    }
}
```

```java
//Arrays对对象数组进行自定义排序：
//如果按照小数进行比较，使用Double.compare()来简化
public static void main(String[] args) {
        Student[] students = new Student[3];
        students[0] = new Student("张三", 12);
        students[1] = new Student("李撒旦", 11);
        students[2] = new Student("仿真", 52);
//方法二，创建Comparator匿名内部类对象，重写compare方法
//      Arrays.sort(students, (o1,o2) -> o1.getAge()-o2.getAge());//按照年龄升序排序
//      System.out.println(Arrays.toString(students));
        Arrays.sort(students);
        System.out.println(Arrays.toString(students));
    }
```

lambda表达式用来简化函数式接口（接口里有且只有一个抽象方法）的匿名内部类的写法 (形参列表)->{方法体}
lambda的省略规则：
    1.参数类型可以不写
    2.如果只有一个参数，()也可以省略
    3.方法体只有一行代码，{;}可以不写 如果是return，则return也可以不写
使用方法引用（静态方法，实例方法，特定类型方法，构造器）进一步简化 lambda表达式

```java
//定义一个类
public class A{
    //静态方法
    public static int compareBy1(Student o1 , Student o2){
        return o1.getAge()-o2.getAge;
    }
    //实例方法
    public  int compareBy2(Student o1 , Student o2){
        return o1.getAge()-o2.getAge;
    }
}
//Test类
//静态方法引用，如果lambda表达式只是调用一个静态方法，并且前后参数的形式一致 
Arrays.sort(students, (o1,o2) -> o1.getAge()-o2.getAge());//替换前
Arrays.sort(students, (o1,o2) -> A.compareBy1(o1,o2));//替换后
Arrays.sort(students, A::compareBy1);
//实例方法引用，如果lambda表达式只是调用一个实例方法，并且前后参数的形式一致 
A a = new A();
Arrays.sort(students, (o1,o2) -> o1.getAge()-o2.getAge());
Arrays.sort(students, (o1,o2) -> a.compareBy2(o1,o2));
Arrays.sort(students, a::compareBy2);
//特定类型方法（比如compareToIgnoreCase）引用，如果lambda表达式只是调用一个实例方法，并且第一个参数是方法的主调，后面的参数是方法的入参
String[] name = {"ssad","fcva","ASdv","dsqq","Baasd"};       
Arrays.sort(name, (o1, o2) -> o1.compareToIgnoreCase(o2));//String类的compareToIgnoreCase方法，按字典顺序进行排序
Arrays.sort(name, String::compareToIgnoreCase);
```

```java
//构造器引用，如果lambda表达式只是在创建对象，并且前后参数的形式一致
//Car类
public class Car {
    private String name ;
    private double price;
    public Car(String name, double price) {
        this.name = name;
        this.price = price;
    }
    @Override
    public String toString() {
        return "Car{" +
                "name='" + name + '\'' +
                ", price=" + price +
                '}';
    }
}
//接口
public interface CreateCar {
    Car create(String name,double price);
}
//测试类
public class Test {
    public static void main(String[] args) {
//        CreateCar c = (name, price) -> new Car(name,price);
        CreateCar c = Car::new;
        Car car = c.create("宝马",100.2);
        System.out.println(car);
    }
}
```

```java
//正则表达式主要用来做合法验证和爬取数据
//字符类（只匹配单个字符）
[abc]：只能是a，b，或c
[^abc]：除了a，b，c之外的任何字符
[a-zA-z]：a到z A到Z，包括（范围）
[a-d[m-p]]：a到d，或m到p
[a-z&&[def]]：d,e, 或f(交集)
[a-z&&[^bc]]：a到z，除了b和c（等同于[ad-z]）
[a-z&&[^m-p]]：a到z，除了m到p（等同于[a-lq-z]）
//预定义字符（只匹配单个字符）
.	任何字符
\d	一个数字：[0-9]
    String s = "9";
    System.out.println(s.matches("\\d"));//true
\D	非数字：[^0-9]
\s	一个空白字符
\S	非空白字符[^\s]
\w	[a-zA-Z_0-9]
\W	[^\w]
//数量词
X?	X，一次或零次
X*	X，零次或多次
X+	X，一次或多次
X{n}	X，正好n次
x{n,}	X，至少n次
X{n,m}	X，至少n但不超过m次
//几个常用的符号
(?i)	忽略大小写
		String s = "asA";
        System.out.println(s.matches("(?i)[A][S][a]"));//true
|	或
    	String s = "asA";
        System.out.println(s.matches("[A|a][S|s][A]"));//true
() 		分组
    	String s = "asA";
        System.out.println(s.matches("((?i)[A])[S][a]"));//false
//手机号的正则表达式，String提供了一个匹配正则表达式的方法 matches
String s = "+8613503623594";
System.out.println(s.matches("\\+86[1][3-9]\\d{9}"));
```

------

异常
 	                        						Throwable类
						Error                                                   		Exception类
                                       						 RuntimeException类            		其他异常
运行时异常，编译时不会报错，如数组越界异常
编译时异常：如日期解析异常，编译阶段就会出现错误提示
异常处理的两种方式：捕获处理、抛出去
自定义运行时异常类：
1.定义异常类继承RuntimeException
2.右键重写无参和有参构造器
3.在异常出现的位置，throw抛出异常对象

```java
//运行时异常
public class MyException extends RuntimeException{
    public MyException() {
    }

    public MyException(String message) {
        super(message);
    }
}
//测试类
public class Test {
    public static void main(String[] args) {
        chu(10, 0);
    }

    public static int chu(int i, int j) {
        if(j==0){
            throw new MyException("分母不能为0");
        }
        return i / j;
    }
}
```

自定义编译时异常类：
1.定义异常类继承Exception
2.右键重写无参和有参构造器
3.在异常出现的位置，throw抛出异常对象，并在方法上throws

```Java
//编译时异常
public class MyException extends Exception{
    public MyException() {
    }

    public MyException(String message) {
        super(message);
    }
}
//测试类
public class Test {
    public static void main(String[] args) throws MyException {
        chu(10, 0);
    }

    public static int chu(int i, int j) throws MyException {
        if(j==0){
            throw new MyException("分母不能为0");
        }
        return i / j;
    }
}
```

------

集合体系：有序是指有顺序（先进先出），升序是指排序（从小到大）
                                                Collection (单列)                                                     								 Map(双列)
           List接口（有重复、有索引、有序）      Set接口（无重复、无索引、无序）              HashMap                     TreeMap（升序）
  ArrayList      LinkedList                	HashSet               TreeSet（升序）   			LinkedHashMap（有序）
                  								LinkedHashSet（有序）
Collection提供的方法：add、remove、clear、isEmpty、size、contains、toArray（集合转换为数组）、addAll(倒出一个集合的元素到另一个集合中)

```java
//toArray方法
Collection<Integer> l1 = new ArrayList<>();
l1.add(0);
l1.add(1);
l1.add(2);
l1.add(3);
System.out.println(l1);//[0, 1, 2, 3]
Object[] objects = l1.toArray();
System.out.println(Arrays.toString(objects));//[0, 1, 2, 3]
Integer[] integers = l1.toArray(new Integer[5]);
System.out.println(Arrays.toString(integers));//[0, 1, 2, 3, null]
//Collection的遍历方式
Collection<String> c = new ArrayList();
c.add("java1");
c.add("java2");
//方式一：迭代器，Iterator<E> 是一个泛型接口
Iterator<String> it = c.iterator(); 
   while (it.hasNext()){
           System.out.println(it.next());
 }
//方式二：增强for，也可以用来遍历数组，本质是迭代器遍历的简化写法，数组和集合名称.for可以快捷生成
for (String ele:c) {
      System.out.println(ele);
}
//方式三：使用forEach和lambda和Consumer匿名内部类，Map集合遍历也可以使用，并且更能突出它的强大
c.forEach(s -> System.out.println(s));
c.forEach(System.out::println);//实例方法引用
```

List新提供的方法（根据索引增删改查）：add、remove、set、get
List的遍历方式：    1.迭代器       2.增强for     3.forEach和lambda   4.for循环
ArrayList基于数组，LinkedList基于双链表。

Set基本没有新增的方法，用到的方法基本是Collection提供的
Set的遍历方式：    1.迭代器       2.增强for     3.forEach和lambda
HashSet，LinkedHashSet基于哈希表，TreeSet基于红黑树。

```java
//集合的并发修改异常是指 ：在遍历集合时，边遍历边删除元素，会出错
ArrayList<String> c = new ArrayList();
c.add("张2");
c.add("王2");
c.add("张3");
c.add("李2");
c.add("张8");
//方法一：每删除一个要做一个i--
for (int i = 0; i < c.size(); i++) {
      if (c.get(i).startsWith("张")){
               c.remove(i);
               i--;
            }
}
//方法二：倒着遍历
for (int i = c.size() - 1; i >= 0; i--) {
    if (c.get(i).startsWith("张")){
                c.remove(i);
           }
}
//方法三：使用iterator.remove()
Iterator<String> it = c.iterator();
        while (it.hasNext()){
           String ele =  it.next();
           if(ele.startsWith("张")){
               it.remove(); //用迭代器自己的remove，而不是集合的
           }
}
```

Collections：Collections.addAll()批量添加元素，List和Set都可以，Collections.shuffle()对List集合打乱顺序，Collections.sort()对List集合排序，类似于Arrays.sort()
可变参数int...nums在函数中是当作数组来使用的

```java
ArrayList<String> c1 = new ArrayList();
c1.add("java1");
c1.add("java2");

System.out.println(c1);
Collections.addAll(c1,"java3","java4");
System.out.println(c1);//[java1, java2, java3, java4]
HashSet<Integer> c2 = new HashSet<>();
c2.add(1);
c2.add(2);
System.out.println(c2);
Collections.addAll(c2,3,4);
System.out.println(c2);//[1, 2, 3, 4]

Collections.shuffle(c1);
System.out.println(c1);//[java4, java3, java2, java1]
Collections.sort(c1);
System.out.println(c1);//[java1, java2, java3, java4]
```

Map(键值对集合)提供的方法：（键不能重复，值可以重复）
put、clear、isEmpty、size、containskey、containsValue、get（根据键取值，若键不存在返回null）、remove（根据键删除整个元素，返回对应的值，若键不存在返回null）、
keySet（获取全部键）、values（获取全部值）、putAll(倒出一个集合的元素到另一个集合)、entrySet

```java
Map<String, Integer> map1 = new HashMap<>();
map1.put("a", 1);
map1.put("b", 2);
map1.put("c", 3);
map1.put("d", 4);
System.out.println(map1);//{a=1, b=2, c=3, d=4}
Map<String, Integer> map2 = new HashMap<>();
map2.put("e", 5);
map2.put("f", 6);
map1.putAll(map2);
System.out.println(map1);//{a=1, b=2, c=3, d=4, e=5, f=6}
System.out.println(map2);//{e=5, f=6}
```

HashMap，LinkedHashMap基于哈希表，TreeMap基于红黑树。

```java
//Map的遍历
Map<String, Integer> m = new HashMap<>();
        m.put("A",123);
        m.put("B",3);
        m.put("C",222);
        m.put("D",512);
//方法一：键找值
Set<String> keys = m.keySet();
        for (String key : keys) {
            Integer value = m.get(key);
            System.out.println(key+"---"+value);
}
//方法二：键值对对象
Set<Map.Entry<String, Integer>> entries = m.entrySet();
        for (Map.Entry<String, Integer> entry : entries) {
            System.out.println(entry.getKey() + "---" + entry.getValue());
}
//方法三：foreach
m.forEach(new BiConsumer<String, Integer>() {
            @Override
            public void accept(String k, Integer v) {
                System.out.println(k+"---"+v);
            }
});
//简化后
m.forEach((k,v) -> System.out.println(k+"---"+v));
```

```java
//补充知识：集合的嵌套
Map<String, List<Integer>> m = new HashMap<>();
```

------

Stream是jdk8的新增的泛型接口，支持链式编程结合lambda表达式，用来操作数组和集合的数据

```java
//创建方法示例
//List和Set集合用stream()方法、Map集合调用entrySet先转换为Set集合,再用stream()方法
Map<String,Double> m = new HashMap<>();
m.put("配擒虎",168.0);
m.put("露娜",88.0);
m.put("高渐离",178.0);
m.put("孙尚香",28.0);
System.out.println(m);
Set<Map.Entry<String, Double>> entries = m.entrySet();
entries.stream().filter(e-> e.getKey().equals("露娜")).forEach(e-> System.out.println(e.getKey()+"-->"+e.getValue()));
//数组获取Stream流
public class StreamArrays {
    public static void main(String[] args) {
        String[] s = {"张三丰", "张无忌", "周芷若", "赵敏", "张强"};
        System.out.println(Arrays.toString(s));
//方法一：Arrays.stream(s)
System.out.println(Arrays.stream(s).filter(res -> res.startsWith("张") && res.length() == 3).collect(Collectors.toList()));
//方法二：Stream.of(s)
Stream.of(s).filter(res -> res.startsWith("张") && res.length() == 3).forEach( rs -> System.out.println(rs));
    }
}
```

```java
public class Student implements Comparable<Student>{
    private String name;
    private int age;
    private double height;

    public Student() {
    }
    
    public Student(String name, int age, double height) {
        this.name = name;
        this.age = age;
        this.height = height;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public double getHeight() {
        return height;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", height=" + height +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Student student = (Student) o;
        return age == student.age && Double.compare(student.height, height) == 0 && Objects.equals(name, student.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age, height);
    }

    @Override
    public int compareTo(Student o) {
        return o.age-age;
    }
}
//中间方法示例		filter，distinct，sorted,limit,skip,map(加工),concat
List<Student> ls = new ArrayList<>();
Student s1 = new Student("张三丰", 56, 173.7);
Student s2 = new Student("张无忌", 66, 143.6);
Student s3 = new Student("周芷若", 36, 89.4);
Student s4 = new Student("周芷若", 36, 89.4);
Student s5 = new Student("赵敏", 46, 155);
Collections.addAll(ls, s1, s2, s3, s4, s5);
//中间方法sorted排序
ls.stream().sorted((o1, o2) -> Double.compare(o1.getHeight(), o2.getHeight())).forEach(student -> System.out.println(student));
//中间方法limit获取前几个、skip跳过前几个
ls.stream().sorted().limit(3).skip(1).forEach(s-> System.out.println(s));
//中间方法filter过滤、map加工、distinct去重
//年龄不超46的学生姓名，其中map(s->s.getName())可以简化为特定类型方法引用map(Student::getName)，把学生对象加工成名字
ls.stream().filter(s -> s.getAge() <= 46).map(s->s.getName()).distinct().forEach(s-> System.out.println(s));
//若是对自定义对象内容进行去重，需要自定义对象重写equals和hashcode方法，一般在重写equals的时候将hashcode也顺便重写了
ls.stream().filter(s -> s.getAge() <= 46).distinct().forEach(s-> System.out.println(s));//年龄不超46的学生对象
```

```java
//终结方法示例	collect（toMap、toSet、toList）,foreach,max,min,toArray,count
Stream<Integer> s1 = Stream.of(1, 2, 3, 4);//可变参数获取Stream流的方式
Stream<Integer> s2 = Stream.of(5, 6, 7);
Stream<Integer> s3 = Stream.concat(s1, s2);//中间方法
s3.forEach(s-> System.out.println(s));//终结方法foreach
//System.out.println(s3.count());//终结方法count个数
//get()获取最值对象，不管是不是自定义类型对象都要注意声明比较规则
Integer integer = s3.max((o1, o2) -> o1 - o2).get();//终结方法max、min
Map<Integer, String> stringMap = s3.collect(Collectors.toMap(e -> e,e -> "s"));//终结方法collect收集到新集合
Object[] objects = s3.toArray();//终结方法toArray收集到数组
Integer[] arrs = s3.toArray(len -> new Integer[len]);//直接转换成Integer类型数组
```

------

File（操作文件本身）和io（操作文件的内容）
字节流适合文件复制，字符流适合读写文本数据
InputStream           	OutputStream              Reader                                 				Writer 													抽象类
FileInputStream       FileOutputStream          FileReader                           				FileWriter 												原始流
BufferedInputStream BufferedOutputStream  BufferedReader   						 BufferedWriter	      									包装流
                                                            	InputStreamReader    OutputStreamWriter 转换流（解决代码编码和文件编码不同导致的乱码）
                               PrintStream字节打印流                            PrintWriter字符打印流  打印流(能实现写啥打印啥，可以替代前面的输出流)
DateInputStream     DateOutputStream                                                                        	数据流（把数据和数据类型都读写）
ObjectInputStream  ObjectOutputStream 		序列化流（读写对象，其中的类要实现Serializable接口，不想序列化的属性加transient）

InputStream:    		read(),read(byte[] arr),readAllBytes()
OutputStream:   	write(int i),write(byte[] arr),write(byte[] arr,int off,int len)
Reader:        		 read(),read(char[] arr)
Writer:         		write(int i),write(char[] arr),write(char[] arr,int off,int len),write(String s),write(String s,int off,int len)
BufferedReader新增：readLine()
BufferedWriter新增：newLine()

------

```java
//InputStream方法
InputStream fi = new FileInputStream("E:\\ideacode\\JavaSEProject\\JavaSENew\\src\\1.txt");
byte[] bytes = fi.readAllBytes();//读取所有字节到一个字节数组中，可以解决中文乱码
System.out.println(new String(bytes));//abc
```

```java
//此时hje不会输出
System.out.println(10/0);
System.out.println("hje");
//此时hje会输出，asd不会输出
try {
    System.out.println(10/0);
    System.out.println("asd");
} catch (Exception e) {
     e.printStackTrace();
}
System.out.println("hje");
//此时hje不会输出
try {
            System.out.println(10/2);
            return;
        } catch (Exception e) {
            e.printStackTrace();
}
System.out.println("hje");
//此时hje会输出
try {
            System.out.println(10/2);
            return;
        } catch (Exception e) {
            e.printStackTrace();
        }finally {
            System.out.println("hje");
}
//此时hje不会输出
try {
            System.out.println(10/2);
            System.exit(0);
        } catch (Exception e) {
            e.printStackTrace();
        }finally {
            System.out.println("hje");
}
```

使用try-catch-resource来关闭资源比使用try-catch-finally来关闭资源更加简洁，资源都是会实现AutoCloseable接口的，用来作为标记

```java
try (OutputStream os = new FileOutputStream("javase\\src\\p12\\d2.txt");) {
        os.write(98);
    } catch (IOException e) {
        e.printStackTrace();
    }
//关闭高级流同时也会关闭低级流
InputStream is = new FileInputStream("javase\\src\\p12\\d2.txt");
BufferedInputStream bis = new BufferedInputStream(is);
bis.close();
```

```java
//转换流就是把字节流转换成字符流，以自定义解码的方式读入和自定义编码的方式写出
//字符输入转换流,也是一种字符输入流可以进行包装为缓冲流
public class InputStreamReaderDemo {
    public static void main(String[] args) {
        //先获取原始字节流，再按真正编码转成字符流
        try (InputStream fileInputStream = new FileInputStream("src\\com\\muc\\io\\d7.txt");//获取原始字节流，d7是gbk编码
             Reader is = new InputStreamReader(fileInputStream,"gbk");//以gbk的方式读入
             BufferedReader bw = new BufferedReader(is);//包装，自带8kb缓冲池
        )
        {
            char[] chars = new char[3];
            int len;
            while((len = bw.read(chars))!=-1){
                System.out.print(new String(chars,0,len));
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
//字符输出转换流
public class OutputStreamWriterDemo {
    public static void main(String[] args) {
        try (OutputStream fileOutputStream = new FileOutputStream("src\\com\\muc\\io\\999.txt");//原始字节输出流
             Writer os = new OutputStreamWriter(fileOutputStream,"gbk");// 以gbk的方式写出去
             BufferedWriter bos = new BufferedWriter(os);){
            bos.write("a我爱你中国123");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
//字节打印流，可以替代字符输出转换流，但是不支持追加（可以在低级流中添加追加参数来实现），而且内部还包装了缓冲流
PrintStream ps = new PrintStream("src\\com\\muc\\io\\d9.txt", "gbk");//以gbk的方式写出去
ps.print(12);//写啥打印啥
ps.print(true);
ps.print("中国");
//System.out就是一个PrintStream对象，可以实现打印重定向，控制台的输出语句重定向到文件中
PrintStream ps = new PrintStream("src\\com\\muc\\io\\d.txt");
System.setOut(ps);
//字节输入数据流
DataInputStream dis = new DataInputStream(new FileInputStream("src\\com\\muc\\io\\d10.txt"));
System.out.println(dis.readDouble());
System.out.println(dis.readBoolean());
System.out.println(dis.readUTF());
//字节输出数据流
DataOutputStream dos = new DataOutputStream(new FileOutputStream("src\\com\\muc\\io\\d10.txt"));
dos.writeDouble(99.0);
dos.writeBoolean(false);
dos.writeUTF("hello");
```

```java
//序列化流
public class Student implements Serializable {//实现接口
    private transient String name ;//该属性不参与序列化
    private int age;
    private  double height;

    public Student() {
    }

    public Student(String name, int age, double height) {
        this.name = name;
        this.age = age;
        this.height = height;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public double getHeight() {
        return height;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", height=" + height +
                '}';
    }
}
//写数据，序列化，ArrayList已经实现了序列化接口，可以对ArrayList进行序列化，一次序列化多个对象
ObjectOutputStream os = new ObjectOutputStream(new FileOutputStream("src\\com\\muc\\io\\d11.txt"));
os.writeObject(new Student("张三",12,178.6));
os.writeObject(new Student("里斯",42,145.3));
//读数据，反序列化
ObjectInputStream is = new ObjectInputStream(new FileInputStream("src\\com\\muc\\io\\d11.txt"));
Student s1 = (Student) is.readObject();
Student s2 = (Student) is.readObject();
System.out.println(s1);//Student{name='null', age=12, height=178.6}
System.out.println(s2);//Student{name='null', age=42, height=145.3}
```

这里学到第一个第三方jar包，Commons-io框架的FileUtils工具类和IOUtils工具类

```java
//FileUtils工具类
void copyFile(File srcFile,File destFile) //复制文件
void copyDirectory(File srcDir,File destDir)//复制文件夹
void deleteDirectory(File directory)//删除文件夹
String readFileToString(File file,String charsetName)//读数据
void writeStringToFile(File file,String data,String charsetName,boolean append)//指定编码、是否以追加的方式写入文件
    //以gbk的方式写出
    FileUtils.write(new File("E:\\temp\\javase\\src\\p14\\3.txt"),"我爱爱你中国sdh","gbk");
    //以gbk的方式读入
    String utf = FileUtils.readFileToString(new File("E:\\temp\\javase\\src\\p14\\3.txt"), "gbk");
    System.out.println(utf);
```

```java
//IOUtils工具类
int copy(InputStream input,OutputStream output)//复制文件
int copy(Reader reader,Writer writer)//复制文件 
void writer(String data,OutputStream output,String charsetName)//写数据
```

------

```java
//读写属性文件的内容，使用Map接口的实现类Properties
public static void main(String[] args) throws Exception {
    //写文件
     Properties p = new Properties();
     p.setProperty("奥迪","100w");//设置值属性
     p.setProperty("奔驰","40w");
     p.setProperty("宝马","20w");
     p.store(new FileWriter("E:\\p1.properties"),"it is note");//这里的资源会自动关闭
  //读文件
     Properties p = new Properties();
     p.load(new FileReader("E:\\p1.properties"));
     Set<String> keys = p.stringPropertyNames();//取所有的属性名
     for (String key : keys) {
           System.out.println(key + "---" + p.getProperty(key));//根据属性名得到属性值
        }
 }
```

```xml
<?xml version="1.0" encoding="utf-8" ?>
<cars>
    <car id="1">
        <name>奔驰</name>
        <price>35.6</price>
    </car>
    <car id="2">
        <name>奥迪</name>
        <price>33.2</price>
    </car>
    <car id="3">
        <name>比亚迪</name>
        <price>15.3</price>
    </car>
</cars>
```

```java
//Dom4j框架读取xml文件，学到的第2个第三方框架
public static void main(String[] args) throws Exception {
        SAXReader saxReader = new SAXReader();//使用SAXReader解析器，把xml文件变成一个文档对象document
        Document document = saxReader.read("E:\\ideacode\\Java\\JavaSE\\src\\com\\muc\\log\\x1.xml");
    	Element root = document.getRootElement();//获取根元素    
        System.out.println(root.getName());//获取元素名
        List<Element> cars = root.elements();//获取下级元素集合
        for (Element car : cars) {
            System.out.println(car.attributeValue("id"));//根据属性名获取属性值
            List<Element> elements = car.elements();//获取下级元素集合
            for (Element element : elements) {
                System.out.println(element.getText());//获取元素文本
            }
            System.out.println("------");
        }
    }
```

```java
//记录程序运行中的各种信息到指定的位置（控制台，文件，数据库），而且可以随时开启和关闭
//日志技术使用学到的第3个第三方框架Logback
//需导入三个模块：logback-core，slf4j-api, logback-classic, 添加核心配置文件logback.xml到src目录下
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
public class R {
// 创建一个Logger日志对象
        public static final Logger LOGGER = LoggerFactory.getLogger("日志对象的名字");
        public static void main (String[]args){
            try {
                LOGGER.info("chu法方法开始执行~~~");
                chu(10, 2);
                LOGGER.info("chu法方法执行成功~~~");
            } catch (Exception e) {
                LOGGER.error("chu法方法执行失败了，出现了bug~~~");
            }
        }
        public static void chu ( int a, int b){
            LOGGER.debug("参数a:" + a);
            LOGGER.debug("参数b:" + b);
            int c = a / b;
            LOGGER.info("结果是：" + c);
        }
}
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <!--CONSOLE ：表示当前的日志信息是可以输出到控制台的。-->
    <appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
        <!--输出流对象 默认 System.out 改为 System.err-->
        <target>System.out</target>
        <encoder>
<!--格式化输出：%d表示日期，%thread表示线程名，%-5level：级别从左显示5个字符宽度
%msg：日志消息，%n是换行符-->
        <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} [%-5level]  %c [%thread] : %msg%n</pattern>
        </encoder>
    </appender>

    <!-- File是输出的方向通向文件的 -->
    <appender name="FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <encoder>
            <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n</pattern>
            <charset>utf-8</charset>
        </encoder>
        <!--日志输出路径-->
        <file>D:/log/itheima-data.log</file>
        <!--指定日志文件拆分和压缩规则-->
        <rollingPolicy
                class="ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy">
            <!--通过指定压缩文件名称，来确定分割文件方式-->
            <fileNamePattern>D:/log/itheima-data-%i-%d{yyyy-MM-dd}-.log.gz</fileNamePattern>
            <!--文件拆分大小-->
            <maxFileSize>1MB</maxFileSize>
        </rollingPolicy>
    </appender>

    <!--1、控制日志的输出情况：如，开启日志，取消日志-->
    <root level="debug">
        <appender-ref ref="CONSOLE"/>
        <appender-ref ref="FILE" />
    </root>
</configuration>
```

------

```java
//线程创建方式一：继承Thread类，缺点无法继承其他类，不利于功能的拓展
public class MyThread1 extends Thread {
    public MyThread1(String name){
        super(name);
    }
    @Override
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println(Thread.currentThread().getName() +"---"+ i);
        }
    }
}
//调用
new MyThread1("子线程1").start();
new MyThread1("子线程2").start();
for (int i = 0; i < 5; i++) {
     System.out.println("主线程---" + i);
}
```

```java
//线程创建方式二：创建Runnable接口实现类（任务类）对象，交给new Thread()
new Thread(new Runnable() {
            @Override
            public void run() {
                for (int i = 0; i < 3; i++) {
                    System.out.println(Thread.currentThread().getName() + "---" + i);//默认线程名Thread-0
                }
            }
}).start();
new Thread(new Runnable() {
            @Override
            public void run() {
                for (int i = 0; i < 3; i++) {
                    System.out.println(Thread.currentThread().getName() + "---" + i);//默认线程名Thread-1
                }
            }
}).start();
for (int i = 0; i < 3; i++) {
            System.out.println(Thread.currentThread().getName() + "---" + i);//默认线程名main
}
```

```java
//线程创建方式三：创建Callable接口实现类对象，交给new FutureTask<>()，再交给new Thread()，与前两种方式相比，它的call方法可以返回结果
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

public class Test {
    public static void main(String[] args) throws ExecutionException, InterruptedException {
        FutureTask<String> futureTask1 = new FutureTask<>(new C());
        new Thread(futureTask1).start();
        System.out.println(futureTask1.get());

        FutureTask<String> futureTask2 = new FutureTask<>(new Callable<String>() {
            @Override
            public String call() throws Exception {
                for (int i = 0; i < 3; i++) {
                    System.out.println(Thread.currentThread().getName() + "---" + i);
                }
                return "call的返回值";
            }
        });
        new Thread(futureTask2).start();
        System.out.println(futureTask2.get());
    }
}
```

```java
import java.util.concurrent.Callable;

public class C implements Callable<String> {
    @Override
    public String call() throws Exception {
        for (int i = 0; i < 3; i++) {
            System.out.println(Thread.currentThread().getName() + "---" + i);
        }
        return "call的返回值";
    }
}
```

```java
//Thread提供的常用方法sleep
for (int i = 0; i < 5; i++) {
    if(i==3){
        Thread.sleep(3000);
    }
}
//Thread提供的常用方法join，保证线程有序执行
Thread a1 = new MyThread1("1号");
a1.start();
a1.join();//让a1线程先执行
Thread a2 = new MyThread1("2号");
a2.start();
a2.join();//让a2线程先执行
```

线程安全问题：多个线程同时修改共享资源，使用线程同步解决线程安全问题，有三种方式：

```java
//方式一：同步代码块 synchronized
//账户类
public class Account {
    private double money;

    public Account() {
    }

    public Account(double money) {
        this.money = money;
    }

    public double getMoney() {
        return money;
    }

    public void setMoney(double money) {
        this.money = money;
    }

    @Override
    public String toString() {
        return "Account{" +
                "money=" + money +
                '}';
    }

    public void drawMoney() {
        Thread thread = Thread.currentThread();
        synchronized (this) {
            if (this.getMoney()>=10.0){
                System.out.println(thread.getName()+"正在取钱");
                this.setMoney(this.getMoney()-10.0);
                System.out.println(thread.getName()+"取钱成功，剩余"+ this.getMoney());
            }else{
                System.out.println(thread.getName()+"来取钱发现账户不足");
            }
        }
    }
}
//线程类
public class MyThread extends Thread{
    private Account account;
    public MyThread(Account account,String name){
        super(name);
        this.account=account;
    }
    @Override
    public void run() {
        account.drawMoney();
    }
}
//测试类
Account account = new Account(10.0);
MyThread myThread1 = new MyThread(account,"爸爸");
myThread1.start();
MyThread myThread2 = new MyThread(account,"妈妈");
myThread2.start();
```

```java
//方式二： 同步方法  synchronized
//账户类
public class Account {
    private double money;

    public Account() {
    }

    public Account(double money) {
        this.money = money;
    }

    public double getMoney() {
        return money;
    }

    public void setMoney(double money) {
        this.money = money;
    }

    @Override
    public String toString() {
        return "Account{" +
                "money=" + money +
                '}';
    }

    public synchronized void drawMoney() {
        Thread thread = Thread.currentThread();
            if (this.getMoney()>=10.0){
                System.out.println(thread.getName()+"正在取钱");
                this.setMoney(this.getMoney()-10.0);
                System.out.println(thread.getName()+"取钱成功，剩余"+ this.getMoney());
            }else{
                System.out.println(thread.getName()+"来取钱发现账户不足");
            }
    }
}
//线程类
public class MyThread extends Thread{
    private Account account;
    public MyThread(Account account,String name){
        super(name);
        this.account=account;
    }
    @Override
    public void run() {
        account.drawMoney();
    }
}
//测试类
Account account = new Account(10.0);
MyThread myThread1 = new MyThread(account,"爸爸");
myThread1.start();
MyThread myThread2 = new MyThread(account,"妈妈");
myThread2.start();
```

```java
//方式三： 使用Lock接口的实现类ReentrantLock来构建Lock锁对象   手动加减锁，更灵活
//账户类
public class Account {
    private double money;
    //每一个账户对象都应该有一个锁对象
    private final Lock lk = new ReentrantLock();

    public void drawMoney() {
        Thread thread = Thread.currentThread();
        lk.lock();
        try {
            if (this.getMoney()>=10.0){
                System.out.println(thread.getName()+"正在取钱");
                this.setMoney(this.getMoney()-10.0);
                System.out.println(thread.getName()+"取钱成功，剩余"+ this.getMoney());
            }else{
                System.out.println(thread.getName()+"来取钱发现账户不足");
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            lk.unlock();
        }
    }

    public Account() {
    }

    public Account(double money) {
        this.money = money;
    }

    public double getMoney() {
        return money;
    }

    public void setMoney(double money) {
        this.money = money;
    }

    @Override
    public String toString() {
        return "Account{" +
                "money=" + money +
                '}';
    }
}
//线程类
public class MyThread extends Thread{
    private Account account;
    public MyThread(Account account,String name){
        super(name);
        this.account=account;
    }
    @Override
    public void run() {
        account.drawMoney();
    }
}
//测试类
Account account = new Account(10.0);
MyThread myThread1 = new MyThread(account,"爸爸");
myThread1.start();
MyThread myThread2 = new MyThread(account,"妈妈");
myThread2.start();
```

线程池就是一个可以复用线程的技术，既能控制线程的数量也能控制任务的数量，避免资源的耗尽

```java
//创建线程池方式一 :  利用ExecutorService接口的实现类ThreadPoolExecutor
ThreadPoolExecutor(int corePoolSize, //核心线程数量
       int maximumPoolSize,//最大线程数量=核心线程数量+临时线程数量
      long keepAliveTime,//临时线程的最大空闲时间，超过空闲时间没使用就销毁。
       TimeUnit unit,//时间单位
        BlockingQueue<Runnable> workQueue,//任务队列
        ThreadFactory threadFactory,//线程工厂（为线程池创建线程）
 RejectedExecutionHandler handler) //拒绝策略（核心线程和临时线程都忙，任务队列满了，新任务来了该怎么处理）

ExecutorService p1 = new ThreadPoolExecutor(3,5,8,TimeUnit.SECONDS,
new ArrayBlockingQueue<>(4),//任务队列基于数组,指定最大任务数量4
Executors.defaultThreadFactory(),
new ThreadPoolExecutor.AbortPolicy());//核心线程和临时线程都忙，任务队列满了，新任务来了直接抛出异常

//任务队列基于链表（了解）
ExecutorService p2 = new ThreadPoolExecutor(3,5,8,TimeUnit.SECONDS,
new LinkedBlockingQueue<>(), Executors.defaultThreadFactory(), new ThreadPoolExecutor.AbortPolicy());

//临时线程的创建时间
核心线程在忙，任务队列满了，新任务来了，此时会创建临时线程
```

```java
//使用线程池处理Runnable任务
public class MyThread implements Runnable{
    @Override
    public void run() {
        System.out.println(Thread.currentThread().getName() + "---任务");

        try {
            Thread.sleep(Integer.MAX_VALUE);//该任务负责拖死线程
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
public class Test {
    public static void main(String[] args) {
        ExecutorService p = new ThreadPoolExecutor(3, 5, 8, TimeUnit.SECONDS,
                new ArrayBlockingQueue<>(4), Executors.defaultThreadFactory(), new ThreadPoolExecutor.AbortPolicy());
        Runnable target = new MyThread();
        p.execute(target);//使用核心线程1
        p.execute(target);//使用核心线程2
        p.execute(target);//使用核心线程3
        p.execute(target);//排队1
        p.execute(target);//排队2
        p.execute(target);//排队3
        p.execute(target);//排队4
        p.execute(target);//进来排队，开始使用临时线程4
        p.execute(target);//进来排队，开始使用临时线程5
        p.execute(target);//拒绝策略，抛出异常
    }
}
```

```java
//使用线程池处理Callable任务
public class MyThread implements Callable<String> {
    @Override
    public String call() throws Exception {
        System.out.println(Thread.currentThread().getName() + "---任务");
        try {
            Thread.sleep(Integer.MAX_VALUE);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        return "返回结果";
    }
}
public class Test {
    public static void main(String[] args) throws Exception {
        ExecutorService p = new ThreadPoolExecutor(3, 5, 8, TimeUnit.SECONDS,
                new ArrayBlockingQueue<>(4), Executors.defaultThreadFactory(), new ThreadPoolExecutor.AbortPolicy());
        Callable<String> target = new MyThread();
//       获取返回值
//        Future<String> res = p.submit(target);
//        System.out.println(res.get());
        p.submit(target);//使用核心线程1
        p.submit(target);//使用核心线程2
        p.submit(target);//使用核心线程3
        p.submit(target);//排队1
        p.submit(target);//排队2
        p.submit(target);//排队3
        p.submit(target);//排队4
        p.submit(target);//进来排队，开始使用临时线程4
        p.submit(target);//进来排队，开始使用临时线程5
        p.submit(target);//拒绝策略，抛出异常
    }
}
```

```java
//创建线程池方式二 : Executors工具类提供了许多静态方法来创建不同的线程池，这种方式会出现并发风险，阿里推荐第一种方式
public class Test {
    public static void main(String[] args) throws Exception {
        ExecutorService p = Executors.newFixedThreadPool(3);//核心3，最大线程3
        Callable<String> target = new MyThread();
        p.submit(target);//核心1
        p.submit(target);//核心2
        p.submit(target);//核心3
        p.submit(target);//排队
    }
}
```

------

```java
//		InetAddress类代表IP地址
//        本机ip对象
        InetAddress localHost = InetAddress.getLocalHost();
//        百度ip对象
        InetAddress baiDu = InetAddress.getByName("www.baidu.com");
        System.out.println(localHost.getHostAddress());//10.151.212.192
        System.out.println(localHost.getHostName());//DESKTOP-3KT8MPK
        System.out.println(baiDu.getHostAddress());//220.181.38.150
        System.out.println(baiDu.getHostName());//www.baidu.com
//        主机在5秒内能否和百度连通
        System.out.println(baiDu.isReachable(5000));//true
```

```java
//UDP通信，用户数据报协议，无连接，不可靠，数据包包括客户端ip、端口和服务端ip、端口以及数据，通信效率高
DatagramSocket用来创建客户端和服务端，DatagramPacket用来创建数据包
//一发一收
//服务端
public class UdpServer {
    public static void main(String[] args) throws Exception {
        System.out.println("服务端启动");
        DatagramSocket server = new DatagramSocket(6666);//指定端口号
        
        byte[] bytes = new byte[50];
        DatagramPacket packet = new DatagramPacket(bytes, bytes.length);//创建用来接收数据的数据包
        
        server.receive(packet);
        //packet.getAddress()拿到客户端ip对象
        //System.out.println(packet.getAddress().getHostAddress() +":"+ packet.getPort());
        //packet.getLength()获取当前数据包实际接了多少字节个数
        System.out.println(new String(bytes, 0, packet.getLength()));
        server.close();
    }
}
//客户端
public class UdpClient {
    public static void main(String[] args) throws Exception {
        System.out.println("客户端启动");
        DatagramSocket client = new DatagramSocket();//随机分配一个端口号，也可以指定
        
        byte[] bytes = "你好呀".getBytes();
        DatagramPacket packet = new DatagramPacket(bytes, bytes.length, InetAddress.getLocalHost(), 6666);//创建用来发出数据的数据包，后两个参数分别为目的地ip对象和端口
        
        client.send(packet);
        System.out.println("发送完毕");
        client.close();
    }
}
```

```java
//多发多收（多个或一个客户端对一个服务端）
//服务端
public class Server {
    public static void main(String[] args) throws Exception {
        System.out.println("服务端启动");
        DatagramSocket server = new DatagramSocket(6666);

        byte[] bytes = new byte[50];
        DatagramPacket packet = new DatagramPacket(bytes, bytes.length);
        while (true) {
            server.receive(packet);
            System.out.println(packet.getAddress().getHostAddress() + ":" + packet.getPort() + "---" + new String(bytes, 0, packet.getLength()));
            System.out.println("-----");
        }
    }
}
//客户端
public class Client {
    public static void main(String[] args) throws Exception {
        DatagramSocket client = new DatagramSocket();
        Scanner sc = new Scanner(System.in);
        while (true) {
            System.out.println("请输入：");
            String s = sc.nextLine();
            if (s.equals("退出")){
                break;
            }
            byte[] bytes = s.getBytes();
            DatagramPacket packet = new DatagramPacket(bytes,bytes.length, InetAddress.getLocalHost(),6666);
            client.send(packet);
            System.out.println("客户端发送完毕");
        }
        client.close();
    }
}
```

```java
//TCP通信，传输控制协议，面向连接，可靠，通信效率不高
三次握手建立连接：客户端发出连接请求，服务端返回一个响应，客户端再次发出确认信息，连接建立，双方都知道对方可以收发数据
传输数据进行确认：客户端发送数据到服务端，服务端接收到数据后会返回一个确认给客户端，如果客户端没有收到确认，则会继续给服务端发送相同的数据
四次挥手断开连接：客户端发出断开连接请求，服务端返回稍等响应，服务端返回可以断开的响应，客户端发出正式确认，断开连接
//一发一收
//服务端
public class Server {
    public static void main(String[] args) throws Exception {
        System.out.println("服务端启动");
        ServerSocket socket = new ServerSocket(8888);
        Socket server = socket.accept();
        InputStream is = server.getInputStream();
        DataInputStream dis = new DataInputStream(is);//数据流
        String s = dis.readUTF();
        System.out.println(s);
        dis.close();
        server.close();
    }
}
//客户端
public class Client {
    public static void main(String[] args) throws Exception {
        Socket client = new Socket("127.0.0.1",8888);
        OutputStream os = client.getOutputStream();
        DataOutputStream dos = new DataOutputStream(os);
        dos.writeUTF("hello");
        System.out.println("发送完毕");
        dos.close();
        client.close();
    }
}
```

```java
//多发多收（一个客户端）
//服务端
public class Server {
    public static void main(String[] args) throws Exception {
        System.out.println("服务端启动");
        ServerSocket socket = new ServerSocket(8888);
        Socket server = socket.accept();
        InputStream is = server.getInputStream();
        DataInputStream dis = new DataInputStream(is);
        while (true) {
            try {
                String s = dis.readUTF();
                System.out.println(s);
            } catch (IOException e) {
                System.out.println(server.getRemoteSocketAddress() + "离线了");///127.0.0.1:56285离线了
                dis.close();
                server.close();
                break;
            }
        }
    }
}
//客户端
public class Client {
    public static void main(String[] args) throws Exception {
        Socket client = new Socket("127.0.0.1",8888);
        OutputStream os = client.getOutputStream();
        DataOutputStream dos = new DataOutputStream(os);
        Scanner sc = new Scanner(System.in);
        while (true) {
            System.out.println("请输入：");
            String s = sc.nextLine();
            if (s.equals("退出")){
                break;
            }
            dos.writeUTF(s);
            System.out.println("发送完毕");
        }
        dos.close();
        client.close();
    }
}
```

```java
//多发多收（多个客户端，需要多线程配合实现，因为每个客户端都需要和服务端建立一个属于双方自己的连接）
//服务端
public class Server {
    public static void main(String[] args) throws Exception {
        System.out.println("服务端启动");
        ServerSocket socket = new ServerSocket(8888);
        while (true) {
            Socket server = socket.accept();
            System.out.println(server.getRemoteSocketAddress()+"上线了");
            new ServerThread(server).start();
        }
    }
}
//服务端线程类
public class ServerThread extends Thread{
    private Socket server;

    public ServerThread(Socket server) {
        this.server = server;
    }

    @Override
    public void run() {
        try {
            InputStream is = server.getInputStream();
            DataInputStream dis = new DataInputStream(is);
            while (true) {
                try {
                    String s = dis.readUTF();
                    System.out.println(s);
                } catch (IOException e) {
                    System.out.println(server.getRemoteSocketAddress() + "离线了");///127.0.0.1:56285离线了
                    dis.close();
                    server.close();
                    break;
                }
            }
        } catch (Exception e) {
            e.printStackTrace();
        }

    }
}
//客户端
public class Client {
    public static void main(String[] args) throws Exception {
        Socket client = new Socket("127.0.0.1",8888);
        OutputStream os = client.getOutputStream();
        DataOutputStream dos = new DataOutputStream(os);
        Scanner sc = new Scanner(System.in);
        while (true) {
            System.out.println("请输入：");
            String s = sc.nextLine();
            if (s.equals("退出")){
                break;
            }
            dos.writeUTF(s);
            System.out.println("发送完毕");
        }
        dos.close();
        client.close();
    }
}
```

------

单元测试针对方法进行测试，学到的第4个第三方框架Junit，idea已经集成了Junit，最核心的功能是断言机制（预测）
为需要测试的类创建对应的测试类，为每个方法编写对应的测试方法（必须公共、无参、无返回值），在测试方法中调用被测试方法

```java
//业务类
public class A {
    public static void getLength(String s) {
//        if (s == null) {
//            System.out.println(0);
//            return;
//        }
        System.out.println(s.length());
    }
    public static int getMaxIndex(String s) {
        if (s == null) {
            return -1;
        }
        return s.length();
//        return s.length()-1;
    }
}
//测试类
public class ATest {
    @Test
    public void testGetLength(){
        A.getLength("abc");
        A.getLength(null);
    }
    @Test
    public void testGetMaxIndex(){
        Assert.assertEquals("出现bug",2,A.getMaxIndex("abc"));//断言
        System.out.println(A.getMaxIndex(null));
    }
}
```

------

注解、反射和动态代理都是为了以后学习框架

------

```java
//自定义注解
public @interface MyTest {
    //属性
    String a();
    boolean b() default  true;
    String[] c();
}
//注解的使用
@MyTest(a = "sad", c = {"1", "2", "3"})
public class Test1 {
    @MyTest(a = "sss", b = false, c = {"1", "2"})
    public void test() {

    }
}

若注解只有一个属性value，在使用时可以不写value
//自定义注解
public @interface MyTest {
//    特殊属性
    String value();
}
//注解的使用
@MyTest("sad")
public class Test1 {
    public void test() {

    }
}

//注解:本质是接口，属性是抽象方法，使用注解本质是创建了实现类对象
public interface MyTest extends Annotation{
    public abstract String value();
}
```

```java
//元注解：修饰注解的注解
//修饰注解可以在哪些地方使用
@Target(ElementType.TYPE,ElementType.METHOD)
TYPE，类，接口
FIELD，成员变量
METHOD，成员方法
PARAMETER，方法参数
CONSTRUCTOR，构造器
LOCAL_VARIABLE，局部变量
//声明注解的保留周期
@Retention(RetentionPolicy.RUNTIME)
1. SOURCE
只作用在源码阶段，字节码文件中不存在。
2.CLASS(默认值)
保留到字节码文件阶段，运行阶段不存在。
3.RUNTIME(开发常用)
一直保留到运行阶段。
```

------

```java
反射：把类的字节码文件加载到内存中，以编程的方式解剖类的各种成分（成员变量，成员方法，构造器），主要是用来做框架的
package d12;
//准备好的学生类
public class Student {
    private int age;
    private String name;

    public Student() {
    }

    public Student(int age) {
        this.age = age;
    }

    private Student(int age, String name) {
        this.age = age;
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    private void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    private void setName(String name) {
        this.name = name;
    }
    
    @Override
    public String toString() {
        return "Student{" +
                "age=" + age +
                ", name='" + name + '\'' +
                '}';
    }
}
//获取类的字节码，用Class对象代替，万物皆对象
package d12;

public class Test {
    public static void main(String[] args) throws ClassNotFoundException {
	//        方式一：
        Class c1 = Student.class;
        System.out.println(c1.getName());//d12.Student包名+类名=全类名
        System.out.println(c1.getSimpleName());//Student
	//        方式二：
        Class c2 = Class.forName("d12.Student");
        System.out.println(c1==c2);//true
	//        方式三：
        Student s = new Student();
        Class c3 =  s.getClass();//由Object继承的方法
        System.out.println(c3==c2);//true
    }
}
//获取类的构造器，用Constructor对象代替
		Class c = Student.class;
        Constructor[] constructors1 = c.getConstructors();//只能获取public
        for (Constructor constructor : constructors1) {
            System.out.println(constructor.getName() + ":" + constructor.getParameterCount());
        }
        Constructor[] constructors2 = c.getDeclaredConstructors();//只要存在就能拿到
        for (Constructor constructor : constructors2) {
            System.out.println(constructor.getName() + ":" + constructor.getParameterCount());
        }
        Constructor constructor1 = c.getConstructor(int.class);
        System.out.println(constructor1.getName() + ":" + constructor1.getParameterCount());//只能获取public
        Constructor constructor2 = c.getDeclaredConstructor(int.class,String.class);
        System.out.println(constructor2.getName() + ":" + constructor2.getParameterCount());//只要存在就能拿到

	拓展：使用构造器对象来创建对象
		Class c = Student.class;
		//反射一般不使用泛型
		Constructor constructor = c.getDeclaredConstructor(int.class, String.class);//私有
		//暴力反射，禁止检查访问控制，反射可以破坏封装性
		constructor.setAccessible(true);
		Student o = (Student) constructor.newInstance(12, "张三");
		System.out.println(o);

//获取类的成员变量，用Field对象代替
Class c = Student.class;
		//        Field[] fields = c.getFields();//只能获取public
        Field[] fields = c.getDeclaredFields();//只要存在就能拿到
        for (Field field : fields) {
            System.out.println(field.getName() + "---" + field.getType());
        }
		//        Field field = c.getField("age");//只能获取public
        Field field = c.getDeclaredField("name");//只要存在就能拿到
        System.out.println(field.getName() + "---" + field.getType());

	拓展：对成员变量赋值和取值
    Class c = Student.class;
        Field field = c.getDeclaredField("age");//只要存在就能拿到
        Student student = new Student();
        field.setAccessible(true);//暴力反射
        field.set(student,11);
        System.out.println(student);//Student{age=11, name='null'}
        System.out.println(field.get(student));//11

//获取类的成员方法，用Method对象代替
Class c = Student.class;
        Method[] methods1 = c.getMethods();//只能获取public
        for (Method method : methods1) {
            System.out.println(method.getName() + "---" + method.getParameterCount());
        }
        Method[] methods2 = c.getDeclaredMethods();//只要存在就能拿到
        for (Method method : methods2) {
            System.out.println(method.getName() + "---" + method.getParameterCount());
        }
        Method method1 = c.getMethod("getAge");//只能获取public
        System.out.println(method1.getName() + "---" + method1.getParameterCount());
        Method method2 = c.getDeclaredMethod("setAge",int.class);//只要存在就能拿到
        System.out.println(method2.getName() + "---" + method2.getParameterCount());

	拓展：执行成员方法
   Class c = Student.class;
        Method method = c.getDeclaredMethod("setAge",int.class);//只要存在就能拿到
        Student student = new Student();
        method.setAccessible(true);
        Object rs = method.invoke(student, 11);//rs代表该方法的返回值，如果是void就返回null
        System.out.println(rs);//null
        System.out.println(student);
```

------

```java
//代理长什么样子
public interface Star {
    String sing();
    String dance();
}
//明星
public class BigStar implements Star {
    private String name;

    public BigStar(String name) {
        this.name = name;
    }

    @Override
    public String sing(String name) {
        System.out.println(this.name + "唱了" + name);
        return "谢谢";
    }

    @Override
    public void dance() {
        System.out.println(this.name + "正在跳舞");
    }
}
//代理工具类，相当于中介公司，为明星创建一个代理
public class ProxyUtils {
    public static Star createProxy(BigStar bigStar){
        Star proxy = (Star) Proxy.newProxyInstance(
      ProxyUtils.class.getClassLoader(),	//指定一个类加载器
      new Class[]{Star.class},	//指定生成的代理有哪些方法，接口数组
      new InvocationHandler() {	//指定生成的代理要做什么
            @Override
            public Object invoke(Object proxy,
                                 Method method,
                                 Object[] args) throws Throwable {
                if (method.getName().equals("sing")){
                    System.out.println("开始唱歌收费");
                }else if (method.getName().equals("dance")){
                    System.out.println("开始跳舞收费");
                }
                return method.invoke(bigStar, args);//调用bigStar的method方法，args是参数，将返回值返回给主程序
            }
        });
        return proxy;
    }
}
//测试类
public class Test {
    public static void main(String[] args) {
        BigStar bigStar = new BigStar("刘德华");
        Star proxy = ProxyUtils.createProxy(bigStar);
        //去调用invoke(Object proxy, Method method, Object[] args)方法，把proxy传给proxy，把sing传给method，把"冰雨"传给args
        String s = proxy.sing("冰雨");
        System.out.println(s);
        proxy.dance();
    }
}
```

![image-20240829220446032](C:\Users\sunbo\AppData\Roaming\Typora\typora-user-images\image-20240829220446032.png)

------

![image-20240901130423234](C:\Users\sunbo\AppData\Roaming\Typora\typora-user-images\image-20240901130423234.png)

![image-20240901130336754](C:\Users\sunbo\AppData\Roaming\Typora\typora-user-images\image-20240901130336754.png)