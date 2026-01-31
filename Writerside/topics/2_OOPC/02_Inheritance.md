# Inheritance

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

All the members of Circle class will be **available** in the Cylinder class.

Object of Circle class will have size of 8 bytes.

Object of Cylinder class will have size of 16 bytes.

## Constructors in Inheritance

Parameterised constructor of base class must be explicitly called from derived class constructor.

```Java
class Base {
    public Base(){System.out.println("Non Param of Base ");}
    public Base(int x){System.out.println("Param of Base " + x);}
}

class Derived extends Base {
    public Derived(){System.out.println("Non Param of Derived ");}
    public Derived(int y){System.out.println("Param of Derived " + y);}

    public Derived(int x, int y){
        super(x);
        System.out.println("2 Param of Derived " + y);
    }
}
```

`super` keyword is used to refer to the parent class of a subclass.

It is a reference to the parent class.

Here, `super()` is used to call a superclass parameterised constructor.

It can also be used to access data members of super class from derived class.

```Java
class Base {
    int x = 10;
}

class Derived extends Base {
    int x = 20;

    void printValues() {
        System.out.println(super.x);            => 10
        System.out.println(x);                  => 20
    }
}
```

## Method Overriding

When we redefine a Base class Method inside Derived class, it is called method overriding.

- Final and static methods cannot be overridden.
- Method can be overridden with same or lenient (public, protected) access
  speciPiers but the stricter(private) access speciPiers cannot be used in sub
  class.

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
        b.display();                    => Base Class Display

        Derived d = new Derived();
        d.display();                    => Derived Class Display
    }
}
```

---

Invalid Ways of Overriding Methods :

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
        Base b = new Derive();
        b.display();                            => Derived Class Display
    }
}
```

We're having reference of Base class, and have assigned Derived class object.

It will work almost the same way as if we have assigned Base class object.

**But** when We're calling Base class method, and already have overrided that Base class method in the Derived class.

The derived class method will be called.

---

```Java
class Base {
    public void meth1()
    {
        System.out.println("Base Method 1 Display");
    }
    public void meth2()
    {
    S   ystem.out.println("Base Method 2 Display");
    }
}

class Derived extends Base {
    public void meth2()
    {
        System.out.println("Derived Method 2 Display");
    }
    public void meth3()
    {
        System.out.println("Derived Method 3 Display");
    }
}

class Main {
    public static void main(String[] args) {
        // Case 1
        Base b = new Base();
        b.meth1();                          => Base Method 1 Display
        b.meth2();                          => Base Method 2 Display

        // Case 2
        Derived d = new Derived();
        d.meth1();                          => Base Method 1 Display
        d.meth2();                          => Derived Method 2 Display
        // meth2() of Base is overrided, so meth2() of Derived is called
        d.meth3();                          => Derived Method 3 Display

        // Case 3
        Base b = new Derived();
        b.meth1();                          => Base Method 1 Display
        b.meth2();                          => Derived Method 2 Display
        b.meth3();                          // Invalid
    }
}
```

In case 3,

Since, we have Base class reference, we can only call Base class methods.

Therefore, `meth3()` cannot be called.

We can call `meth2()`, since we have this function defined in Base class.

But since, `meth2()` is **overridden** in Derived class, So Derived class `meth2()` is called.
