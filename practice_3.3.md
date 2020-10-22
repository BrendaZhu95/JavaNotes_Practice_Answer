## Question 3.3

3. Write a program that will evaluate simple expressions such as 17 + 3 and 3.14159 * 4.7.
The expressions are to be typed in by the user. The input always consist of a number,
followed by an operator, followed by another number. The operators that are allowed are
+, -, *, and /. You can read the numbers with TextIO.getDouble() and the operator
with TextIO.getChar(). Your program should read an expression, print its value, read
another expression, print its value, and so on. The program should end when the user
enters 0 as the first number on the line.


## Answer

```
public class Chap3Practice {
    public static void main(String[] args) {
        double x;
        double y;
        char operator;
        double answer;

        TextIO.putln("Please input something like 3+2 or 4*5.");
        TextIO.putln("(Please note that operator could only be +, -, *, /)");
        TextIO.putln("(to end, input 0 as first number)");

        while (true) {
            x = TextIO.getDouble();
            if (x == 0) {
                TextIO.putln("Thank you!");
                break;
            } else {
                operator = TextIO.getChar();
                y = TextIO.getDouble();

                if (operator == '+') {
                    answer = x + y;
                    TextIO.putln("The final answer is: " + answer);
                } else if (operator == '-') {
                    answer = x - y;
                    TextIO.putln("The final answer is: " + answer);
                } else if (operator == '*') {
                    answer = x * y;
                    TextIO.putln("The final answer is: " + answer);
                } else if (operator == '/') {
                    answer = x / y;
                    TextIO.putln("The final answer is: " + answer);
                } else {
                    TextIO.putln("The operator is not applicable!");
                }
            }
        }
    }
```
