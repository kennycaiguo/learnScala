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
