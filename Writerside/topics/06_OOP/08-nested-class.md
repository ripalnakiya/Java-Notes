# Nested Class

A class can have three type of **members**: variables, methods and inner classes.

```Java
class Outer {
    int x;

    void show() {
        // Implementation
    }

    class Inner {
        // Implementation
    }
}
```

All access modifiers can be used on the **members** of the class.

But, **Outer (top-level) class →** `public` or `default` only

> **Nested / inner classes →** can be `private`, `protected`, `public`, or `default`

## Static Nested Class

- Declared `static` inside another class.
- Does NOT need an instance of the outer class to be created.
- Can access static members of the outer class directly, but not non-static members.

```Java
class Outer {
    static int x = 10;

    static class Nested {
        void show() {
            System.out.println("x = " + x);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Outer.Nested obj = new Outer.Nested();
        obj.show();  // prints 10
    }
}
```

## Inner Class (Non-static nested class)

- Declared without `static` inside a class.
- **Needs an instance** of the **outer class** to be created.
- Can **access** both **static and non-static members** of the outer class.

```Java
class Outer {
    int y = 20;

    class Inner {
        void show() {
            System.out.println("y = " + y);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Outer outer = new Outer();
        Outer.Inner inner = outer.new Inner();
        inner.show();  // prints 20
    }
}
```

## Local Inner Class

- Defined inside a method of a class.
- Scope is limited to the method.
- Can access final or effectively final local variables of the method.

```Java
class Outer {
    void display() {
        int num = 30;
        class LocalInner {
            void show() {
                System.out.println("num = " + num);
            }
        }
        LocalInner li = new LocalInner();
        li.show();
    }
}
```

## Anonymous Inner Class

- No name, used once to create an object.
- Often used to implement interfaces or extend classes on the fly.

```Java
interface Greeting {
    void sayHello();
}

public class Main {
    public static void main(String[] args) {
        Greeting g = new Greeting() {
            public void sayHello() {
                System.out.println("Hello!");
            }
        };
        g.sayHello();
    }
}
```
