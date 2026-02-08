# Static
<show-structure depth="2"/>

    Static Variables, Static Methods, Static Blocks, Static Inner Classes

It is useful for representing the information of a class.

Static members belongs to a class, 
and they can be shared by all the objects of the class.

Static members can be accessed just by using class name.

**Static methods** can access only static data members.

> The static members of a class are created in the method area.
{style="warning"}

## Static Blocks

Set of statements are written in the form of blocks and are made static.

It is used to initialize static data members.

It is executed before the main method at the time of class loading.

```Java
public class Main {
    static {
        System.out.println("Block 1");
    }

    public static void main(String[] args) {
        System.out.println("Main");
    }

    static {
        System.out.println("Block 2");
    }
}
```

Output:

```shell
Block 1
Block 2
Main
```

```Java
class Test {
    static {
        System.out.println("Block 1");
    }

    static {
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

```shell
Main
```

Since, class `Test` is not used, so it won't execute it's static blocks.
