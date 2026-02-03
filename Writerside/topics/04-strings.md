# Strings

String is collection of characters.

String syntax:

```Java
String str = "Hello";
// or
String str = new String("Hello");
```

Strings are **Immutable**.

## String Concatenation

```Java
String fName = "Foo";
String lName = "Bar";

String name = fName + " " + lName;
```

When using concatenation operator with strings, we should be careful.

```Java
int x = 10, y = 20;
System.out.println(x + y + " is Sum");          // 30 is Sum
```

```Java
int x = 10, y = 20;
System.out.println("Sum is " + x + y);          // Sum is 1020
```

This happened because of precedence...

Firstly, It became ("Sum is " + x) = `Sum is 10`

Then, It became ("Sum is 10" + y) = `Sum is 1020`

So, we can use braces to set the precedence.

```Java
int x = 10, y = 20;
System.out.println("Sum is " + (x + y));          // Sum is 30
```

## Accessing String Characters

```Java
String str = "Foo Bar";

System.out.println(str.charAt(1));              // o
```

We can access each character using this method.

## String Comparison

```Java
String s1 = "Foo";
String s2 = "Foo";
String s3 = new String("Foo");

System.out.println( s1 == s2 );             // true

System.out.println( s1 == s3 );             // false
System.out.println( s1.equals(s3) );        // true
```

This happened because, when we created string variable `s2` without new keyword,
String `s2` also started pointing to the same string to which `s1` is pointing.

It is also called **Interning**.

But, using `equals()` function, 
the actual value of the string was compared, instead of its pointer.

## String Lexicographic Comparison

```Java
str1.compareTo(str2);
```

If value is 0, means strings are equal.
If value is less than 0, means `str1` is less than `str2`
If value is greater than 0, means `str1` is greater than `str2`

For example,

- `Java` is greater than `Cpp`, because (74 > 67) i.e. (J > C)
- `ABC` is smaller than `abc`, because (65 < 97) i.e. (A < a)

## String Builder

When we modify existing string, a new string is created inside the memory.

For example,

```Java
String str = new String("Hello");

str = str + 'A';
```

Now, a new string is created `HelloA`, and `str` will point to the new string.

This is because, `Strings` are immutable in java.

**String Builder** is a mutable string class.

```Java
StringBuilder sb = new StringBuilder("Hello");
```

`toString()` functions converts a object into string.

For example,

```Java
int a = 10;
a.toString();               // Incorrect, since a is not object

char ch = 'a';
ch.toString();              // Incorrect, since ch is not object

Integer a = 10;
a.toString();               // Correct

Character ch = 'a';
ch.toString();              // Correct
```

### Adding Characters

We can add characters in the `StringBuilder` object, by using `append()` method.

It appends character to the end of the string.

```Java
StringBuilder sb = new StringBuilder("");
sb.append("Hello");
System.out.println(sb);
```
