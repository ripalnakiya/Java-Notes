# Basics
<show-structure depth="2"/>

## Data Types

Primitive Types:

```Java
boolean var = true;     // JVM Dependent, 1 bit

char ch = 'a';          // 2 bytes

// Integral types
byte b = 100;           // 1 byte
short num = 25;         // 2 bytes
int num = 25;           // 4 bytes
long num = 25;          // 8 bytes

// Floating Point types
float fl = 10.5f;       // 4 bytes
double dl = 12.5;       // 8 bytes
```

- Non-Primitive Types:
  - String
  - Array
  - Class
  - Interface

## Identifier Rules

- Names can contain letters, digits, underscores, and **dollar** signs.
- Names must **begin** with a letter, underscore or **dollar** sign.
- Names should start with a lowercase letter (Camel Case).
- Reserved words (e.g. keywords, such as `int` or `boolean`) cannot be used as names

## Literals

To improve the readability of program, we can use underscores in the literals.

```Java
int num = 12_50_287;
System.out.println(num);                    // 1230287
```

## Operators

- Arithmetic operators
- Relational operators
- Logical operators
- Bitwise operators
- Assignment operators

In Java, we can use `%` operator, even on floating point numbers.

## Code: Sum of two numbers

```Java
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

```
Type Conversion
 ├── Widening Conversion
 │     └── Type Promotion (special case)
 └── Narrowing Conversion (needs casting)
```

### Widening Conversion (Implicit)

Widening conversion takes place when two data types are automatically converted. 

- This happens when:
  - The two data types are compatible.
  - When we assign a value of a smaller data type to a bigger data type.

**For Example,** in java, 
the numeric data types are **compatible with each other** 

but no automatic conversion is supported from numeric type to char or boolean. 

Also, char and boolean are not compatible with each other.

**`Byte` -> `Short` -> `Int` -> `Long` -> `Float` -> `Double`**

```Java
int num = 10;
float price = num;      // valid
```

```Java
float price = 10.0f;
int num = price;        // Invalid
```

- Where it happens:
  - Assignments
  - Expressions
  - Method arguments

#### Type Promotion

While evaluating expressions, 
the intermediate value may exceed the range of operands 
and hence the expression value will be promoted. 

- Some conditions for type promotion are:
  1. Java automatically promotes each `byte`, `short`, or `char` 
     operand to `int` when evaluating an expression.
  2. If one operand is `long`, `float` or `double` 
     the whole expression is promoted to `long`, `float`, or `double` respectively.

**Important detail:**

```Java
byte b = 5;
b = b * 2;      // Invalid
```

This is invalid because `b * 2` is an expression, 
so its value will be promoted to `int` type, 
and cannot be assigned to `byte` type directly.

```Java
byte b = 5;
b = (byte)(b * 2);      // Valid (Type Casting)
```

### Narrowing Conversion (Explicit)

If we want to assign a value of a larger data type 
to a smaller data type we perform explicit **type casting** or **narrowing**.

This is useful for incompatible data types 
where automatic conversion cannot be done.

```Java
float price = 10.0f;
int num = (int) price;      // Valid
```

The decimal part of the variable `price` is lost (the variable is converted to integer).
