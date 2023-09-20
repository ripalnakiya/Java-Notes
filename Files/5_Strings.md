# Strings

String is collection of characters.

String syntax:

```java
String str = "Hello";
// or
String str = new String("Hello");
```

Strings are Immutable.

## String Length

```java
String str = "Captain jack";
System.out.println(str.length());           => 12
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

## String Characters

```java
String str = "Captain jack";

System.out.println(str.charAt(1));              => a
```

We can also access each character using this method.

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

## String Substring

```java
String str = "Captain jack";

System.out.println(str.substring(0,3));              => Cap
```

It will include characters from (start index) upto (end index - 1).

> 0 1 2 (not 3)

## String Lexicographic Comparison

```java
str1.compareTo(str2);
```

If value is 0, means strings are equal.
If value is less than 0, means str1 is less than str2
If value is greater than 0, means str1 is greater than str2

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
