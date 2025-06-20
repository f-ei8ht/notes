Remember always 
recursion is when a function calls it self  not when it is called inside some other function it should be called inside its function only and there should be a base case or condition to stop recursion or from infinite loop recursion may also leed to stackoverflow errors if oyu call yourself many times than it was intended 

we make a recursive call to make the problem small if it not getting smaller then no use for recursion or it is of no use.
```java
package Recursion;

  

public class Recursion {

    public static void main(String[] args) {

        long n = 3;

        long result = fac((fac(n)));

        System.out.println(result);

    }

  

    static long fac(long n) {

        if (n == 1)

            return 1;

        return n * fac(--n);

    }

}
```
