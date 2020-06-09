## Java 异常学习

### 异常定义：

​	———— Java 程序在运行时期发生的不正常情况（问题）。

▲ Java异常分为两种：

​	—— Error ：由系统底层发生的。Error类以及他的子类的实例，代表了JVM本身的错误。错误不能被程序员通过代码处理，Error很少出现。

​	—— Exception : Exception以及他的子类，代表程序运行时发送的各种不期望发生的事件。可以被Java异常处理机制使用，是异常处理的核心。

### 异常的处理：

​	1、声明异常：不进行具体处理，而是继续抛给调用者。在所定义功能时，需要在功能上对有可能发生的问题使用 throws 关键字进行声明。	——声明的目的：让调用者可以进行处理。

~~~java
public class 异常 {
	public static void main(String[] args)	throws Exception {
		
		Demo de = new Demo();
		
			System.out.println(de.div(2,0)); //被除数不能为零。
	}

}

class Demo	{
	
	int div (int a , int b) throws Exception{
		
		return a/b;
		}
	
	}
~~~



​	2、捕获异常（针对性处理）：

格式：

~~~java
try
{
	// 有可能发生异常的代码。
}

catch(异常类 变量)	// 没有该段代码，不能被称之异常针对性处理
{
	// 这是真正的捕获，处理异常的代码。
}
finally{
	// 一定会被执行的代码。
}
~~~

~~~java
public class 异常 {
	public static void main(String[] args) {
		
		Demo de = new Demo();
		
		try {
			int num = de.div(3,0);
		
			System.out.println(num); //被除数不能为零。
		}
		catch (Exception e) {
//			System.out.println("出现异常");
			System.out.println(e.getMessage()); // 获取异常信息；
			e.printStackTrace(); // 获取异常名字 + 信息 + 位置  JVM默认处理收到异常就调用这个方法。信息显示在屏幕上。
		}
		
		System.out.println("是否执行！！");
		
	}

}

class Demo	{
	
	int div (int a , int b) throws Exception{
		if(b==0) {
		throw new ArithmeticException("分母不能为零");	// 程序员抛出异常
			}
		return a/b;
		}
	
	}
~~~



### ▲  throw 和  throws 的区别。

​	1、位置不同。

​		throws 用在函数上，后面跟的是异常类，可以跟多个。

​		throw 用在函数内，后面跟的是异常对象。

​	2、功能不同。

​		throws 用来声明异常，让调用者只知道该功能可能出现的问题，并由调用者可以给出预先的处理方式。

​		throw 抛出具体问题对象。执行到 throw 功能就已经结束了，跳转到调用者。并将具体的问题对象也抛给调用者。

【扩展】： throw 语句独立存在时，下面不要定义其他语句。因为执行不到。

### 异常的原则：

​	1、功能內部有异常 throw 抛出，功能上一定要 throws 声明。

​		—— 内部抛什么，功能就声明什么。

​		—— 声明的目的就是为了让调用者处理，如果调用者不处理，编译失败。

​	2、特殊情况：

​		—— 当函数内通过 throw 抛出了 RuntimeException 及其子类的异常对象时，函数上可以不用 throws 声明。

​		—— 不声明的目的是为了不让调用者处理。直接让调用者的程序停止（因为如果对其处理，在后面函数调用该变量、函数可能出错），要对代码进行修改。





 

 