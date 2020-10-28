# learnScala
# Scala hello world实例
object HelloWorld {
    def main(args: Array[String]): Unit = {
        println("Hello, world!")
    }
}
# scala中的集合
Scala Collection
Scala提供了一套很好的集合实现，提供了一些集合类型的抽象。

Scala 集合分为可变的和不可变的集合。

可变集合可以在适当的地方被更新或扩展。这意味着你可以修改，添加，移除一个集合的元素。

而不可变集合类，相比之下，永远不会改变。不过，你仍然可以模拟添加，移除或更新操作。但是这些操作将在每一种情况下都返回一个新的集合，同时使原来的集合不发生改变。

接下来我们将为大家介绍几种常用集合类型的应用：

序号	集合及描述
1	Scala List(列表)
List的特征是其元素以线性方式存储，集合中可以存放重复对象。
Scala List(列表)
Scala 集合 Scala 集合

Scala 列表类似于数组，它们所有元素的类型都相同，但是它们也有所不同：列表是不可变的，值一旦被定义了就不能改变，其次列表 具有递归的结构（也就是链接表结构）而数组不是。。

列表的元素类型 T 可以写成 List[T]。例如，以下列出了多种类型的列表：

实例
// 字符串列表
val site: List[String] = List("Runoob", "Google", "Baidu")

// 整型列表
val nums: List[Int] = List(1, 2, 3, 4)

// 空列表
val empty: List[Nothing] = List()

// 二维列表
val dim: List[List[Int]] =
   List(
      List(1, 0, 0),
      List(0, 1, 0),
      List(0, 0, 1)
   )
构造列表的两个基本单位是 Nil 和 ::

Nil 也可以表示为一个空列表。

以上实例我们可以写成如下所示：

实例
// 字符串列表
val site = "Runoob" :: ("Google" :: ("Baidu" :: Nil))

// 整型列表
val nums = 1 :: (2 :: (3 :: (4 :: Nil)))

// 空列表
val empty = Nil

// 二维列表
val dim = (1 :: (0 :: (0 :: Nil))) ::
          (0 :: (1 :: (0 :: Nil))) ::
          (0 :: (0 :: (1 :: Nil))) :: Nil
列表基本操作
Scala列表有三个基本操作：

head 返回列表第一个元素
tail 返回一个列表，包含除了第一元素之外的其他元素
isEmpty 在列表为空时返回true
对于Scala列表的任何操作都可以使用这三个基本操作来表达。实例如下:

实例
// 字符串列表
object Test {
   def main(args: Array[String]) {
      val site = "Runoob" :: ("Google" :: ("Baidu" :: Nil))
      val nums = Nil

      println( "第一网站是 : " + site.head )
      println( "最后一个网站是 : " + site.tail )
      println( "查看列表 site 是否为空 : " + site.isEmpty )
      println( "查看 nums 是否为空 : " + nums.isEmpty )
   }
}
执行以上代码，输出结果为：

$ vim Test.scala 
$ scala Test.scala 
第一网站是 : Runoob
最后一个网站是 : List(Google, Baidu)
查看列表 site 是否为空 : false
查看 nums 是否为空 : true
连接列表
你可以使用 ::: 运算符或 List.:::() 方法或 List.concat() 方法来连接两个或多个列表。实例如下:

实例
object Test {
   def main(args: Array[String]) {
      val site1 = "Runoob" :: ("Google" :: ("Baidu" :: Nil))
      val site2 = "Facebook" :: ("Taobao" :: Nil)

      // 使用 ::: 运算符
      var fruit = site1 ::: site2
      println( "site1 ::: site2 : " + fruit )
     
      // 使用 List.:::() 方法
      fruit = site1.:::(site2)
      println( "site1.:::(site2) : " + fruit )

      // 使用 concat 方法
      fruit = List.concat(site1, site2)
      println( "List.concat(site1, site2) : " + fruit  )
     

   }
}
执行以上代码，输出结果为：

$ vim Test.scala 
$ scala Test.scala 
site1 ::: site2 : List(Runoob, Google, Baidu, Facebook, Taobao)
site1.:::(site2) : List(Facebook, Taobao, Runoob, Google, Baidu)
List.concat(site1, site2) : List(Runoob, Google, Baidu, Facebook, Taobao)
List.fill()
我们可以使用 List.fill() 方法来创建一个指定重复数量的元素列表：

实例
object Test {
   def main(args: Array[String]) {
      val site = List.fill(3)("Runoob") // 重复 Runoob 3次
      println( "site : " + site  )

      val num = List.fill(10)(2)         // 重复元素 2, 10 次
      println( "num : " + num  )
   }
}
执行以上代码，输出结果为：

$ vim Test.scala 
$ scala Test.scala 
site : List(Runoob, Runoob, Runoob)
num : List(2, 2, 2, 2, 2, 2, 2, 2, 2, 2)
List.tabulate()
List.tabulate() 方法是通过给定的函数来创建列表。

方法的第一个参数为元素的数量，可以是二维的，第二个参数为指定的函数，我们通过指定的函数计算结果并返回值插入到列表中，起始值为 0，实例如下：
实例
object Test {
   def main(args: Array[String]) {
      // 通过给定的函数创建 5 个元素
      val squares = List.tabulate(6)(n => n * n)
      println( "一维 : " + squares  )

      // 创建二维列表
      val mul = List.tabulate( 4,5 )( _ * _ )      
      println( "多维 : " + mul  )
   }
}
执行以上代码，输出结果为：

$ vim Test.scala 
$ scala Test.scala 
一维 : List(0, 1, 4, 9, 16, 25)
多维 : List(List(0, 0, 0, 0, 0), List(0, 1, 2, 3, 4), List(0, 2, 4, 6, 8), List(0, 3, 6, 9, 12))
List.reverse
List.reverse 用于将列表的顺序反转，实例如下：

实例
object Test {
   def main(args: Array[String]) {
      val site = "Runoob" :: ("Google" :: ("Baidu" :: Nil))
      println( "site 反转前 : " + site )

      println( "site 反转后 : " + site.reverse )
   }
}
执行以上代码，输出结果为：

$ vim Test.scala 
$ scala Test.scala 
site 反转前 : List(Runoob, Google, Baidu)
site 反转后 : List(Baidu, Google, Runoob)
Scala List 常用方法
下表列出了 Scala List 常用的方法：

序号	方法及描述
1	
def +:(elem: A): List[A]

为列表预添加元素

scala> val x = List(1)
x: List[Int] = List(1)

scala> val y = 2 +: x
y: List[Int] = List(2, 1)

scala> println(x)
List(1)
2	
def ::(x: A): List[A]

在列表开头添加元素

3	
def :::(prefix: List[A]): List[A]

在列表开头添加指定列表的元素

4	
def :+(elem: A): List[A]

复制添加元素后列表。

scala> val a = List(1)
a: List[Int] = List(1)

scala> val b = a :+ 2
b: List[Int] = List(1, 2)

scala> println(a)
List(1)
5	
def addString(b: StringBuilder): StringBuilder

将列表的所有元素添加到 StringBuilder

6	
def addString(b: StringBuilder, sep: String): StringBuilder

将列表的所有元素添加到 StringBuilder，并指定分隔符

7	
def apply(n: Int): A

通过列表索引获取元素

8	
def contains(elem: Any): Boolean

检测列表中是否包含指定的元素

9	
def copyToArray(xs: Array[A], start: Int, len: Int): Unit

将列表的元素复制到数组中。

10	
def distinct: List[A]

去除列表的重复元素，并返回新列表

11	
def drop(n: Int): List[A]

丢弃前n个元素，并返回新列表

12	
def dropRight(n: Int): List[A]

丢弃最后n个元素，并返回新列表

13	
def dropWhile(p: (A) => Boolean): List[A]

从左向右丢弃元素，直到条件p不成立

14	
def endsWith[B](that: Seq[B]): Boolean

检测列表是否以指定序列结尾

15	
def equals(that: Any): Boolean

判断是否相等

16	
def exists(p: (A) => Boolean): Boolean

判断列表中指定条件的元素是否存在。

判断l是否存在某个元素:

scala> l.exists(s => s == "Hah")
res7: Boolean = true
17	
def filter(p: (A) => Boolean): List[A]

输出符号指定条件的所有元素。

过滤出长度为3的元素:

scala> l.filter(s => s.length == 3)
res8: List[String] = List(Hah, WOW)
18	
def forall(p: (A) => Boolean): Boolean

检测所有元素。

例如：判断所有元素是否以"H"开头：

scala> l.forall(s => s.startsWith("H")) res10: Boolean = false
19	
def foreach(f: (A) => Unit): Unit

将函数应用到列表的所有元素

20	
def head: A

获取列表的第一个元素

21	
def indexOf(elem: A, from: Int): Int

从指定位置 from 开始查找元素第一次出现的位置

22	
def init: List[A]

返回所有元素，除了最后一个

23	
def intersect(that: Seq[A]): List[A]

计算多个集合的交集

24	
def isEmpty: Boolean

检测列表是否为空

25	
def iterator: Iterator[A]

创建一个新的迭代器来迭代元素

26	
def last: A

返回最后一个元素

27	
def lastIndexOf(elem: A, end: Int): Int

在指定的位置 end 开始查找元素最后出现的位置

28	
def length: Int

返回列表长度

29	
def map[B](f: (A) => B): List[B]

通过给定的方法将所有元素重新计算

30	
def max: A

查找最大元素

31	
def min: A

查找最小元素

32	
def mkString: String

列表所有元素作为字符串显示

33	
def mkString(sep: String): String

使用分隔符将列表所有元素作为字符串显示

34	
def reverse: List[A]

列表反转

35	
def sorted[B >: A]: List[A]

列表排序

36	
def startsWith[B](that: Seq[B], offset: Int): Boolean

检测列表在指定位置是否包含指定序列

37	
def sum: A

计算集合元素之和

38	
def tail: List[A]

返回所有元素，除了第一个

39	
def take(n: Int): List[A]

提取列表的前n个元素

40	
def takeRight(n: Int): List[A]

提取列表的后n个元素

41	
def toArray: Array[A]

列表转换为数组

42	
def toBuffer[B >: A]: Buffer[B]

返回缓冲区，包含了列表的所有元素

43	
def toMap[T, U]: Map[T, U]

List 转换为 Map

44	
def toSeq: Seq[A]

List 转换为 Seq

45	
def toSet[B >: A]: Set[B]

List 转换为 Set

46	
def toString(): String

列表转换为字符串

参考 API文档

2	Scala Set(集合)
Set是最简单的一种集合。集合中的对象不按特定的方式排序，并且没有重复对象。

参考 API文档

3	Scala Map(映射)
Map 是一种把键对象和值对象映射的集合，它的每一个元素都包含一对键对象和值对象。

参考 API文档

4	Scala 元组
元组是不同类型的值的集合

5	Scala Option
Option[T] 表示有可能包含值的容器，也可能不包含值。

6	Scala Iterator（迭代器）
迭代器不是一个容器，更确切的说是逐一访问容器内元素的方法。

实例
以下代码判断，演示了所有以上集合类型的定义实例：

// 定义整型 List
val x = List(1,2,3,4)

// 定义 Set
val x = Set(1,3,5,7)

// 定义 Map
val x = Map("one" -> 1, "two" -> 2, "three" -> 3)

// 创建两个不同类型元素的元组
val x = (10, "Runoob")

// 定义 Option
val x:Option[Int] = Some(5)
# scala中类的使用
## 实例1
1.创建一个MyMath类
MyMath.scala
class MyMath {
   def add(x:Int,y:Int):Int={
     x+y
   }
  def subtr(a:Int,b:Int):Int={
    a-b
  }
}

2.创建一个HelloWorld类，与MyMath类在同一个包下面，如果不是，需要使用Import语句导入
HelloWorld.scala
object HelloWorld{
  def main(args:Array[String]):Unit={
    /*var x =100;
     //println("hello Scala!!!"+x)
    var res = add(12,22)*/
    var math =new MyMath()
    var res = math.subtr(22,12)
    println("result="+res)
  }
  def add(a:Int,b:Int):Int={
    return a+b
  }

}

## 实例2
import java.io._

class Point(xc: Int, yc: Int) { 声明类的同时，实现构造函数
   var x: Int = xc
   var y: Int = yc

   def move(dx: Int, dy: Int) {
      x = x + dx
      y = y + dy
      println ("x 的坐标点: " + x);
      println ("y 的坐标点: " + y);
   }
}

object Test {
   def main(args: Array[String]) {
      val pt = new Point(10, 20);

      // 移到一个新的位置
      pt.move(10, 10);
   }
}
执行以上代码，输出结果为：

$ scalac Test.scala 
$ scala Test
x 的坐标点: 20
y 的坐标点: 30

# Scala 继承
## 实例1
Scala继承一个基类跟Java很相似, 但我们需要注意以下几点：

1、重写一个非抽象方法必须使用override修饰符。
2、只有主构造函数才可以往基类的构造函数里写参数。
3、在子类中重写超类的抽象方法时，你不需要使用override关键字。
接下来让我们来看个实例：

实例
class Point(xc: Int, yc: Int) {
   var x: Int = xc
   var y: Int = yc

   def move(dx: Int, dy: Int) {
      x = x + dx
      y = y + dy
      println ("x 的坐标点: " + x);
      println ("y 的坐标点: " + y);
   }
}

class Location(override val xc: Int, override val yc: Int,
   val zc :Int) extends Point(xc, yc){
   var z: Int = zc

   def move(dx: Int, dy: Int, dz: Int) {
      x = x + dx
      y = y + dy
      z = z + dz
      println ("x 的坐标点 : " + x);
      println ("y 的坐标点 : " + y);
      println ("z 的坐标点 : " + z);
   }
}
Scala 使用 extends 关键字来继承一个类。实例中 Location 类继承了 Point 类。Point 称为父类(基类)，Location 称为子类。

override val xc 为重写了父类的字段。

继承会继承父类的所有属性和方法，Scala 只允许继承一个父类。

## 实例2
Scala重写一个非抽象方法，必须用override修饰符。

实例
class Person {
  var name = ""
  override def toString = getClass.getName + "[name=" + name + "]"
}

class Employee extends Person {
  var salary = 0.0
  override def toString = super.toString + "[salary=" + salary + "]"
}

object Test extends App {
  val fred = new Employee
  fred.name = "Fred"
  fred.salary = 50000
  println(fred)
}

结果：Employee[name=Fred][salary=50000.0]

## Scala 单例对象
在 Scala 中，是没有 static 这个东西的，但是它也为我们提供了单例模式的实现方法，那就是使用关键字 object。

Scala 中使用单例模式时，除了定义的类之外，还要定义一个同名的 object 对象，它和类的区别是，object对象不能带参数。

当单例对象与某个类共享同一个名称时，他被称作是这个类的伴生对象：companion object。你必须在同一个源文件里定义类和它的伴生对象。类被称为是这个单例对象的伴生类：companion class。类和它的伴生对象可以互相访问其私有成员。
### 单例对象实例
单例对象实例
实例
import java.io._

class Point(val xc: Int, val yc: Int) {
   var x: Int = xc
   var y: Int = yc
   def move(dx: Int, dy: Int) {
      x = x + dx
      y = y + dy
   }
}

object Test {
   def main(args: Array[String]) {
      val point = new Point(10, 20)
      printPoint

      def printPoint{
         println ("x 的坐标点 : " + point.x);
         println ("y 的坐标点 : " + point.y);
      }
   }
}
执行以上代码，输出结果为：

$ scalac Test.scala 
$ scala Test
x 的坐标点 : 10
y 的坐标点 : 20

### 伴生对象实例
/* 文件名：Marker.scala
 * author:菜鸟教程
 * url:www.runoob.com
 */

// 私有构造方法
class Marker private(val color:String) {

  println("创建" + this)
 
  override def toString(): String = "颜色标记："+ color
 
}

// 伴生对象，与类名字相同，可以访问类的私有属性和方法
object Marker{
 
    private val markers: Map[String, Marker] = Map(
      "red" -> new Marker("red"),
      "blue" -> new Marker("blue"),
      "green" -> new Marker("green")
    )
   
    def apply(color:String) = {
      if(markers.contains(color)) markers(color) else null
    }
 
   
    def getMarker(color:String) = {
      if(markers.contains(color)) markers(color) else null
    }
    def main(args: Array[String]) {
        println(Marker("red"))  
        // 单例函数调用，省略了.(点)符号  
                println(Marker getMarker "blue")  
    }
}
执行以上代码，输出结果为：

$ scalac Marker.scala 
$ scala Marker
创建颜色标记：red
创建颜色标记：blue
创建颜色标记：green
颜色标记：red
颜色标记：blue
