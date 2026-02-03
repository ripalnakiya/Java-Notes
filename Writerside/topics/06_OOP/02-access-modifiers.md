# Access Modifiers

## `private`
- Only accessible inside that class
- **Not** accessible inside the subclass
- **Not** accessible inside the non-subclass (`main` method)
- **Not** accessible inside the subclass of **another package**
- **Not** accessible inside the non-subclass of **another package**

## Default
- Accessible inside that class
- Accessible inside the subclass
- Accessible inside the non-subclass (`main` method)
- **Not** accessible inside the subclass of **another package**
- **Not** accessible inside the non-subclass of **another package**

(They are not accessible outside its package)

## `protected`
- Accessible inside that class
- Accessible inside the subclass
- Accessible inside the non-subclass (`main` method)
- Accessible inside the subclass of **another package**
- **Not** accessible only inside the **non-subclass** of **another package**

## `public`
- Accessible everywhere
