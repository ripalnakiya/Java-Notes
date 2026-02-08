# Singleton
<show-structure depth="2"/>

A class which can create only one object is called **singleton class**.

Constructors are made `private` 
and object of the singleton class is created in `static` method of that class.

In singleton class, `getInstance()` method is used.

> Here, we never make a **static object**.
> 
> We make a **static reference** that points to an object on the heap.
{style="warning"}

```Java
class Singleton {
    private static Singleton instance = new Singleton();

    private Singleton() {}

    public static Singleton getInstance() {
        return instance;
    }
}
```

Because the reference is static:
- it’s reachable for the entire program lifetime
- the object cannot be garbage collected
- heap memory is held for entire JVM runtime

## Lazy Singleton

```Java
class Singleton {
    private static Singleton instance;

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

**Difference:**

- object creation is delayed
- lifetime is still entire program runtime after creation

Lazy does not mean short-lived. It just means procrastination.

## Example

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

class Main {
    public static void main(String[] args) {
        CoffeeMachine m1 = CoffeeMachine.getInstance();
        CoffeeMachine m2 = CoffeeMachine.getInstance();
        CoffeeMachine m3 = CoffeeMachine.getInstance();

        // All three references point to the same object.

        if (m1 == m2 && m1 == m3)
            System.out.println("Same");
    }
}
```

Output:

```shell
Same
```
