## Question

2. Which integer between 1 and 10000 has the largest number of divisors, and how many
divisors does it have? Write a program to find the answers and print out the results. It is
possible that several integers in this range have the same, maximum number of divisors.
Your program only has to print out one of them. Subsection 3.4.2 discussed divisors. The
source code for that example is CountDivisors.java.
You might need some hints about how to find a maximum value. The basic idea is
to go through all the integers, keeping track of the largest number of divisors that you’ve
seen so far. Also, keep track of the integer that had that number of divisors.

## Answer

```
public class Chap3Practice {
    public static void main(String[] args) {
        int m;    //one of the integers
        int n;    //a number to be tested if it's a divisor of m
        int divisor_count;    //number of divisors of m
        int max_i;        //maximum number with maximum divisors
        int max_i_divisor_count;    //number of maximum divisors of max_i

        max_i = 1;
        max_i_divisor_count = 1;   //start with the fact that 1 has 1 divisor

        for(m = 2; m <= 10000; m++){
            divisor_count = 0;
            for(n = 1; n <= m; n++){
                if(m % n == 0)
                    divisor_count++;}
            if(divisor_count >= max_i_divisor_count){
                        max_i = m;
                        max_i_divisor_count = divisor_count;
            }
        }
        System.out.println("The max integer from 1 to 10000 has the most divisor is " + max_i);
        System.out.println("The number of divisor is " + max_i_divisor_count);
    }
}
```
