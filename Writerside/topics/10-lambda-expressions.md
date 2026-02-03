# Lambda Expressions

Lambda expressions are used for defining 
anonymous expressions or nameless methods or functions.

Lambda expressions are defined with the help of interfaces.

If a interface have single abstract method 
then it is called the **functional interface**.

```Java
@FunctionalInterface
interface MyLambda {
    public void display();
}

public class Main {
    public static void main(String[] args) {
        // Anonymous Method itself is acting as object
        MyLambda obj = () -> {
            System.out.println("Hello World")
        };
        // Here, We're overriding the display()

        // Since, it contains only single statement, we can also write it as
        MyLambda obj = () -> System.out.println("Hello World");

        obj.display();
    }
}
```

## Passing Parameters

```Java
@FunctionalInterface
interface MyLambda {
    public void display(String str);
}

public class Main {
    public static void main(String[] args) {
        MyLambda obj = (s) -> System.out.println(s);

        obj.display("Hello World");
    }
}
```

## Returning Value

```Java
@FunctionalInterface
interface MyLambda {
    public int add(int a, int b);
}

public class Main{
    public static void main(String[] args) {
        MyLambda obj = (a,b) -> {
            return a + b;
        };

        int result = obj.add(10,20);

        System.out.println(result);
    }
}
```

## Variables Capture

Lambda Expression can access/capture variables of the method they're defined in... 

but those variables should be final or effectively final 
(i.e. those variables should be constants)

```Java
@FunctionalInterface
interface MyLambda {
    public void display();
}

class Demo {
    int temp = 10;  // This is a instance variable

    public void method1() {
        int num = 5;
        MyLambda obj = () -> {
            System.out.println(num);
            num++;  // Not Allowed to modify the variable, it should be final

            // Instance variables can directly be used (Withough being final)
            System.out.println(temp);
            temp++; // Hence, instance variables can be modified as well
        };
        num++;  // Not allowed, if we want to use it inside of lambda
    }
}

public class Main {
    public static void main(String[] args) {
        Demo d = new Demo();
        d.method1();
    }
}
```

## Lambda Expression as Parameter

```Java
@FunctionalInterface
interface Operation {
    int apply(int a, int b);
}

class Calculator {

    static int calculate(int x, int y, Operation op) {
        return op.apply(x, y);
    }
}

public class Main {
    public static void main(String[] args) {

        int sum = Calculator.calculate(10, 5, (a, b) -> a + b);
        int diff = Calculator.calculate(10, 5, (a, b) -> a - b);
        int product = Calculator.calculate(10, 5, (a, b) -> a * b);

        System.out.println(sum);      // 15
        System.out.println(diff);     // 5
        System.out.println(product);  // 50
    }
}
```

## Method Reference

If lambda looks like this:

```Java
(x) -> someMethod(x)
```

Java allows to replace it with:

```Java
ClassName::someMethod
```

We can use method reference to call a method.

```Java
@FunctionalInterface
interface MyLambda {
    public void display(String str);
}

public class Main {
    Main() {};
    
    Main(String str) {
        System.out.println(str);
    }

    void upper(String str) {
        System.out.println(str.toUpperCase());
    }

    static void reverse(String str) {
        StringBuffer sb = new StringBuffer(str);
        sb.reverse();
        System.out.println(sb);
    }

    public static void main(String[] args) {
        Main mn = new Main();
        
        MyLambda object1 = mn::upper; // Calling method of a class
        object1.display("hello world"); // HELLO WORLD
        
        MyLambda object2 = System.out::println; // Calling a method of a class
        object2.display("Hello World"); // Hello World
        
        MyLambda object13 = Main::reverse;  // Calling a static method of a class
        object13.display("Hello World"); // dlroW olleH
        
        MyLambda object4 = Main::new;   // Calling a constructor of a class
        object4.display("Hello World"); // Hello World
    }
}
```

Method Reference with parameters

```Java
@FunctionalInterface
interface MyLambda {
    public int display(String str1, String str2);
}

public class Main {
    public static void main(String[] args) {
        MyLambda object = String::compareTo;

        // The display() internally calls compareTo() method
        System.out.println(object.display("Hello", "Hello"));  // 0
        System.out.println(object.display("Hello", "World"));  // -15
    }
}
```
