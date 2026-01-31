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

In Java, we can only pass the arguments by value.

That is, pass by reference and pass by address is not allowed.

Content of Actual Parameters is **Copied** to Formal Parameters.

## Passing Objects as Parameter

When passing **objects** the objects also the Content of Actual Parameters is **Copied** to Formal Parameters.

But actually the reference of the object in Actual Parameters is copied to Formal Paramters.

So, changes made to the reference in another function are reflected in the main() as well.

```Java
public class FunctionPower {

    public static int change(int Arr[]) {
        Arr[0] = 20;
    }

    public static void main(String[] args) {
        int A[] = {2, 4, 6, 8, 10};
        change(A);
        System.out.println(A[0]);           => 20
    }
}
``
```

New Array object is not created in the `change()`, but instead Reference to the Array object `A` is copied to Reference `Arr`.

So, `Arr` will also point to the same Array object to which `A` is pointing.

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
    show(1,2,3,4,5);                    => 1 2 3 4 5
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

Now, To pass the command line arguments:

```SH
> javac CommandLineArgs.java
```

```SH
> java CommandLineArgs Harry Jack Thomas
Harry
Jack
Thomas
```
