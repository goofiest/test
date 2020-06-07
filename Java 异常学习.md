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
			System.out.println("出现异常");
		}
		
		
	}

}

class Demo	{
	
	int div (int a , int b) throws Exception{
		
		return a/b;
		}
	
	}
~~~



 

