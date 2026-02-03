# Interfaces

Interfaces are used for implementing **Polymorphism**.

Interfaces are used for borrowing methods.

Consider this abstract class:

```Java
abstract class Base {
    abstract public void method1();
    abstract public void method2();
}

class Derived extends Base {
    public void method1() {
        // Implementation
    }

    public void method2() {
        // Implementation
    }
}
```

When an `abstract` class has all methods defined as `abstract`, 
then it is used purely for implementing **Polymorphism**.

Derived class has to implement all the `abstract` methods to become concrete class.

**Interface** can be call as a Abstract Class with all abstract methods.

Previous class can be re-written using Interface:

```Java

interface Base {
    void method1();
    void method2();
}

class Derived implements Base {
    public void method1() {
        //
    }

    public void method2() {
        //
    }
}
```

Classes are **extended**, Interfaces are **implemented**.

A class can be extended from only one class, 
and can implement multiple interfaces.

**In abstract class,** we can create abstract class reference and assign the derived class object.

**In Interfaces also,** we can create reference of interface and assign the object of class, which implemented the interface.

## Interface Example

We can also define our own extra methods in derived class.

```Java
class Phone {
    public void call() {
        System.out.println("Phone call");
    }

    public void SMS() {
        System.out.println("Phone SMS");
    }
}

interface ICamera {
    void click();
    void record();
}

interface IMusicPlayer {
    void play();
    void pause();
}

class Smartphone extends Phone implements ICamera, IMusicPlayer {
    public void click() {
        System.out.println("Camera Click");
    }

    public void record() {
        System.out.println("Camera Record");
    }

    public void play() {
        System.out.println("Music Play");
    }

    public void pause() {
        System.out.println("Music Pause");
    }

    public void videoCall() {
        System.out.println("Smartphone Video Call");
    }
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

        IMusicPlayer m = new Smartphone();
        m.play();
        m.pause();
    }
}
```

## Callbacks using Interface

Interfaces are the go-to tool for callbacks 
because Java doesn’t have function pointers like C or lambdas in older versions.

Interfaces are used for defining callback methods.

```Java
interface TaskCompleteListener {
    void onTaskComplete(String result);
}

class Worker {
    private TaskCompleteListener listener;

    // Constructor or setter to register the callback
    public Worker(TaskCompleteListener listener) {
        this.listener = listener;
    }

    public void doWork() {
        System.out.println("Working...");
        // simulate work
        try { Thread.sleep(1000); } catch (InterruptedException e) {}
        // notify callback
        listener.onTaskComplete("Task finished!");
    }
}

public class Main {
    public static void main(String[] args) {
        TaskCompleteListener myListener = new TaskCompleteListener() {
            @Override
            public void onTaskComplete(String result) {
                System.out.println("Callback received: " + result);
            }
        };

        Worker worker = new Worker(myListener);
        worker.doWork();
    }
}
```

## Interface Rules

### Rule 1

Methods are `public` and `abstract` by default in Interfaces.

We cannot make abstract methods in Interfaces as `private`.

### Rule 2

We can have Identifiers in the interface, and they are `final` and `static`, 
but the identifiers must be given name in Upper case.

### Rule 3

Methods inside an interface cannot have body, but a method can
have body if the method is `static`.

And we can access the static members using Interface name and dot operator.

### Rule 4

We can also have `default` methods inside the interface 
(they have their body defined inside interface).

We can override the `default` method, 
but if we don't override then also they are **accessible**.

`default` methods are useful when, 
we already have implemented the interface in many classes.

If we want to add one more method in Interface, 
then all the implementing classes will have to 
implement that new method as well (otherwise they will become `abstract` classes).

So, instead we can define that method inside the interface 
using `default` keyword, and then we don't need to implement it in all those classes.

### Rule 5

We can also define `private` methods in the interface 
(`private` methods that are **not** `abstract`).

`private` methods are useful inside the default method, 
they are not useful outside the interface.

```Java
interface Vehicle {

    default void start() {
        log("Starting vehicle");
    }

    default void stop() {
        log("Stopping vehicle");
    }

    private void log(String msg) {
        System.out.println(msg);
    }
}
```

> So, a `private` method is a utility/helper function 
> for default or static methods inside the interface.

### Rule 6

Interface can **extend** from another Interface.
