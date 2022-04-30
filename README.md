# Table Of Contents

[Fundamentals](#fundamentals)

[Basics](#basics)

[Strings](#strings)

[Arrays](#arrays)

[Functions](#functions)

[Object Oriented Programming](#object-oriented-programming)

[Inheritance](#inheritance)

[Abstract Classes](#abstract-classes)

[Interfaces](#interfaces)

[Static and Final keywords](#static-and-final-keywords)

[Access Modifiers](#access-modifiers)

[Exception Handling](#exception-handling)

[Multithreading](#multithreading)

[Annotations](#annotations)

[Lambda Expressions](#lambda-expressions)

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

# Strings

String is collection of characters.

String syntax:

```java
String str = "Hello";
// or
String str = new String("Hello");
```

Strings are Immutable.

String Class Methods:

```java
int length()
String toLowerCase()    // Will return a new string, it will not mutate the original string
String toUpperCase()
String trim()   // Will remove leading and trailing whitespaces
String substring(int begin)
String substring(int begin, int end)
String replace(old char, new char)  // Will replace all the occurrences of old char with new char
String concat(String s) // It will concat the string s with the string

boolean startsWith(String s)    // Will check if the string starts with given substring s
boolean endsWith(String s)
char charAt(int index)
boolean contains(String s) // Will check if the substring s is present in the string or not

int indexOf(String s)   // Will return the index of first occurance given substring s inside the string
int lastIndexOf(String s)

boolean equals(String s)
boolean equalsIgnoreCase(String s)

int CompareTo(String s)     // Lexicographic comparison
```

## String Concatenation

```java
String fName = "Captain";
String lName = "Jack";

String name = fName + " " + lName;
```

When using concatenation operator with strings , we should be careful.

```java
int x = 10, y = 20;
System.out.println(x + y + " is Sum");          => 30 is Sum
```

```java
int x = 10, y = 20;
System.out.println("Sum is " + x + y);          => Sum is 1020
```

> This happened because of precedence
> Firstly, It became ("Sum is " + x) = "Sum is 10"
> Then, It became ("Sum is 10" + y) = "Sum is 1020"

So, we can use bracket to set the precedence.

```java
int x = 10, y = 20;
System.out.println("Sum is " + (x + y));          => Sum is 30
```

## Accessing String Characters

```java
String str = "Captain jack";

System.out.println(str.charAt(1));              => a
```

We can access each character using this method.

## String Comparison

```java
String s1 = "Jack";
String s2 = "Jack";
String s3 = new String("Jack");

System.out.println( s1 == s2 );             => true

System.out.println( s1 == s3 );             => false
System.out.println( s1.equals(s3) );        => true
```

This happened because, when we created string variable `s2` without new keyword,
String `s2` also started pointing to the same string to which `s1` is pointing.

It is also called **Interning**.

But, using `equals()` function, the actual value of the string was compared, instead of its pointer.

## String Lexicographic Comparison

```java
str1.compareTo(str2);
```

If value is 0, means strings are equal.
If value is less than 0, means str1 is less than str2
If value is greater than 0, means str1 is greater than str2

For example,

- `Java` is greater than `Cpp`, because (74 > 67) i.e. (J > C)
- `ABC` is smaller than `abc`, because (65 < 97) i.e. (A < a)

## String Builder

When we modify existing string, a new string is created inside the memory.

For example,

```java
String str = new String("Hello");

str = str + 'A';
```

Now, a new string is created "HelloA", and str will point to the new string.

This is because, Strings are immutable in java.

**String Builder** is a mutable

```java
StringBuilder sb = new StringBuilder("Hello");
```

`toString()` functions converts a object into string.

For example,

```java
int a = 10;
a.toString();               // Incorrect, since a is not object

char ch = 'a';
ch.toString();              // Incorrect, since ch is not object
```

```java
Integer a = 10;
a.toString();               // Correct

Character ch = 'a';
ch.toString();              // Correct
```

### Adding Characters

We can add characters in the `StringBuilder` object, by using `append()` method.

It appends character to the end of the string.

```java
StringBuilder sb = new StringBuilder("");
sb.append("Hello");
System.out.println(sb);
```

# Arrays

Array Declaration Syntax:

```java
dataType arrayName[] = new dataType[size];
```

For example,

```java
int marks[] = new marks[10];

int []marks = new int[10];

// Here, int[] becomes a data type
int[] marks = new int[10];

// So, we can create multiple arrays
int[] marks, values;
marks = new int[10];
values = new int[10];


int marks[] = {10, 20 ,30};

String fruits[] = {"Banana", "Mango", "Apple"};
```

## Array Length

```java
System.out.println(marks.length);           => 50
```

## For each loop

We can also use **For each** loop to access the elements of the array

```java
int A[] = {2, 4, 6, 8, 10};

for(int x : A) {
    System.out.println(x);
}
```

It will access each element of the array.

For each loop will only access the array elements, it will not modify the acutal array.

## 2D Array

```java
int A[][] = new int[3][4];

int [][]A = new int[3][4];

int []A[] = new int[3][4];

// Here, int[] becomes a data type
int[] A[] = new int[3][4];

int[] B[], C[];
B = new int[3][4];
C = new int[3][4];

// Here, int[][] becomes a data type
int[][] A = new int[3][4];

int[][] B, C;
B = new int[3][4];
C = new int[3][4];

int A[][] = {{1,2,3,4}, {2,4,6,8}, {3,6,9,12}};

```

---

Consider this tricky array declaration:

```java
int[] A, B[];

A = new int[10];
B = new int[3][4];
```

Here, A is 1D array and B is 2D array.

### Accessing Array Elements

```java
for(int x[] : A) {
    for(int y : x) {
        System.out.print(y);
    }
    System.out.print("\n");
}
```

# Functions

```java
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

```java
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

```java
static void show(int ...A) {
    for(int x : A) {
        System.out.println(x);
    }
}
```

In the argument list, `A` functions similar to an array.

```java
static void show(int ...A) {
    for(int i=0; i<A.length; i++) {
        System.out.print(A[i] + " ");
    }
}

public static void main(String[] args) {
    show(1,2,3,4,5);                    => 1 2 3 4 5
}
```

```java
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

```java
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

```sh
> javac CommandLineArgs.java
```

```sh
> java CommandLineArgs Harry Jack Thomas
Harry
Jack
Thomas
```

# Object Oriented Programming

Consider this file name `MyRectangle.java` :

```java
class Rectangle {
    private int length;
    private int breadth;

    public Rectangle() {
        length = 1;
        breadth = 1;
    }

    public Rectangle(int l, int b) {
        length = l;
        breadth = b;
    }

    public int area() {
        return length * breadth;
    }
}

public class MyRectangle {
    public static void main(String[] args) {
        Rectangle r1 = new Rectangle(5,10);
        System.out.println(r1.area());          => 50
    }
}
```

## Printing Object of a Class

```java
class Test {

}

class Main {
    public static void main(String[] args) {
        Test obj = new Test();
        System.out.println(obj);                        => Test@512ddf17
    }
}
```

This is because while printing the object, the toString() method of the object class is called. It formats the object in the default format.

If we want to format the output in our own way, we need to override the toString() method inside the class.

```java
class Test {
    public String toString() {
        return "object";
    }
}

class Main {
    public static void main(String[] args) {
        Test obj = new Test();
        System.out.println(obj);                        => object
    }
}
```

## Array of Objects

```java
class Subject {
    private String name;
    private int maxMarks;

    public Subject(String name, int maxMarks) {
        this.name = name;
        this.maxMarks = maxMarks;
    }

    public String toString() {
        return "\nName: "+ name + "\nMax Marks: "+ maxMarks;
    }
}

public class ArrayOfObjects {
    public static void main(String[] args) {
        // This only creates 3 references for the objects, It doesn't create the objects
        Subject subs[] = new Subject[3];

        // We need to create objects explicitly, from the heap.
        subs[0] = new Subject("Cpp", 100);
        subs[1] = new Subject("Java", 100);
        subs[2] = new Subject(".NET", 50);

        for(Subject sub : subs) {
            System.out.println(sub);
        }
    }
}
```

## Class with Other Class Object as Member

```java
class Subject {
    private String name;
    private int maxMarks;

    public Subject(String name, int maxMarks) {
        this.name = name;
        this.maxMarks = maxMarks;
    }

    public String toString() {
        return "\nName: " + name + "\tMax Marks: " + maxMarks;
    }
}

class Student {
    private int rollNo;
    private String name;
    private String Department;
    private Subject subjects[];

    public Student(int rollNo, String name, String Department, String... subs) {
        this.rollNo = rollNo;
        this.name = name;
        this.Department = Department;
        this.subjects = new Subject[subs.length];
        int i = 0;
        for (String s : subs) {
            subjects[i++] = new Subject(s, 100);
        }
    }

    public String toString() {

        // adding the Subject object to the string
        StringBuilder sb = new StringBuilder("");
        for (Subject s : subjects) {
            sb.append(s.toString());
        }

        // returning the Student object, along with the value of Array of Subject objects
        return "\nRoll no: " + rollNo + "\nName: " + name + "\nDepartment: " + Department + "\nSubjects: " + sb;
    }
}

public class Main {
    public static void main(String[] args) {

        // Creating Array of Student Objects
        Student studs[] = new Student[args.length];

        // Initializing all the references of Student object
        int i = 0;
        for (String str : args) {
            studs[i++] = new Student(i, str, "CSE", "CPP", "Java", "Python");
        }

        // Displaying data of all Student objects
        for (Student s : studs) {
            System.out.println(s);
        }
    }
}
```

# Inheritance

```java
class Circle {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    public double circumference() {return 2 * Math.PI * radius;}
    public double area() {return Math.PI*radius * radius;}
}

class Cylinder extends Circle {
    private double height;
    public volume(){return area() * height;}
}
```

All the members of Circle class will be **available** in the Cylinder class.

Object of Circle class will have size of 8 bytes.

Object of Cylinder class will have size of 16 bytes.

## Constructors in Inheritance

Parameterised constructor of base class must be explicitly called from derived class constructor.

```java
class Base {
    public Base(){System.out.println("Non Param of Base ");}
    public Base(int x){System.out.println("Param of Base " + x);}
}

class Derived extends Base {
    public Derived(){System.out.println("Non Param of Derived ");}
    public Derived(int y){System.out.println("Param of Derived " + y);}

    public Derived(int x, int y){
        super(x);
        System.out.println("2 Param of Derived " + y);
    }
}
```

`super` keyword is used to refer to the parent class of a subclass.

It is a reference to the parent class.

Here, `super()` is used to call a superclass parameterised constructor.

It can also be used to access data members of super class from derived class.

```java
class Base {
    int x = 10;
}

class Derived extends Base {
    int x = 20;

    void printValues() {
        System.out.println(super.x);            => 10
        System.out.println(x);                  => 20
    }
}
```

## Method Overriding

When we redefine a Base class Method inside Derived class, it is called method overriding.

- Final and static methods cannot be overridden.
- Method can be overridden with same or lenient (public, protected) access
  speciPiers but the stricter(private) access speciPiers cannot be used in sub
  class.

Method Overriding, shadows the Base class method.

```java
class Base {
    public void display() {
        System.out.println("Base Class Display");
    }
}

class Derived extends Base {
    public void display() {
        System.out.println("Derived Class Display");
    }
}

class Main {
    public static void main(String[] args) {
        Base b = new Base();
        b.display();                    => Base Class Display

        Derived d = new Derived();
        d.display();                    => Derived Class Display
    }
}
```

---

Invalid Ways of Overriding Methods :

```java
class Base {
    public void Display() {
        System.out.println("Base Class Display");
    }
}

class Derived extends Base {
    public void Display(int x) {
        System.out.println("Derived Class Display");
    }
}
```

Here, `Display()` is not **overrided**, But they are **overloaded**.

```java
class Base {
    public void Display() {
        System.out.println("Base Class Display");
    }
}

class Derived extends Base {
    public int Display(int x) {
        System.out.println("Derived Class Display");
    }
}
```

This will generate error, since the return types are different.

## Dynamic Method Dispatch

```java
class Base {
    public void display() {
        System.out.println("Base Class Display");
    }
}

class Derived extends Base {
    public void display() {
        System.out.println("Derived Class Display");
    }
}

class Main {
    public static void main(String[] args) {
        Base b = new Derive();
        b.display();                            => Derived Class Display
    }
}
```

We're having reference of Base class, and have assigned Derived class object.

It will work almost the same way as if we have assigned Base class object.

**But** when We're calling Base class method, and already have overrided that Base class method in the Derived class.

The derived class method will be called.

---

```java
class Base {
    public void meth1()
    {
        System.out.println("Base Method 1 Display");
    }
    public void meth2()
    {
    S   ystem.out.println("Base Method 2 Display");
    }
}

class Derived extends Base {
    public void meth2()
    {
        System.out.println("Derived Method 2 Display");
    }
    public void meth3()
    {
        System.out.println("Derived Method 3 Display");
    }
}

class Main {
    public static void main(String[] args) {
        // Case 1
        Base b = new Base();
        b.meth1();                          => Base Method 1 Display
        b.meth2();                          => Base Method 2 Display

        // Case 2
        Derived d = new Derived();
        d.meth1();                          => Base Method 1 Display
        d.meth2();                          => Derived Method 2 Display
        // meth2() of Base is overrided, so meth2() of Derived is called
        d.meth3();                          => Derived Method 3 Display

        // Case 3
        Base b = new Derived();
        b.meth1();                          => Base Method 1 Display
        b.meth2();                          => Derived Method 2 Display
        b.meth3();                          // Invalid
    }
}
```

In case 3,

Since, we have Base class reference, we can only call Base class methods.

Therefore, `meth3()` cannot be called.

We can call `meth2()`, since we have this function defined in Base class.

But since, `meth2()` is **overridden** in Derived class, So Derived class `meth2()` is called.

# Abstract Classes

There are two types of classes Abstract class and Concrete class.

If `abstract` keyword is used before the class then it is an Abstract
Class

If nothing is written before class then it is a Concrete class.

Object of an Abstract class cannot be created but object of Concrete
class can be created.

Reference of abstract class is allowed.

```java
abstract class Base
{
    Base()
    {
        System.out.println("Base Constructor");
    }

    void method1()
    {
        System.out.println("Method 1 called");
    }

    abstract void method2();
}

class Derived extends Base
{
    void method2()
    {
        System.out.println("Method 2 called");
    }
}

public class Main{
    public static void main(String[] args) {
        Base b;                         // Reference of abstract class is allowed
        Derived d = new Derived();
    }
}
```

Method which is not having a body is known as **Abstract** method, and the method must be declared as `abstract`.

The abstract method is undefined method.

A class is Abstract class if at least one of the methods is abstract, and we has to declare that class as `abstract`.

Already declared `abstract` class is allowed to not to contain any abstract method.

If any other class inherits abstract class then that class also becomes abstract class, but to make the subclass as concrete class it must override all the undefined(abstract) methods.

- Abstract classes are used for imposing standards and sharing methods

- Sub classes are meant for following those standards

Abstract Class and method both, can neither be final nor static.

Abstract Classes are used for implementing **Inheritance** as well as **Polymorphism**.

Inheritance -> Concrete Methods

Polymorphism -> Abstract Methods

# Interfaces

Interfaces are used for implementing **Polymorphism**.

Inheritances are used for borrowing methods.

Consider this abstract class:

```java
abstract class Base {
    abstract public void method1();
    abstract public void method2();
}

class Derived extends Base
{
    public void method1()
    {
        // Implementation
    }

    public void method2()
    {
        // Implementation
    }
}
```

When an `abstract` class has all methods defined as `abstract`, then it is used purely for implementing **Polymorphism**.

Derived class, has to implement all the `abstract` methods to become concrete class.

Interface can be call as Abstract Class with all abstract methods

Above class can be written using Interfaces in the same way:

```java
interface Base {
    void method1();
    void method2();
}

class Derived implements Base
{
    public void method1()
    {
        //
    }

    public void method2()
    {
        //
    }
}
```

Classes are extended, Interfaces are implemented.

A class can be extended from only one class, and can implement multiple interfaces.

In abstract class, we can create abstract class reference and assign the derived class object.

In Interfaces also, we can create reference of interface and assign the object of class, which implemented the interface.

## Interface Examples

We can also define our own extra methods in derived class.

```java
class Phone {
    public void call(){System.out.println("Phone call");}
    public void SMS(){System.out.println("Phone SMS");}
}

interface Icamera {
    void click();
    void record();
}

interface IMusicPlayer {
    void play();
    void pause();
}

class Smartphone extends Phone implements ICamera, IMusicPlayer {
    public void click(){System.out.println("Camera Click");}
    public void record(){System.out.println("Camera Record");}

    public void play(){System.out.println("Music Play");}
    public void pause(){System.out.println("Music Pause");}

    public void videoCall(){System.out.println("Smartphone Video Call");}
}

public class Main {
    public static void main(String[] args) {
        Smartphone s = new Smartphone();
        s.call();
        s.SMS();
        s.click();
        s.record();
        s.play();
        s.pause();
        s.videoCall();

        Phone p = new Smartphone();
        p.call();
        p.SMS();

        ICamera c = new Smartphone();
        c.click();
        c.record();

        IMusicPlayer m = new IMusicPlayer();
        m.play();
        m.pause();
    }
}
```

## Callbacks using Interface

Interfaces are used for defining callback methods.

```java
interface Member {
    public void callback();
}

class Store {
    // Creating array of references of Member
    Member members = new Member[100];
    int counter = 0;

    void register(Member m){
        members[counter++] = m;
    }

    void inviteSale(){
        for(int i = 0; i < counter ; i++)
            members[i].inviteSale();
    }
}

class Customer implements Member {
    String name;

    Customer(String name){
        this.name = name;
    }

    void inviteSale(){
        System.out.println("I'll Visit, " + name);
    }
}

public class Main {
    public static void main(String[] args) {
        Store s = new Store();
        Customer c1 = new Customer("Jack");
        Customer c2 = new Customer("John");

        s.register(c1);
        s.register(c2);

        s.inviteSale();                 => I'll visit, Jack
                                           I'll visit, John
    }
}
```

## Interface Rules

Methods are `public` and `abstract` by default in Interfaces.

    We cannot make abstract classes in Interfaces as `private`.

---

We can have Identifiers in the interface, and they are `final` and `static`, but the identiAiers must be given name in Upper case.

Methods inside an interface cannot have body, but a method can
have body if the method is `static`.

    And we can access the static members using Interface name and dot operator.

---

We can also have `default` methods inside the interface(they have their body defined inside interface).

We can override the `default` method, but if we don't override then also they are **accessible**.

    `default` methods are useful when, we already have implemented the interface in many classes.

    If we want to add one more method in Interface, then all the implementing classes will have to implement that new method as well(otherwise they will become `abstract` classes).

    So, instead we can define that method inside the interface using `default` keyword, and then we don't need to implement it in all those classses.

---

We can also define `private` methods in the interface (`private` methods that are **not** `abstract`).

    private methods are useful inside the default method, they are not useful outside the interface.

---

Interface can extend from another Interface.

## Cpp vs Java

In C++, one class can inherit from multiple classes(Multiple Inheritance).

But in Java, one class can inherit from only one class.

Multiple Inheritance in java is achieved using Interfaces.

# Static and Final keywords

## Static

    Static Variables, Static Methods, Static Inner Classes, Static Blocks

Static keywords is useful for representing information or data about the class.

Static Keyword is used for representing Meta Data (data about data).

It is useful for representing the information of a class.

Static members belongs to a class and they can be shared by all the objects of the class and all the objects have their own non-static members.

All the object can use the static variable as a shared data.

Static members can be accessed just by using class name.

The static members of a class are created in the method area.

Static methods can access only static members.

## Static Block

Set of statements are written in the form of blocks and are made static.

It is used to initialise static data member.

It is executed before the main method at the time of class loading.

```java
public class Main {
    static
    {
        System.out.println("Block 1");
    }
    public static void main(String[] args)
    {
        System.out.println("Main");
    }
    static
    {
        System.out.println("Block 2");
    }
}
```

Output:

```sh
Block 1
Block 2
Main
```

---

```java
class Test
{
    static
    {
        System.out.println("Block 1");
    }
    static
    {
        System.out.println("Block 2");
    }
}

public class Main {
    public static void main(String[] args) {
        System.out.println("Main");
    }
}
```

Output:

```sh
Main
```

Since, `class` Test is not used, so it won't execute it's static members.

## Final

    Final Variable, Final Method, Final Class

Value of `final` variables are fixed,that is once the value is assigned then it can’t be modified.

`final` variables are written in capital letters.

`final` variable can be initialised **:**

- During the declaration of the variable
- Inside intance block (just a block of curly brackets)
- Inside a static block (`main` method is also `static`), if the variable is also declared `static`
- Inside the constructor of class.
  - As constructors can be overloaded, so the final variable must be initialised in every constructor.

```java
class Test
{
    final int LOW = 0;

    // This is not allowed, it will generate error.
    final int MIN;
    MIN = 1;

    final int AVG;
    {
        AVG = 5;
    }

    static final int MAX;
    static
    {
        // we cannot initialize/use non-static member in static block/method
        MAX = 9;
    }
    // also
    static void fun()
    {
        final int MAX;
        MAX = 9;
    }

    final int HIGH;
    Test()
    {
        HIGH = 10;
    }
    Test(int x)
    {
        HIGH = 10;
    }
}
```

It is not necessary to declare and initialize the final variable in the same statement.

---

`final` method cannot be overridden.

- It is used to restrict Polymorphism.

`final` class cannot be extended.

- It is used to restrict Inheritance.

## Singleton Class

A class which can create only one object is called singleton class.

Constructors are made private and object of the singleton class is created in static method of that class.

In singleton class getInstance() method is used.

```java
class CoffeeMachine {
    private float coffeeQ;
    private float waterQ;

    static private CoffeeMachine machine = null;

    static CoffeeMachine getInstance() {
        // This insures that object is created only once.
        if (machine == null)
            machine = new CoffeeMachine();
        return machine;
    }
}

class Main{
    public static void main(String[] args){
        CoffeeMachine m1 = CoffeeMachine.getInstance();
        CoffeeMachine m2 = CoffeeMachine.getInstance();
        CoffeeMachine m3 = CoffeeMachine.getInstance();

        // All three references point to the same object.

        if(m1 == m2 && m1 == m3)
            System.out.println("Same");
    }
}
```

Output:

```sh
Same
```

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

```java
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

```java
class Test
{
    // Implementation
}
```

```java
// HAS-A relationship
// This class HAS-A object of Test
class Demo1
{
    Test t = new Test();
}
```

```java
// IS-A relationship
// This class IS-A Test class
class Demo2 extends Test
{
    // Implementation
}
```

# Exception Handling

Exceptions are Runtime Errors.

There are many types of errors:

1. Syntax Error - can be removed with the help of compiler.

2. Logical Error - can be removed with the help of debugger.

3. Runtime Error - can be resolved with the help of Exception Handling.

   . Mishandling of a program causes Runtime error.

   . Causes of runtime errors are bad input or unavailability of resources.

   . Exception handling is process of responding to the runtime errors

Syntax and Logical errors are faced by Programmers, and runtime
errors are faced by user

```java
public class Main {
   public static void main(String[] args) {
      int a = 10;
      int b = 0;
      try
      {
         int c = a/b;
         System.out.println(c);
      }
      catch(ArithmeticException e)
      {
         System.out.println("Cannot divide by zero");
      }
      System.out.println("Program ends");
   }
}
```

## Built-in Exception Classes

Object is the mother class for all the java classes.

Exception is the parent class for all the exceptions.

```java
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

```java
// Exception Class Methods
String getMessage();          // System.out.println(e.getMessage());
String toString();            // System.out.println(e);
// These methods returns a string with a message written about exception, purpose of both the methods is same, but the usage of both the methods are different.
void printStackTrace();       // e.printStackTrace();
// This prints the stack trace of the exception (Sequence of Method calls).
```

Exception classes are categorised into two types:

1. Checked exception must be handle by try and catch, java compiler
   forces you to write try and catch.

2. Unchecked exception are not mandatory to be handled, Only Runtime
   Exceptions are the unchecked exceptions.

## Custom Exception Classes

```java
class NegativeDimensionException extends Exception {
   public String toString() {
      return "Dimensions cannot be negative";
   }
}
```

```java
public int area(int a, int b) throws NegativeDimensionException
{
   if(a<0 || b<0) {
      throw new NegativeDimensionException();
   }
   return a*b;
}
```

## Propagation of Exception

```java
public class Main {
   static int method1() {
      return 10/0;
   }
   static void method2() {
      method1();
   }
   static void method3() {
      method2();
   }
   public static void main(String[] args) {
      try
      {
         method3();
      }
      catch(ArithmeticException e)
      {
         System.out.println("Cannot divide by zero");
      }
   }
}
```

Output:

```sh
Cannot divide by zero
```

Even though, the exception occured in `method1()`, It was passed on to its calling methods, and finally was handled in `main()`.

## Throw vs Throws

`throw` keyword is used to throw an exception logically.

Only one exception can be thrown at a time by using `throw` keyword.

We can catch the exception in the same function using `try` and `catch` block.

```java
public class Main {
   public static void main(String[] args) {
      int a = 10, b = 0;
      try
      {
         if(b==0)
            throw new ArithmeticException();
         int c = a/b;
         System.out.println(c);
      }
      catch(ArithmeticException e)
      {
         System.out.println("Cannot divide by zero");
      }
   }
}
```

---

`throws` keyword is used to pass the exception to the calling function.

`throws` is used for declaring that a method may throw exception.

```java
class NegativeDimensionException extends Exception {
   public String toString() {
      return "Dimensions cannot be negative";
   }
}

public class Main {
   static int area(int a, int b) throws NegativeDimensionException {
      if(a<0 || b<0) {
         throw new NegativeDimensionException();
      }
      return a*b;
   }

   static void method1() throws NegativeDimensionException {
      System.out.println("Area is " + method1(-5,10));
   }

   public static void main(String[] args) {
      try
      {
         method1();
      }
      catch(NegativeDimensionException e)
      {
         System.out.println(e);
      }
   }
}
```

Firstly we generated exception in `area()`, and If we don't want to handle it inside that function, then we can pass it on to the calling function using `throws` keyword in the function name.

## finally Block

`finally` keyword is used in association with a try/catch block.

`finally` keyword is meant to execute whether an exception occurs or not.

Resources are needed to be closed in `finally` block.

It is useful when we're not handling all the exceptions in the program.

```java
public class Mai {
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

```sh
Finally block
```

Here, we haven't handled the particular exception, but still the `finally` block was executed.

## Try with resources

Garbage Collector only releases the heap memory(Heap memory is resource).

Programmer is responsible for releasing the other resources(Network, Database, Files).

```java
int method1() throws Exception {
   FileReader f;

   try
   {
      f = new FileReader("abc.txt");
      // Use File
   }
   finally
   {
      f.close();
   }

   return result;
}
```

This is a proper code, for handling with resources.

---

`try` with resources, automatically closes the resources.

To avoid `finally` block(to close the acquired resources), we use `try` with resources.

```java
int method1() throws Exception {

   try(FileReader f = new FileReader("abc.txt")) {
      // Use File
      return result;
   }
}
```

`try` block wil automatically release the acquired resources after it finishes its execution.

# Multithreading

Running multiple programs on a single machine or a computer is known as **multi-programming**.

Forms of Multiprogramming:

1. Multi User : Multiple users are using the same computer for running different programs.

2. Multi Tasking : Single user, but runs multiple tasks simultaneously in one computer.

Multithreading is part of Multi-tasking.

Java provides `Thread` class and `runnable` interface to achieve multithreading.

`Thread` class contains the actual mechanism for multithreading.

## Thread Class

```java
class MyThread extends Thread{
    @Override
    public void run(){
        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". Hello");
        }
    }
}

public class Main{
    public static void main(String[] args){
        Thread thd = new Thread();
        thd.start();

        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". World");
        }
    }
}
```

```java
public class Main extends Thread{
    @Override
    public void run(){
        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". Hello");
        }
    }

    public static void main(String[] args){
        Main dr = new Main();
        dr.start();

        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". World");
        }
    }
}
```

---

## Runnable Interface

```java
class MyRunnable implements Runnable{
    @Override
    public void run(){
        int i = 0;
        while (true)
        {
            i++;
            System.out.println(i + ". Hello");
        }
    }
}

public class Main{
    public static void main(String[] args){
        MyRunnable rnb = new MyRunnable();
        Thread thd = new Thread(rnb);
        thd.start();

        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". World");
        }
    }
}
```

```java
public class Main implements Runnable{
    @Override
    public void run(){
        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". Hello");
        }
    }

    public static void main(String[] args){
        Main dr = new Main();
        Thread thd = new Thread(dr);
        thd.start();

        int i = 0;
        while (true){
            i++;
            System.out.println(i + ". World");
        }
    }
}
```

## States of Thread

new -> ready -> running -> terminated

During Running state, it can go into one of the following states:

1. wait : Waiting to acquire some resource or Made to wait by some other thread.

2. timed wait : To make the thread to delay for some time using the sleep method, it is also known as sleep state.

3. blocked : It is similar to waiting state.

The First state of the thread is `new`, it stores the object of the thread.

When `start()` method is called then thread enters into the ready state, where it is ready to run.

## Thread Priorities

JAVA supports thread priorities from 1-10.

The priority of default thread is always 5.

The higher priority is given to the thread which gets the input or the data.

The thread with higher priority gets the more CPU time.

Multithreading features are provided by the operating systems but in java, JVM have its own scheduler.

## Methods of Thread Class

```java
// Constructors
Thread()
Thread(Runnable r)
Thread(String name) // Gives name to the thread
Thread(Runnable r, String name)
Thread(ThreadGroup g, String name)

// Getter and Setter methods
long getId();
String getName();
int getPriority();
ThreadState getState();
THreadGroup getThreadGroup(); // to	know the group to which the thread belongs

void setName(String name);
void setPriority(int p);
void setDaemon(Boolean d);  // Daemon thread is a background thread with least priority and no user interaction
                            // e.g. Garbage Collector in Java

// Enquiry
boolean isAlive();
boolean isDaemon();
boolean isInterrupted();

// Instance methods
void interrupt();   // It will stop doing the currently doing work, e.g. stop waiting/sleeping
void join();    // If a thread has finished its job, then instead of terminating, it can wait for other threads to finish
                // e.g. main() can wait until all the threads have finished
void join(long millseconds);
void run();
void start();

// Static Methods
int activeCount();
Thread currentThread();     // returns reference to current running thread
void yield();               // It can stop higher priority thread from starvating lower priority threads (Continue after the lower priority thread is finished)
void dumpstack();           // to know the contents in the stack or to know the depth of the stack.
```

```java
class MyThread extends Thread {
    public MyThread(String name) {
        // calling super class constructor i.e. Thread(String name)
        super(name);

        // Priority can be set in the main() also, using the Thread object
        setPriority(MIN_PRIORITY);

    }

    public void run() {
        int counter = 1;
        while (true) {
            System.out.println(counter);
            counter++;
            try {
                Thread.sleep(1000);
            } catch (Exception e) {
                System.out.println(e);
            }
        }
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t = new MyThread("Thread 1");
        System.out.println("Thread Id: " + t.getId());
        System.out.println("Thread name: " + t.getName());
        // t.setPriority(MIN_PRIORITY);
        System.out.println("Thread Priority: " + t.getPriority());
        System.out.println("Thread State: " + t.getState());
        t.start();
        System.out.println("Now, Thread State: " + t.getState());
        t.interrupt();
    }
}
```

Output:

```sh
Thread Id: 15
Thread name: Thread 1
Thread Priority: 1
Thread State: NEW
Now, Thread State: RUNNABLE
1
java.lang.InterruptedException: sleep interrupted
2
3
4
5
6
```

## Synchronization

```java
class MyData {
    // We can synchronize a block or a complete function
    public void display(String str) {
        synchronized (this) {
            for (int i = 0; i < str.length(); i++) {
                System.out.print(str.charAt(i));
            }
        }
    }

    // synchronized public void display(String str) {
    //      for (int i = 0; i < str.length(); i++) {
    //          System.out.print(str.charAt(i));
    //      }
    // }
}

class MyThread1 extends Thread {
    MyData d = new MyData();

    public MyThread1(MyData d) {
        this.d = d;
    }

    public void run() {
        d.display("Hello World");
    }
}

class MyThread2 extends Thread {
    MyData d = new MyData();

    public MyThread2(MyData d) {
        this.d = d;
    }

    public void run() {
        d.display("Welcome");
    }
}

public class Main {
    public static void main(String[] args) {
        MyData data = new MyData();

        MyThread1 thd1 = new MyThread1(data);
        MyThread2 thd2 = new MyThread2(data);

        thd2.start();
        thd1.start();
    }
}
```

The classes Mythread1 and Mythread2 access the data from the display class which is the shared object.

---

Example using ATM Machine:

```java
public class ATM {
    synchronized public void checkBalance(String name) {
        System.out.print(name);
        try {Thread.sleep(1000);} catch (Exception e) {}
        System.out.println(" is checking balance");
    }

    synchronized public void withdraw(String name, int amount) {
        System.out.print(name);
        try {Thread.sleep(1000);} catch (Exception e) {}
        System.out.println(" is withdrawing " + amount);
    }
}

public class Customer extends Thread {
    private String name;
    private int amount;
    private ATM atm;

    public Customer(String name, int amount, ATM atm) {
        this.name = name;
        this.amount = amount;
        this.atm = atm;
    }

    public void useATM() {
        atm.checkBalance(name);
        atm.withdraw(name, amount);
    }

    public void run() {
        useATM();
    }
}

public class Main {
    public static void main(String[] args) {
        ATM atm = new ATM();

        Customer c1 = new Customer("Jack", 2000, atm);
        Customer c2 = new Customer("John", 2000, atm);

        c1.start();
        c2.start();
    }
}

```

ATM Object is a shared resource, so we need to synchronize it.

## Inter Process Communication

It is a communication between the synchronized threads.

It is the communication between a single producer thread and a consumer thread.

The inter thread communication refers to the synchronization between the producer thread and the consumer thread to access the write and read method simultaneously.

To achieve the communication the flag = true and flag = false are used.

### Race Condition

When there is a single producer thread and multiple consumer threads.

All consumers do not execute at once, they do in a round robin fashion.

- When the count is zero then it is the producers turn.

- When the count is not zero then it is the consumers turn.

Since there are more than one consumers, any one of the consumer can access it.

The `notify()` method can open any thread as they may not be in an order.

    Assume one thread is accessing the shared resource and all other threads are blocked,
    when that thread has finished working it will inform other threads
    and any of the threads may access the object just like in a race.

So, in the above the count method is used to control the race.

The race condition can be avoided by the inter-thread condition.

> Notify() : This methods informs the blocked threads that they can now access the shared resource

# Annotations

Annotations are useful for giving meta data to class or interface or a method.

There are some Built-in annotations that are **Applied to code**:

These are set of annotations applied upon the code. This type of annotation gives the hint to the compiler so that it avoids showing errors and warnings.

The in-built annotations applied to the code are:

@Override:
It informs the compiler that the element is meant to override an element declared in a superclass.

@Deprecated:
It indicates that the marked element is deprecated and should no longer be used.

@FunctionalInterface:
Indicates that the type declaration is intended to be a functional interface (Lamda Expression i.e. only one method)

@SuppressWarnings:
It tells the compiler to suppress specific warnings that it would otherwise generate.

@SafeVarArgs:
When it is applied to a method or a constructor, it asserts that the code does not perform potentially unsafe operations on its varargs parameter.

# Lambda Expressions

Lambda expressions are used for de1ining anonymous expressions or nameless methods or functions.

Lambda expressions are defined with the help of interfaces.

If a interface have single abstract method then it is called the functional interface.

```java
@FunctionalInterface
interface MyLambda {
    public void display();
}

public class Main{
    public static void main(String[] args) {
        // Anonymous Method itself is acting as object
        MyLambda obj = () -> {System.out.println("Hello World")};
        // Here, We're overriding the display()

        // Since, it contains only single statement, we can write it as
        MyLambda obj = () -> System.out.println("Hello World");

        obj.display();
    }
}
```

## Parameters and Returning

```java
@FunctionalInterface
interface MyLambda {
    public void display(String str);
}

public class Main{
    public static void main(String[] args) {
        MyLambda obj = (s) -> System.out.println(s);

        obj.display("Hello World");
    }
}
```

```java
@FunctionalInterface
interface MyLambda {
    public int add(int a, int b);
}

public class Main{
    public static void main(String[] args) {
        MyLambda obj = (a,b) -> return a+b;

        // We can also remove the return keyword
        MyLambda obj = (a,b) -> a+b;

        int result = obj.add(10,20);

        System.out.println(result);
    }
}
```

## Variables Capture

```java
@FunctionalInterface
interface MyLambda {
    public void display();
}

class Demo{
    // This is a instance variable
    int temp=10;

    // This is a non static method
    public void method1(){
        int num = 5;
        MyLambda obj = () -> {
            int count=0;    // It acts like a local variable of a method
            count++;
            System.out.println(count);

            // Lambda Expression can use method variables
            // but they should be final or effectively final
            System.out.println(num);
            num++; // It is not allowed at all

            // Lambda Expression can use instance variables
            // Those variables can be modified as well
            System.out.println(temp);
            temp++;
        }
        num++;  // It is not allowed
                // If it is done then we can't use it inside lambda expression
    }
}

public class Main{
    public static void main(String[] args) {
        Demo d = new Demo();
        d.method1();
    }
}
```

Lamda Expressions can access/capture local variables only if they are declared `final` or are effectively final.
Also, those variables can never be modified inside the lamda expression.

## Lambda Expression as Parameter

```java
@FunctionalInterface
interface MyLambda {
    public int add(int a, int b);
}


class UserLambda{
    public void callLambda(MyLambda ml){
        ml.display();
    }
}

class Demo{
    public void method1(){
        UserLambda ul = new UserLambda();

        // We can pass the lambda expression as parameter
        ul.callLambda((a,b) -> a+b);
    }
}

public class Main{
    public static void main(String[] args) {
        Demo d = new Demo();
        d.method1();
    }
}
```

## Method Reference

We can use method reference to call a method

```java
@FunctionalInterface
interface MyLambda {
    public void display(String str);
}

public class Main{
    Main(String str){
        System.out.println(str);
    }

    void upper(String str){
        System.out.println(str.toUpperCase());
    }

    static void reverse(String str){
        StringBuffer sb = new StringBuffer(str);
        sb.reverse();
        System.out.println(sb);
    }

    public static void main(String[] args) {
        // Calling method of a class
        Main mn = new Main();
        MyLambda obj = mn::upper;
        obj.display("hello world");             => HELLO WORLD

        // Calling a method of a class
        MyLambda obj = System.out::println;
        obj.display("Hello World");             => Hello World

        // Calling a static method of a class
        MyLambda obj = Main::reverse;
        obj.display("Hello World");             => dlroW olleH

        // Calling a constructor of a class
        MyLambda obj = Main::new;
        obj.display("Hello World");             => Hello World
    }
}
```

---

Method Reference with parameters

```java
@FunctionalInterface
interface MyLambda {
    public int display(String str1, String str2);
}

public class Main{
    public static void main(String[] args) {
        MyLambda obj = String::compareTo;

        // The display() internally calls compareTo() method
        System.out.println(obj.display("Hello", "Hello"));  => 0
        System.out.println(obj.display("Hello", "World"));  => -15
    }
}
```
