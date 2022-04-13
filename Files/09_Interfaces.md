# Interfaces

Interfaces are used for implementing **Polymorphism**.

Inheritances are used for borrowing methods.

Consider this abstract class:

```java
abstract class Base {
    abstract public void method1();
    abstract public void method2();
}

class Derived extends Base
{
    public void method1()
    {
        // Implementation
    }

    public void method2()
    {
        // Implementation
    }
}
```

When an `abstract` class has all methods defined as `abstract`, then it is used purely for implementing **Polymorphism**.

Derived class, has to implement all the `abstract` methods to become concrete class.

Interface can be call as Abstract Class with all abstract methods

Above class can be written using Interfaces in the same way:

```java
interface Base {
    void method1();
    void method2();
}

class Derived implements Base
{
    public void method1()
    {
        //
    }

    public void method2()
    {
        //
    }
}
```

Classes are extended, Interfaces are implemented.

A class can be extended from only one class, and can implement multiple interfaces.

In abstract class, we can create abstract class reference and assign the derived class object.

In Interfaces also, we can create reference of interface and assign the object of class, which implemented the interface.

## Interface Examples

We can also define our own extra methods in derived class.

```java
class Phone {
    public void call(){System.out.println("Phone call");}
    public void SMS(){System.out.println("Phone SMS");}
}

interface Icamera {
    void click();
    void record();
}

interface IMusicPlayer {
    void play();
    void pause();
}

class Smartphone extends Phone implements ICamera, IMusicPlayer {
    public void click(){System.out.println("Camera Click");}
    public void record(){System.out.println("Camera Record");}

    public void play(){System.out.println("Music Play");}
    public void pause(){System.out.println("Music Pause");}

    public void videoCall(){System.out.println("Smartphone Video Call");}
}

public class Main {
    public static void main(String[] args) {
        Smartphone s = new Smartphone();
        s.call();
        s.SMS();
        s.click();
        s.record();
        s.play();
        s.pause();
        s.videoCall();

        Phone p = new Smartphone();
        p.call();
        p.SMS();

        ICamera c = new Smartphone();
        c.click();
        c.record();

        IMusicPlayer m = new IMusicPlayer();
        m.play();
        m.pause();
    }
}
```

## Callbacks using Interface

Interfaces are used for defining callback methods.

```java
interface Member {
    public void callback();
}

class Store {
    // Creating array of references of Member
    Member members = new Member[100];
    int counter = 0;

    void register(Member m){
        members[counter++] = m;
    }

    void inviteSale(){
        for(int i = 0; i < counter ; i++)
            members[i].inviteSale();
    }
}

class Customer implements Member {
    String name;

    Customer(String name){
        this.name = name;
    }

    void inviteSale(){
        System.out.println("I'll Visit, " + name);
    }
}

public class Main {
    public static void main(String[] args) {
        Store s = new Store();
        Customer c1 = new Customer("Jack");
        Customer c2 = new Customer("John");

        s.register(c1);
        s.register(c2);

        s.inviteSale();                 => I'll visit, Jack
                                           I'll visit, John
    }
}
```

## Interface Rules

Methods are `public` and `abstract` by default in Interfaces.

    We cannot make abstract classes in Interfaces as `private`.

---

We can have Identifiers in the interface, and they are `final` and `static`, but the identiAiers must be given name in Upper case.

Methods inside an interface cannot have body, but a method can
have body if the method is `static`.

    And we can access the static members using Interface name and dot operator.

---

We can also have `default` methods inside the interface(they have their body defined inside interface).

We can override the `default` method, but if we don't override then also they are **accessible**.

    `default` methods are useful when, we already have implemented the interface in many classes.

    If we want to add one more method in Interface, then all the implementing classes will have to implement that new method as well(otherwise they will become `abstract` classes).

    So, instead we can define that method inside the interface using `default` keyword, and then we don't need to implement it in all those classses.

---

We can also define `private` methods in the interface (`private` methods that are **not** `abstract`).

    private methods are useful inside the default method, they are not useful outside the interface.

---

Interface can extend from another Interface.

## Cpp vs Java

In C++, one class can inherit from multiple classes(Multiple Inheritance).

But in Java, one class can inherit from only one class.

Multiple Inheritance in java is achieved using Interfaces.
