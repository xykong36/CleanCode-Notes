## Objects and Data Structures

需要理解abstraction的威力 抽象和分层是计算机的核心概念

软件中的分层是将问题组织起来的方式 如果我们想要制作一个复杂的系统 我们必须要有一种方式来组织我们的代码

* [Simple way to understand abstraction and encapsulation](https://stackoverflow.com/a/23032098)
* [How much abstraction is too much?](https://stackoverflow.com/a/15467758/8629112)
* [Difference between abstraction and encapsulation?](https://stackoverflow.com/a/743698/8629112)
* [Why use getters and setters/accessors?](https://stackoverflow.com/a/1568230/8629112)

### Data Abstraction

6-1 直接将数据结构通过public data field暴露

6-2 只暴露可以操作数据的方法，而不暴露数据结构，隐藏了内部实现 => 强制规定访问规则 可以读取某一个坐标的x值或y值，但必须同时设置一组坐标

Listing 6-1 Concrete Point
```java
public class Point {
  public double x;
  public double y;
}
```

Listing 6-2 Abstract Point

```java
// hide the implementations + enforce an access policy
public interface Point {
  double getX(); 
  double getY();
  void setCartesian(double x, double y);
  double getR();
  double getTheta();
  void setPolar(double r, double theta);
}
```




### Data/Object Anti-Symmetry

OOP: 添加Data容易 修改难
FP: 添加难 修改容易

|         | OOP          | FP  |
| ------------- |:-------------:| -----:|
| 添加Data     | 容易 | 难 |
| 修改Data      | 难      |   容易 |

天然的一对矛盾 

Procedural code(code using data structures) makes it easy to add new functions without changing the existing data structures.

OO code makes it easy to add new classes without changing existing functions.

对比objects 和 data structures区别的例子
```java

// FP
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

// OOP
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

### The Law of Demeter
```java
final String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath();

Options opts = ctxt.getOptions();
File scratchDir = opts.getScratchDir();
final String outputDir = scratchDir.getAbsolutePath();
```

### Data Transfer Objects

```java
public class Address {
    private String street;
    private String streetExtra;
    private String city;
    private String state;
    private String zip;

    public Address(String street, String streetExtra,
                   String city, String state, String zip) {
        this.street = street;
        this.streetExtra = streetExtra;
        this.city = city;
        this.state = state;
        this.zip = zip;
    }

    public String getStreet() {
        return street;
    }

    public String getStreetExtra() {
        return streetExtra;
    }

    public String getCity() {
        return city;
    }

    public String getState() {
        return state;
    }

    public String getZip() {
        return zip;
    }
}
```

