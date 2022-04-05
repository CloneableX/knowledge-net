- 详情可查看 [Record Class](https://docs.oracle.com/en/java/javase/15/language/records.html)
- Java SE 14 的 preview feature
- Record Class 会声明并自动创建一组 fields，构造方法，equals，hashCode 和 toString 方法
	- ```java
	  record Rectangle(double length, double width) {}
	  ```
	- 将编译为
	- ```java
	  public final class Rectangle {
	      private final double length;
	      private final double width;
	  
	      public Rectangle(double length, double width) {
	          this.length = length;
	          this.width = width;
	      }
	  
	      double length() { return this.length; }
	      double width()  { return this.width; }
	  
	      // Implementation of equals() and hashCode(), which specify
	      // that two record objects are equal if they
	      // are of the same type and contain equal field values.
	      public boolean equals...
	      public int hashCode...
	  
	      // An implementation of toString() that returns a string
	      // representation of all the record class's fields,
	      // including their names.
	      public String toString() {...}
	  }
	  ```
- 如果要对构造参数有所限制，可以使用 compact constructor
- 在 Record Class 内部能够声明 static 的变量，方法及构造方法，声明的实例方法不能为私有方法
- Record Class 可以使用泛型，也可以实现接口，甚至可以使用注解
	- 应用在 Record Class 上的注解会被自动应用至多个地方，包括构造方法参数、components、私有的变量及变量的相应访问方法上
	- 所以声明注解时需要准确描述作用的目标
- Record Class 可以声明在方法体中
- Record Class 也可以被序列化