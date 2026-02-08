# Inheritance
<show-structure depth="2"/>

```Java
class Circle {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    public double circumference() {return 2 * Math.PI * radius;}
    public double area() {return Math.PI*radius * radius;}
}

class Cylinder extends Circle {
    private double height;
    public volume(){return area() * height;}
}
```

Java inheritance is always **public inheritance** behavior. 

(Java inheritance ≈ C++ `public` inheritance)

## Access Control

A derived class **inherits all accessible members** of the base class.

This includes **public and protected** members, 
as well as package-private members when the subclass is in the same package.

**Private members** of the base class are **not accessible** 
and are **not inherited** in the sense of direct use,
but they still exist as part of the base-class portion of the derived object, 
and therefore contribute to the size and state of the derived object.

Private members can be accessed only through public or protected methods provided by the base class.

[Visit C++ Reference](https://ripalnakiya.github.io/Cpp-Notes/04-inheritance.html#access-control)

## Constructors in Inheritance

Parameterised constructor of base class 
must be explicitly called from derived class constructor.

```Java
class Base {
    public Base(){ System.out.println("Non Param of Base "); }
    public Base(int x){ System.out.println("Param of Base " + x); }
}

class Derived extends Base {
    public Derived(){ System.out.println("Non Param of Derived "); }
    public Derived(int y){ System.out.println("Param of Derived " + y); }

    public Derived(int x, int y){
        super(x);
        System.out.println("2 Param of Derived " + y);
    }
}
```

`super` is a reference to the parent class.

- It is used to:
  - Call parent constructor
  - Access parent fields
  - Call parent methods

Here, `super()` is used to call a superclass parameterized constructor.

It can also be used to access data members of super class from derived class.

```Java
class Base {
    int x = 10;
}

class Derived extends Base {
    int x = 20;

    void printValues() {
        System.out.println(super.x);            // 10
        System.out.println(x);                  // 20
    }
}
```

## Method Overriding

When we redefine a Base class method inside the Derived class, 
it is called method overriding.

- `final` and `static` methods cannot be overridden.
- Method can be overridden with same or lenient (`public`, `protected`) access
  specifiers but the stricter(`private`) access specifiers cannot be used in sub class.

Method Overriding, shadows the Base class method.

```Java
class Base {
    public void display() {
        System.out.println("Base Class Display");
    }
}

class Derived extends Base {
    public void display() {
        System.out.println("Derived Class Display");
    }
}

class Main {
    public static void main(String[] args) {
        Base b = new Base();
        b.display();                    // Base Class Display

        Derived d = new Derived();
        d.display();                    // Derived Class Display
    }
}
```

Invalid Ways of Overriding Methods:

```Java
class Base {
    public void Display() {
        System.out.println("Base Class Display");
    }
}

class Derived extends Base {
    public void Display(int x) {
        System.out.println("Derived Class Display");
    }
}
```

Here, `Display()` is not **overrided**, But they are **overloaded**.

```Java
class Base {
    public void Display() {
        System.out.println("Base Class Display");
    }
}

class Derived extends Base {
    public int Display(int x) {
        System.out.println("Derived Class Display");
    }
}
```

This will generate error, since the return types are different.

## Dynamic Method Dispatch

```Java
class Base {
    public void display() {
        System.out.println("Base Class Display");
    }
}

class Derived extends Base {
    public void display() {
        System.out.println("Derived Class Display");
    }
}

class Main {
    public static void main(String[] args) {
        Base b = new Derived();
        b.display();              // Derived Class Display
    }
}
```

We're having reference of Base class, and have assigned Derived class object.

It will work almost the same way as if we have assigned Base class object.

But Since, we're calling Base class method, 
and already have overrided that Base class method in the Derived class.

So, derived class method will be called.

Read this example code:

```Java
class Base {
    public void function1() {
        System.out.println("Base Function 1");
    }

    public void function2() {
        System.out.println("Base Function 2");
    }
}

class Derived extends Base {
    public void function2() {
        System.out.println("Derived Function 2");
    }

    public void function3() {
        System.out.println("Derived Function 3");
    }
}

class Main {
    public static void main(String[] args) {
        // Case 1
        Base b = new Base();
        b.function1();                          // Base Function 1
        b.function2();                          // Base Function 2

        // Case 2
        Derived d = new Derived();
        d.function1();                          // Base Function 1
        d.function2();                          // Derived Function 2 (function2() of Base is overrided, so function2() of Derived is called)
        d.function3();                          // Derived Function 3

        // Case 3
        Base b = new Derived();
        b.function1();                          // Base Function 1
        b.function2();                          // Derived Function 2 (Dynamic Method Dispatch)
        b.function3();                          // Invalid
    }
}
```

In `Case 3`,

Since, we have Base class reference, we can only call Base class methods. Therefore, `function3()` cannot be called.

We can call `function2()` with `b`, but since, `function2()` is **overridden** in Derived class, 
So Derived class `function2()` is called.

Java decides at runtime which `function2()` has to be called, based on the actual object.

[Visit C++ Reference](https://ripalnakiya.github.io/Cpp-Notes/05-polymorphism.html#virtual-functions)
