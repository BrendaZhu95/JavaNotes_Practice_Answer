## Question 4.3

Write a function that simulates rolling a pair of dice until the total on the dice comes up<br/>
to be a given number. The number that you are rolling for is a parameter to the function.<br/>
The number of times you have to roll the dice is the return value of the function. The<br/>
parameter should be one of the possible totals: 2, 3, . . . , 12. The function should throw<br/>
an IllegalArgumentException if this is not the case. Use your function in a program that<br/>
computes and prints the number of rolls it takes to get snake eyes. (Snake eyes means<br/>
that the total showing on the dice is 2.) <br/>

## Answer
```
public class Chapter4Practice {
    public static void main(String[] args) {
        int n;        //user input number

        do {
            TextIO.putln("Please input a number from 2 to 12: ");
            n = TextIO.getlnInt();

            if (n < 2 || n > 12){
                TextIO.putln("you input a wrong number, please input again: ");}
            else{
                CountNumberOfRolls(n);
            }

        }while (true);
    }

    static void CountNumberOfRolls(int number){
        int first_dice;     //number of first dice
        int second_dice;    //number of second dice
        int sum;     //sum of two dices
        int count;     //number of times of rolling to get n

        count = 0;

        do {
            first_dice = (int)(Math.random()*6) + 1;
            second_dice = (int)(Math.random()*6) + 1;
            sum = first_dice + second_dice;
            if (number == sum) {
                TextIO.putln("(" + first_dice + ',' + second_dice + ')');
                count++;
                TextIO.putln("It tooks " + count + " times roll to get the number " + number);
                break;
            } else {
                TextIO.putln("(" + first_dice + ',' + second_dice + ')');
                count++;
            }
        }while (true);
    }
}
```

## Note
The question asks for "Snake eyes" rolling number, the answer is for all possible input number, <br/>
if we want to know how many times of rolling to get snake eyes, we can just input 2 to get the answer.
