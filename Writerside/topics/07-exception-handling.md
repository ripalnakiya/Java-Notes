# Exception Handling

Exceptions are Runtime Errors.

There are many types of errors:

1. **Syntax Error** - can be removed with the help of compiler.

2. **Logical Error** - can be removed with the help of debugger.

3. **Runtime Error** - can be resolved with the help of Exception Handling.

Causes of runtime errors are bad input or unavailability of resources.

Exception handling is process of responding to the runtime errors.

**Syntax** and **Logical** errors are faced by Programmers, and **Runtime**
errors are faced by User.

```Java
public class Main {
    public static void main(String[] args) {
        int a = 10;
        int b = 0;
        try {
            int c = a / b;
            System.out.println(c);
        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero");
        }
        System.out.println("Program ends");
    }
}
```

## Built-in Exception Classes

`Object` is the parent class for all the java classes.

`Exception` is the parent class for all the exceptions.

```Java
Exception
   ClassNotFoundException
   IOException
   InterruptedException
   NumberFormatException
   RuntimeException
      ArithmeticException
      ArrayIndexOutOfBoundsException
      NullPointerException
```

**Exception Class Methods:**

```Java
String getMessage();          // System.out.println(e.getMessage());
String toString();            // System.out.println(e);
// These methods returns a string with a message written about exception, 
// purpose of both the methods is same
// but the usage of both the methods are different.

void printStackTrace();       // System.out.println(e.printStackTrace());
// This prints the stack trace of the exception (Sequence of Method calls).
```

Exception classes are categorized into two types:

1. **Checked exceptions** must be handled by `try` and `catch`, java compiler
   forces you to write `try` and `catch`.

2. **Unchecked exceptions** are not mandatory to be handled.
   - Only Runtime Exceptions are the unchecked exceptions.

## Custom Exception Classes

```Java
class NegativeDimensionException extends Exception {
    public String toString() {
        return "Dimensions cannot be negative";
    }
}

public int area(int a, int b) throws NegativeDimensionException {
    if (a < 0 || b < 0) {
        throw new NegativeDimensionException();
    }
    return a * b;
}
```

## Propagation of Exception

```Java
public class Main {
    static int method1() {
        return 10 / 0;
    }

    static void method2() {
        method1();
    }

    static void method3() {
        method2();
    }

    public static void main(String[] args) {
        try {
            method3();
        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero");
        }
    }
}
```

Output:

```shell
Cannot divide by zero
```

Even though, the exception occurred in `method1()`, 
It was passed on to its calling methods, 
and finally was handled in `main()`.

## Throw

`throw` keyword is used to throw an exception logically.

Only one exception can be thrown at a time by using `throw` keyword.

We can catch the exception in the same function using `try` and `catch` block.

```Java
public class Main {
    public static void main(String[] args) {
        int a = 10, b = 0;
        try {
            if (b == 0)
                throw new ArithmeticException();
            int c = a / b;
            System.out.println(c);
        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero");
        }
    }
}
```

## Throws

`throws` keyword is used to pass the exception to the calling function.

`throws` is used for declaring that a method may throw exception.

```Java
class NegativeDimensionException extends Exception {
    public String toString() {
        return "Dimensions cannot be negative";
    }
}

public class Main {
    static int area(int a, int b) throws NegativeDimensionException {
        if (a < 0 || b < 0) {
            throw new NegativeDimensionException();
        }
        return a * b;
    }

    static void method1() throws NegativeDimensionException {
        System.out.println("Area is " + area(-5, 10));
    }

    public static void main(String[] args) {
        try {
            method1();
        } catch (NegativeDimensionException e) {
            System.out.println(e);
        }
    }
}
```

Firstly we generated exception in `area()`, 
But we don't want to handle it inside that function...

So we pass it on to the calling function using `throws` keyword in the function name.

## finally Block

`finally` keyword is used in association with a try/catch block.

`finally` keyword is meant to execute whether an exception occurs or not.

Usually `finally` block is used to release the resources.

> It is useful when we're not handling all the exceptions in the program.

```Java

public class Main {
    public static void main(String[] args) {
        try
        {
            throw new Exception();
        }
        finally
        {
            System.out.println("Finally block");
        }
    }
}
```

Output:

```shell
Finally block
```

Here, we haven't handled the particular exception, but still the `finally` block was executed.

## Try with resources

**Garbage Collector** only releases the **heap memory** (Heap memory is resource).

**Programmer** is responsible for releasing the **other resources** (Network, Database, Files).

```Java
int method1() throws Exception {
    FileReader f;

    try {
        f = new FileReader("abc.txt");
        // Use File
    } finally {
        f.close();
    }

    return result;
}
```

This is a proper code, to handle resources.

But, we has to use `finally` block everytime, to close the acquired resources.

To avoid `finally` block, we can use **`try` with resources**.

**`try` with resources**, automatically closes the resources.

```Java
int method1() throws Exception {
    try (FileReader f = new FileReader("abc.txt")) {
        // Use File
        return result;
    }
}
```

`try` block wil automatically release the acquired resources after it finishes its execution.
