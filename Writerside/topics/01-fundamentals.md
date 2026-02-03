# Fundamentals

## Hybrid Language

Java file is firstly compiled using `javac` compiler.

And `.class` file is generated.

Then It is executed using interpreter inside JVM, 
so, no new file is generated at this stage, since Interpreter is used.

## Platform Independent

**Java** language is platform independent, 
because all the system calls are handled by JVM.

So, after compiling the Java program, 
we can port the compiled(`.class`) file to other OS, 
and JVM for that particular OS can execute the `.class` file.

But in languages like **C++**, 
system calls are directly inside the compiled(`.exe`) file.

So, we cannot port the compiled file to other OS.

## Running a Java program

Firstly, we need to compile the Java program.

```shell
javac First.java
```

A `.class` file is generated after this. (`First.class`)

Then, we'll run the Java program.

```shell
java First
```

## Java File Name

It is NOT compulsory to have file name same as class name.

It is compulsory only when the class is declared public.

### Case 1

```Java
// "First.java"

class First {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

We can run the program,

```shell
javac First.java
java First
```

### Case 2

```Java
// "First.java"

class Second {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

We can run the program,

```shell
javac First.java
java Second
```

Here, we need to take care when we are executing java byte code.

This happens because generated `.class` file name 
will have the same as the class name. (`Second.class`)

### Case 3

```Java
"First.java"

public class Third {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

Try running this program:

```shell
javac First.java
```

This will generate error, since class `Second` is declared `public`.

So to solve the problem, we compulsory has to have same class name as file name.

## `main()` in Java

If the `main()` doesn't contain `String[] args` as parameter, 
still the program will be compiled successfully.

But there will be an error when executing the program.

## Output in Java

```Java
public class Main {
    public static void main(String[] args) {
        System.out.print("Hello World!");       // Prints in the same Line
        System.out.println("Hello World!");     // Prints and then Moves printing pointer to the Next Line
        System.out.print("Hello World!\n");     // It also Prints and then Moves the printing pointer to the Next Line
    }
}
```

## Input in Java

To take input we need a object of `Scanner` class.

```Java
import java.util.Scanner;
```

Class has many methods, for input of different data types.

```Java
Scanner sc = new Scanner(System.in);
String fName = sc.next();   // Word (until a space is encountered)
System.out.println("Hello " + fName) ;
sc.close();
```

```Java
String name = sc.nextLine();  // Multiples Words
System.out.println("Hello " + name);
```

`nextBoolean()` Reads a boolean value from the user

`nextInt()` Reads a int value from the user

`nextLong()` Reads a long value from the user

`nextFloat()` Reads a float value from the user

`nextDouble()` Reads a double value from the user
