# Functions

```java
public class FunctionPower
{

    public static int power(int num, int pow)
    {
        int result = 1;
        for(int i = 0; i < pow ; i++)
        {
            result = result * num;
        }
        return result;
    }

    public static void main(String[] args)
    {
        System.out.println(power(2,3));
    }
}

```
