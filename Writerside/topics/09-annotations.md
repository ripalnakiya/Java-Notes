# Annotations

Annotations provide metadata about program elements 
such as classes, interfaces, methods, fields, parameters, and constructors.

They do not change program logic directly, 
but they supply information to the compiler, build tools, or runtime frameworks.

Some built-in annotations are used directly in source code 
to help the compiler detect errors, suppress warnings, or enforce constraints.

## Common Built-in Annotations (Applied to Code)

`@Override`
    
Indicates that a method is intended to override a method from a superclass or interface.
The compiler will generate an error if the method does not correctly override a parent method.

`@Deprecated`

Marks a program element as deprecated, meaning it should no longer be used.
The compiler will generate a warning when deprecated elements are used.

`@FunctionalInterface`

Indicates that an interface is intended to be a functional interface, 
i.e., it must contain exactly one abstract method.
This enables use with lambda expressions and causes a compile-time error if the rule is violated.

`@SuppressWarnings`

Instructs the compiler to suppress specified warnings that would otherwise be generated.
Common values include "unchecked", "deprecation", and "rawtypes".

`@SafeVarargs`

When applied to a method or constructor, 
it asserts that the method does not perform unsafe operations 
on its varargs parameter involving generics.
It suppresses unchecked warnings related to heap pollution.
