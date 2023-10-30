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
