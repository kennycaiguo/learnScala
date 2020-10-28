# learnScala
# Scala hello world实例
object HelloWorld {
    def main(args: Array[String]): Unit = {
        println("Hello, world!")
    }
}
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

