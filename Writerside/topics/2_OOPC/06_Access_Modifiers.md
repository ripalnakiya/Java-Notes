# Access Modifiers

Private :

- They are only accessible inside that class
- They are **not** accessible inside the subclass
- They are **not** accessible inside the non-subclass (main method)
- They are **not** accessible inside the subclass of another package

Public :

- They are accessible everywhere.

Default : (They are not accessible outside its package)

- They are accessible inside that class
- They are accessible inside the subclass
- They are accessible inside the non-subclass (main method)
- They are **not** accessible inside the subclass of **another package**
- They are **not** accessible inside the non-subclass of **another package**

Protected : (They are not accessible only in non-subclass of another package)

- They are accessible inside that class
- They are accessible inside the subclass
- They are accessible inside the non-subclass (main method)
- They are accessible inside the subclass of another package
- They are **not** accessible inside the **non-subclass** of **another package**

---

A Class can have three type of members : variables, methods and inner classes.

```Java
class Outer
{
    int x;

    void show()
    {
        // Implementation
    }

    class Inner
    {
        // Implementation
    }
}
```

All access modifiers can be used on the members of class.

Outer class can only be `defualt` and `public`, It cannot be private or protected.

---

Class Can be used in two ways:

Either by creating its object, or by Inheriting it.

```Java
class Test
{
    // Implementation
}
```

```Java
// HAS-A relationship
// This class HAS-A object of Test
class Demo1
{
    Test t = new Test();
}
```

```Java
// IS-A relationship
// This class IS-A Test class
class Demo2 extends Test
{
    // Implementation
}
```
