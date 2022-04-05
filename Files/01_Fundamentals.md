# Fundamentals

### Check If Java is already installed

```sh
java --version
javac --version
```

_java_ is runtime.
_javac_ is compiler.

## Hybrid Language

Java file is firstly compiled using `javac` compiler.

And `.class` file is generated.

Then It is Executed using the Interpreter inside JVM.

and No new file is generated, since Interpreter is used.

## Platform Independent

- Java Language is platform independent, because all the system calls are handled by JVM.

  - So, after compiling the Java program, we can port the compiled(.class) file to other OS, and JVM for that particular OS will execute the `.class` file.

- But in languages like C++, system calls are directly inside the compiled(.exe) file.

  - So, we cannot port the compiled file to other OS.

## Running Java program

Firstly, we need to compile the Java program.

```sh
javac First.java
```

A `.class` file is generated after this. (First.class)

Then, we'll run the Java program.

```sh
java First
```

## Java File Name

It is not compulsory to have file name same as class name.

It is compulsory only when the class is declared public.

---

Consider this program file name is `First.java`:

```java
class First
{
    public static void main(String[] args)
    {
        System.out.println("Hello World!");
    }
}
```

Now run this program,

```sh
javac First.java

java First
```

---

Consider this program file name is `First.java`:

```java
class Second
{
    public static void main(String[] args)
    {
        System.out.println("Hello World!");
    }
}
```

Now run this program,

```sh
javac First.java

java Second
```

> Here, we need to take care when we are executing java byte code.
>
> This happens because the `.class` file name is same as the class name. (Second.class)

---

Now, Consider this program file name is `First.java`:

```java
public class Second
{
    public static void main(String[] args)
    {
        System.out.println("Hello World!");
    }
}
```

Now run this program,

```sh
javac First.java
```

> This will generate error, since class Second is declared public.
>
> So to solve the problem, we compulsory has to have same class name as file name.

## main() in Java

If the main() doesn't contain `String[] args` as parameter, still the program will be compiled successfully.

But There will be an error when executing the program.

## Java Program

```java
public class Main
{
    public static void main(String[] args)
    {
        System.out.print("Hello World!");       // Prints in the same Line
        System.out.println("Hello World!");     // Prints and then Moves printing pointer to the Next Line
        System.out.print("Hello World!\n");     // It also Prints and then Moves the printing pointer to the Next Line
    }
}
```

## Formatted Output

Format Specifier:

```java
% [argumentIndex $] [flags] [width] [.precesion] conversion
```

- argumentIndex: 1$ 2$ 3$ ...

- flags: **0** , **(**, **+**, **-**

- conversion:
  - char -> c
  - int -> d, o, x
  - float -> f, e, g
  - string -> s

```java
int x = 5;
float y = 10.2;
String z = "Jack";

System.out.printf("%d %f %s", x, y, z);         => 5 10.2 Jack
```

```java
int x = 5;
float y = 10.2;
String z = "Jack";

// Using the Argument Indexes
System.out.printf("%3$s %2$f %1$d", x, y, z);       => Jack 10.2 5
```

```java
int a = 12;

// Using the Width
System.out.printf("%5d", a);                => "   12"
```

The value of a will be printed and will occupy 5 places in the output.

```java
int a = 123456;

// Using the Width
System.out.printf("%5d", a);                => "123456"
```

When value of width is less than the value of digits in number, then the width will have no effect on the output.

---

```java
int a = 12;

// Using the Width and Flag 0
System.out.printf("%05d", a);                => "00012"
```

The **Flag 0** will fill empty space with 0.

```java
int a = -12;

// Using the Width and Flag (
System.out.printf("%(5d", a);                => " (12)"
```

The **Flag (** will wrap the negative numbers in brackets.
It will not have any effect on positive numbers.

```java
int a = 12;

// Using the Width and Flag +
System.out.printf("%+5d", a);                => "  +12"
```

```java
int a = -12;

// Using the Width and Flag +
System.out.printf("%+5d", a);                => "  -12"
```

The **Flag +** forces to preceed the result with a plus or minus sign (+ or -) even for positive numbers. By default, only negative numbers are preceded with a - sign.

```java
String str = "Jack";

// Using the Width and Flag -
System.out.printf("%11s",str);                  => "       Jack"
```

```java
String str = "Jack";

// Using the Width and Flag -
System.out.printf("%-11s",str);                  => "Jack       "
```

The **Flag -** will left-justify within the given field width. Right justification is the default

---

```java
int float = 12.432;

// Using the Width
System.out.printf("%7d", a);                    => " 12.432"

// Using the Width and precision
System.out.printf("%7.2d", a);                  => "  12.43"

// Using the Width and precision
System.out.printf("%5.2d", a);                  => "12.43"

// Using the Width, Flag and precision
System.out.printf("%07.2d", a);                 => "012.43"
```

```java
int float = 12345678.543;

// Using the Width and precision
System.out.printf("%6.2d", a);                => "12345678.00"
```

```java
int float = 12.654321;

// Using only Width
System.out.printf("%5d", a);                => "12.654321"
```

When the number is larger than specified width, It won't give desired results.

## Input in Java

To Take input we need a object of Scanner class.

And to use Scanner class, we need to import it.

```java
import java.util.Scanner;
```

Class have many methods, for inputing different data types.

```java
Scanner sc = new Scanner(System.in);
String fName = sc.next();               // Word (Words after a space are not included)
System.out.println("Hello " + fName) ;
sc.close();
```

```java
String name = sc.nextLine();            // Multiples Words
System.out.println("Hello " + name);
```

`nextBoolean()` Reads a boolean value from the user

`nextByte()` Reads a byte value from the user

`nextShort()` Reads a short value from the user

`nextInt()` Reads a int value from the user

`nextLong()` Reads a long value from the user

`nextDouble()` Reads a double value from the user

`nextFloat()` Reads a float value from the user

`nextLine()` Reads a String value from the user
