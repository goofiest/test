## 疯狂java讲义笔记

### final

 final 可以修饰变量（各种变量）、方法、类。

 final 与 abstract 是互斥的 ：永远不会同时出现。

▲ final 修饰变量：该变量被赋初始值之后，不能被重新赋值！final 修饰的变量<font color= red>必须</font>被赋值，且只能赋值<font color=red>一次</font>。

▲ final 修饰成员变量:

​	非 final 的成员变量，程序员可以不显示指定初始值，系统会默认初始值。

​	final 的成员变量，程序员必须显示指定初始值。

​	☆ final 实例变量，必须显示指定初始值。只能在以下三个位置的其中之一指定。（本质只有一个：【构造器】）

​		—— 定义时指定初始值。

​		—— 实例初始化块。

​		—— 每个构造器显示指定一次初始值。

~~~java
class test1{
	
	final int age = 3; // 定义时指定
	final int a1;
	
	{
		a1 =6;	// 实例初始化块。
	}
}

class test2{
	
	final double b1;
		
	public test2() {	// 每个构造器显示指定一次初始值。
		b1 = 3.3;
	}
	
	public test2(double a) { //每个构造器显示指定一次初始值。
		b1 = 3.5;
	}
}

public class final关键字1 {
	
	public static void main(String[] args) {		
		test2 sta1 = new test2(4.3);
	}
	
}
~~~

​	☆ final 类变量，必须显示指定初始值。只能在一下两个位置的其中之一指定（本质只有一个【类初始化块】）；

​		—— 定义时指定初始值；

​		—— 类初始化块；

▲ final 修饰局部变量：

​	非 final 的局部变量，程序员必须先指定初始值，然后才能使用。

​	final 的局部变量，程序员必须先指定初始值，然后才能使用，final 局部变量不能被重复赋值。

▲ final 修饰的引用变量。

​	—— final 只保证引用变量本身不会被重新赋值，该变量所引用的对象可以被修改。

<font color = red> 本节没写完</font>



### abstract (抽象)

​	它只能修饰两个东西 ：<font color=red>方法</font>和<font color=red>类</font>。（抽象方法和抽象类）

abstract 与 final ，互斥永远不能同时出现！

▲ 抽象类：有得有失。

​	—— 有得 ：得到一个新功能：抽象类可拥有抽象方法。

​	—— 有失 ：抽象类失去了一个功能：创建对象。

​	☆ 抽象类的主要作用：派生子类	—— 子类构造器一定调用父类构造器一次。因此抽象类必须有构造器。



▲ 抽象方法 ：只有方法名，没有方法体。 

​		—— 抽象方法，一定要交给子类实现，否则不能调用！

▲ 抽象类的作用：

​	（1）、定义变量 （只能用它的子类的实例： 向上转型）。

​	（2）、调用类方法和类变量。

​	（3）、 派生子类 —— 主要作用。



### 接口 interface

​	接口相当于一种彻底的抽象类。 【接口多继承】

​	接口体现的是一种规范——要暴露出来供大家遵守，所以接口里所有东西都用 public 修饰，不管写不写，始终都有 public 修饰，所以通常不写。

▲ 接口语法：

​	【修饰符】 interface 接口名 extends 父接口1 ，父接口2 ……{

​			// 成员变量；（只有常量。始终会默认添加 public static final 修饰。通常不需要写）

​			// 抽象方法；（java 8 ，之后，可以写类方法）

​			// 内部类；

​		}

▲ 接口的用处；

​	—— 定义变量（只能用实现类的实例来赋值【向上转型】）。

​	—— 调用类方法或类变量。

​	—— 派生实现类。【重点用途】

▲ 接口实现：

​	【修饰符】 class 类名 extends 父类 implements 父接口1 ， 父接口2，……

​			{

​				// 五大成员

​				}

​	【推论：】 子类要么重写接口中所有抽象方法，要么子类也只能时抽象的。重写接口中的方法只能用 public 修饰。



▲ Java 9 为接口增加 private 方法。

​	—— 由于接口中的 default 方法本质就是实例方法， 那么多个实例方法之间很可能出现 “ 公共部分 ” ，这个 “ 公共部分 ” 就应该被抽取到 “ 工具方法中 ” 。而 “ 工具方法 ” 又希望被隐藏，所以用 private 修饰。

“ 工具方法 ” 的本质：用于为接口中（实例方法）提供支持。



▲ 接口调用静态方法。

​	从java 8 开始，接口当中允许定义静态方法。

【注意事项】：不能通过接口实现类的对象来调用接口中的静态方法。

【正确用法】：通过接口名称，直接调用其中的静态方法。

~~~java
public interface StaticTest {

	public static void sta1() {	// public 可以省略 
		
		System.out.println("这是一个 static 方法");
	}
}

======================================================================================================
    
public class StaticDemo {
	
	public static void main(String[] args) {
		
		StaticTest.sta1();	// 成功调用
	}

}

~~~



▲ 接口作为成员变量；

~~~java
public interface Skil {
	
	void use();	// 技能；
	
}

~~~

~~~java
public class ShiJiNen implements Skil{
	public void use() {	// 实现技能；
		System.out.println("biu~biu~biu~");
	}
}

~~~

~~~java
public class ChenBan {
	private String name;
	private Skil skil;	// 接口作为成员变量；
	
	public void ChenBan() {};

	public void ChenBan(String name,Skil skil) {
		this.name = name;
		this.skil = skil;
	}
	
	
	public void setName(String name) {
		this.name = name;
	}
	
	public String getName() {
		return name;
	}

	public void setSkil(Skil skil) {
		this.skil = skil;
	}
	
	public Skil getSkil() {
		return skil;
	}
	
	
	public void start() {
		System.out.println("我的名字叫" + name + ", 开始释放技能……");
		skil.use(); // 调用技能；
		System.out.println("技能释放完毕！");
	}
	
}
~~~

~~~java
public class CenBanTest {
	public static void main(String[] args) {
		ChenBan st = new ChenBan();
		st.setName("妲己");
		st.setSkil(new ShiJiNen());
		
		st.start();
		
	}
}
~~~

