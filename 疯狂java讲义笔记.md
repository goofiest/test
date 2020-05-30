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



▲ 抽象方法 ：只有方法名，没有方法体。（子类必须重写该方法）。

 



