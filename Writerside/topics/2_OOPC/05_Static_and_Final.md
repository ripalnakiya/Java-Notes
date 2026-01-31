# Static and Final keywords

## Static

    Static Variables, Static Methods, Static Inner Classes, Static Blocks

Static keywords is useful for representing information or data about the class.

Static Keyword is used for representing Meta Data (data about data).

It is useful for representing the information of a class.

Static members belongs to a class and they can be shared by all the objects of the class and all the objects have their own non-static members.

All the object can use the static variable as a shared data.

Static members can be accessed just by using class name.

The static members of a class are created in the method area.

Static methods can access only static members.

## Static Block

Set of statements are written in the form of blocks and are made static.

It is used to initialise static data member.

It is executed before the main method at the time of class loading.

```Java
public class Main {
    static
    {
        System.out.println("Block 1");
    }
    public static void main(String[] args)
    {
        System.out.println("Main");
    }
    static
    {
        System.out.println("Block 2");
    }
}
```

Output:

```shell
Block 1
Block 2
Main
```

---

```Java
class Test
{
    static
    {
        System.out.println("Block 1");
    }
    static
    {
        System.out.println("Block 2");
    }
}

public class Main {
    public static void main(String[] args) {
        System.out.println("Main");
    }
}
```

Output:

```shell
Main
```

Since, `class` Test is not used, so it won't execute it's static members.

## Final

    Final Variable, Final Method, Final Class

Value of `final` variables are fixed,that is once the value is assigned then it can’t be modified.

`final` variables are written in capital letters.

`final` variable can be initialised **:**

- During the declaration of the variable
- Inside intance block (just a block of curly brackets)
- Inside a static block (`main` method is also `static`), if the variable is also declared `static`
- Inside the constructor of class.
  - As constructors can be overloaded, so the final variable must be initialised in every constructor.

```Java
class Test
{
    final int LOW = 0;

    // This is not allowed, it will generate error.
    final int MIN;
    MIN = 1;

    final int AVG;
    {
        AVG = 5;
    }

    static final int MAX;
    static
    {
        // we cannot initialize/use non-static member in static block/method
        MAX = 9;
    }
    // also
    static void fun()
    {
        final int MAX;
        MAX = 9;
    }

    final int HIGH;
    Test()
    {
        HIGH = 10;
    }
    Test(int x)
    {
        HIGH = 10;
    }
}
```

It is not necessary to declare and initialize the final variable in the same statement.

---

`final` method cannot be overridden.

- It is used to restrict Polymorphism.

`final` class cannot be extended.

- It is used to restrict Inheritance.

## Singleton Class

A class which can create only one object is called singleton class.

Constructors are made private and object of the singleton class is created in static method of that class.

In singleton class getInstance() method is used.

```Java
class CoffeeMachine {
    private float coffeeQ;
    private float waterQ;

    static private CoffeeMachine machine = null;

    static CoffeeMachine getInstance() {
        // This insures that object is created only once.
        if (machine == null)
            machine = new CoffeeMachine();
        return machine;
    }
}

class Main{
    public static void main(String[] args){
        CoffeeMachine m1 = CoffeeMachine.getInstance();
        CoffeeMachine m2 = CoffeeMachine.getInstance();
        CoffeeMachine m3 = CoffeeMachine.getInstance();

        // All three references point to the same object.

        if(m1 == m2 && m1 == m3)
            System.out.println("Same");
    }
}
```

Output:

```shell
Same
```

