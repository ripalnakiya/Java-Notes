# Abstract Classes

There are two types of classes Abstract class and Concrete class.

If `abstract` keyword is used before the class then it is an Abstract
Class

If nothing is written before class then it is a Concrete class.

Object of an Abstract class cannot be created but object of Concrete
class can be created.

Reference of abstract class is allowed.

```Java
abstract class Base
{
    Base()
    {
        System.out.println("Base Constructor");
    }

    void method1()
    {
        System.out.println("Method 1 called");
    }

    abstract void method2();
}

class Derived extends Base
{
    void method2()
    {
        System.out.println("Method 2 called");
    }
}

public class Main{
    public static void main(String[] args) {
        Base b;                         // Reference of abstract class is allowed
        Derived d = new Derived();
    }
}
```

Method which is not having a body is known as **Abstract** method, and the method must be declared as `abstract`.

The abstract method is undefined method.

A class is Abstract class if at least one of the methods is abstract, and we has to declare that class as `abstract`.

Already declared `abstract` class is allowed to not to contain any abstract method.

If any other class inherits abstract class then that class also becomes abstract class, but to make the subclass as concrete class it must override all the undefined(abstract) methods.

- Abstract classes are used for imposing standards and sharing methods

- Sub classes are meant for following those standards

Abstract Class and method both, can neither be final nor static.

Abstract Classes are used for implementing **Inheritance** as well as **Polymorphism**.

Inheritance -> Concrete Methods

Polymorphism -> Abstract Methods
