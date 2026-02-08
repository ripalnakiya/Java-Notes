# Final
<show-structure depth="2"/>

    Final Variable, Final Method, Final Class

Value of `final` variables are fixed, 
that is once the value is assigned then it can’t be modified.

`final` variables are written in capital letters.

- `final` variable can be initialised:
  - During the declaration of the variable
  - Inside instance block (just a block of curly brackets)
  - Inside a static block (`main` method is also `static`), if the variable is also declared `static`
  - Inside the constructor of class
      - As constructors can be overloaded, so the final variable must be initialized in every constructor.

```Java
class Test {
    final int LOW = 0;

    // This is not allowed, it will generate error.
    final int MIN;
    MIN = 1;

    final int AVG;

    {
        AVG = 5;
    }

    static final int MAX;

    static {
        // we cannot initialize/use non-static member in static block/method
        MAX = 9;
    }

    // also
    static void fun() {
        final int MAX;
        MAX = 9;
    }

    final int HIGH;

    Test() {
        HIGH = 10;
    }

    Test(int x) {
        HIGH = 10;
    }
}
```

It is **not necessary** to declare and initialize 
the final variable in the same statement.

## Final in OOP

- `final` class cannot be **extended**.
  - It is used to restrict Inheritance.
- `final` method cannot be **overridden**.
  - It is used to restrict Polymorphism.
