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
