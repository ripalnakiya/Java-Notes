# Lambda Expressions

Lambda expressions are used for de1ining anonymous expressions or nameless methods or functions.

Lambda expressions are defined with the help of interfaces.

If a interface have single abstract method then it is called the functional interface.

```Java
@FunctionalInterface
interface MyLambda {
    public void display();
}

public class Main{
    public static void main(String[] args) {
        // Anonymous Method itself is acting as object
        MyLambda obj = () -> {System.out.println("Hello World")};
        // Here, We're overriding the display()

        // Since, it contains only single statement, we can write it as
        MyLambda obj = () -> System.out.println("Hello World");

        obj.display();
    }
}
```

## Parameters and Returning

```Java
@FunctionalInterface
interface MyLambda {
    public void display(String str);
}

public class Main{
    public static void main(String[] args) {
        MyLambda obj = (s) -> System.out.println(s);

        obj.display("Hello World");
    }
}
```

```Java
@FunctionalInterface
interface MyLambda {
    public int add(int a, int b);
}

public class Main{
    public static void main(String[] args) {
        MyLambda obj = (a,b) -> return a+b;

        // We can also remove the return keyword
        MyLambda obj = (a,b) -> a+b;

        int result = obj.add(10,20);

        System.out.println(result);
    }
}
```

## Variables Capture

```Java
@FunctionalInterface
interface MyLambda {
    public void display();
}

class Demo{
    // This is a instance variable
    int temp=10;

    // This is a non static method
    public void method1(){
        int num = 5;
        MyLambda obj = () -> {
            int count=0;    // It acts like a local variable of a method
            count++;
            System.out.println(count);

            // Lambda Expression can use method variables
            // but they should be final or effectively final
            System.out.println(num);
            num++; // It is not allowed at all

            // Lambda Expression can use instance variables
            // Those variables can be modified as well
            System.out.println(temp);
            temp++;
        }
        num++;  // It is not allowed
                // If it is done then we can't use it inside lambda expression
    }
}

public class Main{
    public static void main(String[] args) {
        Demo d = new Demo();
        d.method1();
    }
}
```

Lamda Expressions can access/capture local variables only if they are declared `final` or are effectively final.
Also, those variables can never be modified inside the lamda expression.

## Lambda Expression as Parameter

```Java
@FunctionalInterface
interface MyLambda {
    public int add(int a, int b);
}


class UserLambda{
    public void callLambda(MyLambda ml){
        ml.display();
    }
}

class Demo{
    public void method1(){
        UserLambda ul = new UserLambda();

        // We can pass the lambda expression as parameter
        ul.callLambda((a,b) -> a+b);
    }
}

public class Main{
    public static void main(String[] args) {
        Demo d = new Demo();
        d.method1();
    }
}
```

## Method Reference

We can use method reference to call a method

```Java
@FunctionalInterface
interface MyLambda {
    public void display(String str);
}

public class Main{
    Main(String str){
        System.out.println(str);
    }

    void upper(String str){
        System.out.println(str.toUpperCase());
    }

    static void reverse(String str){
        StringBuffer sb = new StringBuffer(str);
        sb.reverse();
        System.out.println(sb);
    }

    public static void main(String[] args) {
        // Calling method of a class
        Main mn = new Main();
        MyLambda obj = mn::upper;
        obj.display("hello world");             => HELLO WORLD

        // Calling a method of a class
        MyLambda obj = System.out::println;
        obj.display("Hello World");             => Hello World

        // Calling a static method of a class
        MyLambda obj = Main::reverse;
        obj.display("Hello World");             => dlroW olleH

        // Calling a constructor of a class
        MyLambda obj = Main::new;
        obj.display("Hello World");             => Hello World
    }
}
```

---

Method Reference with parameters

```Java
@FunctionalInterface
interface MyLambda {
    public int display(String str1, String str2);
}

public class Main{
    public static void main(String[] args) {
        MyLambda obj = String::compareTo;

        // The display() internally calls compareTo() method
        System.out.println(obj.display("Hello", "Hello"));  => 0
        System.out.println(obj.display("Hello", "World"));  => -15
    }
}
```
