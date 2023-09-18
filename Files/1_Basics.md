# Basics

### Check If Java is already installed

```sh
java --version
javac --version
```

_java_ is runtime.
_javac_ is compiler.

## Java Program

The _program file_ name and _class_ name should be **same**.

For example, the following program is written in `JavaBasics.java` files

```java
public class JavaBasics
{
    public static void main(String[] args)
    {
        System.out.print("Hello World!");       // Prints in the same Line
        System.out.println("Hello World!");     // Prints and then Moves printing pointer to the Next Line
        System.out.print("Hello World!\n");     // It also Prints and then Moves the printing pointer to the Next Line
    }
}
```

## Running Java program

Firstly, we need to compile the Java program.

```sh
javac <file-name>.java
```

Then, we'll run the Java program.

```sh
java <file-name>.java
```

## Data Types

Primitive Types:

```java
boolean var = true;         // 1 bit

char ch = 'a';              // 2 bytes

byte b = 100;               // 1 byte
short num = 25;             // 2 bytes
int num = 25;               // 4 bytes
long num = 25;              // 8 bytes

float fl = 10.5f;            // 4 bytes
double dl = 12.5;           // 8 bytes
```

Non Primitive Types:

String
Array
Class
Object
Interface

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

## Summery

Sum of two number

```java
import java.util.Scanner;

public class SumTwo
{
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);

        int a = sc.nextInt();
        int b = sc.nextInt();
        int sum = a + b;

        System.out.println("Sum is " + sum);

        sc.close();
    }
}

```

## Identifer Rules

Names can contain letters, digits, underscores, and dollar signs

Names must begin with a letter

Names should start with a lowercase letter and it cannot contain whitespace

Names can also begin with $ and \_

Reserved words (like Java keywords, such as int or boolean) cannot be used as names

## Type Conversion

It happens when :

- The two data types are compatible.
- When we assign a value of a smaller data type to a bigger data type.

> Numeric Types are compatible with each other.
>
> Character and Boolean Types are not compatible with each other
> Nor they are compatible with Numeric Types.

> Byte -> Short -> Int -> Long -> FLoat -> Double

It is also called widening conversion or Implicit conversion.

```java
int num = 10;
float price = num;      // valid
```

```java
float price = 10.0f;
int num = price;        // Invalid
```

## Type Casting

If we want to assign a value of a larger data type to a smaller data type we perform explicit type casting or narrowing.

```java
float price = 10.0f;
int num = (int) price;      // Valid
```

The decimal part of the variable `price` is lost (the variable is converted to integer).

## Type Promotion

While evaluating expressions, the intermediate value may exceed the range of operands and hence the expression value will be promoted.

- Java automatically promotes each `byte`, `short`, or `char` operand to `int` when evaluating an expression.

- If one operand is `long`, `float` or `double` the whole expression is promoted to long, float, or double respectively.

```java
byte b = 5;
b = b * 2;      // Invalid
```

This is invalid because `b * 2` is an expression, so its value will be promoted to `int` type, and cannot be assigned to byte type directly.

```java
byte b = 5;
b = (byte)(b * 2);      // Valid
```

## Operators

There are different types of operators :

Arithmetic operators

Relational operators

Logical operators

Bitwise operators

Assignment operators
