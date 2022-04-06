# Basics

## Data Types

Primitive Types:

```java
boolean var = true;         // 1 bit

char ch = 'a';              // 2 bytes

// Integral types
byte b = 100;               // 1 byte
short num = 25;             // 2 bytes
int num = 25;               // 4 bytes
long num = 25;              // 8 bytes

// Floating Point types
float fl = 10.5f;            // 4 bytes
double dl = 12.5;           // 8 bytes
```

Non Primitive Types:

String
Array
Class
Object
Interface

## Identifer Rules

Names can contain letters, digits, underscores, and dollar signs.

Names must begin with a letter, underscore or dollar sign.

Names should start with a lowercase letter (Camel Case).

Reserved words (like Java keywords, such as int or boolean) cannot be used as names

## Literals

To improve the readability of program, we can use underscores in the literals.

```java
int num = 12_50_287;
System.out.println(num);                    => 1230287
```

## Operators

In Java, we can use % operator, even on floating point numbers.

## Summery

Sum of two number

```java
import java.util.Scanner;

public class Main
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
