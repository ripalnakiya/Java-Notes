# Object Oriented Programming

```java
class Rectangle
{
    private int length;
    private int breadth;

    public Rectangle()
    {
        length = 1;
        breadth = 1;
    }

    public Rectangle(int l, int b)
    {
        length = l;
        breadth = b;
    }

    public int area()
    {
        return length * breadth;
    }
}

public class MyRectangle
{
    public static void main(String[] args) {
        Rectangle r1 = new Rectangle(5,10);
        System.out.println(r1.area());          => 50
    }
}
```
