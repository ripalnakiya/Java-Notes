# C++ vs Java
<show-structure depth="2"/>

## 1. Multiple Inheritance

**C++**

A class can inherit from multiple classes. 
But, Multiple inheritance has diamond problem.

```c++
class A {};
class B {};
class C : public A, public B {};
```

**Java**

A class can extend only one class. Multiple inheritance of behavior is not allowed.

Multiple inheritance of type is allowed via interfaces.

```Java
class C extends A implements B, D {}
```

## 2. Nested Classes

- **C++** has nested classes, but:
  - They do not have an implicit reference to the outer class.
  - They behave like normal classes scoped inside another class.
  - No concept of “inner class tied to an object”.

- **Java** goes all-in on nesting:
  - Static nested classes
  - Non-static inner classes (have access to outer object)
  - Local classes (inside methods)
  - Anonymous classes

```Java
class Outer {
  class Inner {
    void access() {
      System.out.println(Outer.this);
    }
  }
}
```

Java nested classes are tightly integrated with the object model.

C++ nested classes are mostly about namespacing, not object relationships.

## 3. Memory Management

- **C++**
  - Manual memory management.
  - `new`, `delete`, smart pointers, RAII.
  - You control lifetime.

- **Java**
  - Automatic Garbage Collection.
  - No delete.
  - Objects die when JVM decides they’ve suffered enough.

## 4. Pointers vs References

- **C++**
  - Full-blown pointers.
  - Pointer arithmetic.
  - Null and dangling pointers.

- **Java**
  - No pointers (publicly).
  - Only references.
  - No pointer arithmetic.

## 5. Platform Dependency

- **C++**
  - Compiled to machine code.
  - Platform-dependent binaries.
  - Fast. Very fast.

- **Java**
  - Compiled to bytecode, runs on JVM.
  - “Write once, run anywhere” (after installing the JVM everywhere).

## 6. Performance

- **C++**
  - Generally faster.
  - No GC pauses.
  - Predictable latency.
  - Preferred for systems, games, engines.

- **Java**
  - Slightly slower in raw terms.
  - JIT compiler and JVM optimizations narrow the gap.
  - GC can introduce pauses.

## 7. Operator Overloading

- **C++**
  - Supported.
  - You can overload almost anything.

- **Java**
  - Not supported (except + for strings).
  - Intentional decision to keep code readable.

## 8. Templates vs Generics

- **C++**
  - Templates: compile-time, very powerful.

- **Java**
  - Generics: type erasure at runtime.
  - Less powerful, more predictable.

## 9. Exceptions

- **C++**
  - No checked exceptions.

- **Java**
  - Checked exceptions exist.
  - Compiler forces you to deal with them.
