# Abstract Classes
<show-structure depth="2"/>

| Concrete Class               | Abstract Class                     |
|------------------------------|------------------------------------|
| Regular class                | Class that uses `abstract` keyword |
| Objects **can** be created   | Objects **cannot** be created      |
| Reference **can** be created | Reference **can** be created       |

```Java
abstract class Base {
    Base() {
        System.out.println("Base Constructor");
    }

    void method1() {
        System.out.println("Method 1 called");
    }

    abstract void method2();
}

class Derived extends Base {
    void method2() {
        System.out.println("Method 2 called");
    }
}

public class Main {
    public static void main(String[] args) {
        // Reference of abstract class is allowed
        Base b;
        
        // Reference and object of concrete class is allowed
        Derived d = new Derived();
    }
}
```

## Abstract Method

Method which is not having a body is known as **Abstract** method, 
and the method must be declared as `abstract`.

The abstract method is undefined method.

## Abstract Class

A class is Abstract class if **at least one of the methods is abstract**, 
and we has to declare that class as `abstract`.

Though, already declared `abstract` class is allowed to not contain any abstract method.

## Inheriting from abstract class

If any other class inherits abstract class 
then that class also becomes abstract class...

but to make the subclass as concrete class 
it must override all the abstract methods.

> Abstract classes are used for imposing standards and sharing methods,
>
> Subclasses are meant for following those standards.
{style="note"}

Abstract Class and abstract methods, can neither be `final` nor `static`.

- Abstract Classes are used for implementing **Inheritance** as well as **Polymorphism**.
  - **Inheritance:** using Concrete Methods
  - **Polymorphism:** using Abstract Methods
