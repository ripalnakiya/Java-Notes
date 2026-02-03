# Functions

```Java
public class FunctionPower {

    public static int power(int num, int pow) {
        int result = 1;
        for(int i = 0; i < pow ; i++) {
            result = result * num;
        }
        return result;
    }

    public static void main(String[] args) {
        System.out.println(power(2,3));
    }
}
```

In Java, we can only pass the arguments **by value**, always.

That is, we can't use **pass by reference** and **pass by address**.

Content of Actual Parameters is **Copied** to Formal Parameters.

## Passing Objects as Parameters

When an object is passed to a method in Java, a copy of the reference is passed.

Both the original reference and the parameter refer to the same object, 
so changes to the object are visible.

Reassigning the parameter does not affect the original reference.

```Java
Student s1 = new Student();
function(s1);
```

The **value of the reference** is copied.

Not the object.

```Java
void function(Student s) {
    s.rollNo = 42;
}
```

This does change the object sent from `main()`.

**Why?** We modified the object, Not the reference.

Now watch this:

```Java
void function(Student s) {
    s = new Student(); // reassign
}
```

This does nothing to `main()`.

**Why?** Only the copied reference `s` changed, the original reference stays untouched.

> If this were true pass-by-reference, that reassignment would be visible. It isn’t.

## Variable Number of Arguments

we use `...` for defining variable number of arguments.

```Java
static void show(int ...A) {
    for(int x : A) {
        System.out.println(x);
    }
}
```

In the argument list, `A` functions similar to an array.

```Java
static void show(int ...A) {
    for(int i=0; i<A.length; i++) {
        System.out.print(A[i] + " ");
    }
}

public static void main(String[] args) {
    show(1,2,3,4,5);                    // 1 2 3 4 5
}
```

```Java
static void showList(int a, String ...S) {
    System.out.println(a);
    for(int i = 0; i < S.length; i++) {
        System.out.println(S[i]);
    }
}

public static void main(String[] args) {
    showList(12, "Jack", "Harry", "Viking", "Thomas");
}
```

## Command Line Arguments

When writing `main()`, we have a parameter `String[] args`.

This parameter is used for command line arguments.

For example, let us write a java program to print all the names passed as command line arguments.

```Java
public class CommandLineArgs {
    public static void main(String[] args) {
        for(String s : args) {
            System.out.println(s);
        }

        // This is also valid
        for(int i = 0; i < args.length; i++) {
            System.out.println(args[i]);
        }
    }
}
```

Now, to pass the command line arguments:

```shell
> javac CommandLineArgs.java

> java CommandLineArgs Harry Jack Thomas
Harry
Jack
Thomas
```
