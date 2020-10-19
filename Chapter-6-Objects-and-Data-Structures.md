需要理解abstraction的威力 抽象和分层是计算机的核心概念，必须要理解

软件中的分层是将问题组织起来的方式 如果我们想要制作一个复杂的系统 我们必须要有一种方式来组织我们的代码

https://stackoverflow.com/a/23032098



对比6-1 和 6-2来理解Data Abstraction
6-1 直接将数据结构通过public data field暴露
6-2 只暴露可以操作数据的方法，而不暴露数据结构，隐藏了内部实现 => 强制规定访问规则 可以读取某一个坐标的x值或y值，但必须同时设置一组坐标


对于抽象的本质究竟是什么理解不足


6-2 interface still unmistakably represents a data structure.

Listing 6-1 Concrete Point
```java
public class Point {
  public double x;
  public double y;
}
```

Listing 6-2 Abstract Point
```java
public interface Point {
  double getX(); 
  double getY();
  void setCartesian(double x, double y);
  double getR();
  double getTheta();
  void setPolar(double r, double theta);
}
```


// 对比objects 和 data structures区别的例子
```java
public class Square {
    public Point topLeft;
    public double side;
}

public class Rectangle {
    public Point topLeft;
    public double height;
    public double width;
}

public class Circle {
    public Point center;
    public double radius;
}

public class Geometry {
    public final double PI = 3.141592653589793;

    public double area(Object shape) throws NoSuchShapeException {
        if (shape instanceof Square) {
            Square s = (Square) shape;
            return s.side * s.side;
        } else if (shape instanceof Rectangle) {
            Rectangle r = (Rectangle) shape;
            return r.height * r.width;
        } else if (shape instanceof Circle) {
            Circle c = (Circle) shape;
            return PI * c.radius * c.radius;
        }
        throw new NoSuchShapeException();
    }
}
```


好像和 OOP FP的核心有点关联

OOP: 添加容易 修改难
FP: 添加难 修改容易

天然的一对矛盾 

Procedural code(code using data structures) makes it easy to add new functions without changing the existing data structures.

OO code makes it easy to add new classes without changing existing functions.

```java
public class Square implements Shape {
    private Point topLeft;
    private double side;

    public double area() {
        return side * side;
    }
}

public class Rectangle implements Shape {
    private Point topLeft;
    private double height;
    private double width;

    public double area() {
        return height * width;
    }
}

public class Circle implements Shape {
    private Point center;
    private double radius;
    public final double PI = 3.141592653589793;

    public double area() {
        return PI * radius * radius;
    }
}
```

