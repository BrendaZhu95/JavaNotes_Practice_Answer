## Question 

4. This exercise builds on Exercise 4.3. Every time you roll the dice repeatedly, trying to<br/>
get a given total, the number of rolls it takes can be different. The question naturally<br/>
arises, what’s the average number of rolls to get a given total? Write a function that<br/>
performs the experiment of rolling to get a given total 10000 times. The desired total is<br/>
162 CHAPTER 4. SUBROUTINES<br/>
a parameter to the subroutine. The average number of rolls is the return value. Each<br/>
individual experiment should be done by calling the function you wrote for Exercise 4.3.<br/>
Now, write a main program that will call your function once for each of the possible totals<br/>
(2, 3, ..., 12).<br/>

## Note
The answer code is for custermized times and given total.<br/>
If we only need no more than 5 tests to calculate an average, it will show all dice results and <br/>
tell counts of everytime; if it's more than 5 tests, it would be too many printings on the screen, <br/>
so the program will only tell the final results of total counts and average counts.

## Answer

```
public class RollForAnyTimes {
    public static void main(String[] args) {
        int n;        //user input number
        double times;    //number of rolling

        do {
            TextIO.putln("Please input a number from 2 to 12: (input 0 if you want to stop)");
            n = TextIO.getlnInt();
            if(n == 0){break;}
            TextIO.putln("Please input number of tests you want: ");
            times = TextIO.getlnInt();

            if (n < 2 || n > 12){
                TextIO.putln("you input a wrong number, please input again: ");}
            else{
                if (times < 5){
                    AvgCount(times, n);
                }
                else{AvgCountLarge(times, n);
                }
            }
        }while (true);
    }

    static void AvgCount(double times, int number){
        int first_dice;     //number of first dice
        int second_dice;    //number of second dice
        int sum;     //sum of two dices
        int count;     //times of rolling to get n
        int j;       //number of times to do test
        double total_count;
        double avg_count;

        total_count=0;

        for(j = 1; j <= times; j++){
            count = 0;
            do {
                first_dice = (int)(Math.random()*6) + 1;
                second_dice = (int)(Math.random()*6) + 1;
                sum = first_dice + second_dice;
                if (number == sum) {
                    TextIO.putln("(" + first_dice + ',' + second_dice + ')');
                    TextIO.putln("-------------------------");
                    count++;
                    TextIO.putln("It tooks " + count + " times roll to get the number " + number);
                    break;
                } else {
                    TextIO.putln("(" + first_dice + ',' + second_dice + ')');
                    count++;
                }
            }while (true);
            total_count = total_count + count;
            TextIO.putln("Total count of " + times + " times tests is " + total_count);
        }
        avg_count = total_count/times;
        TextIO.putln("The average count of the number is " + avg_count);
    }

    static void AvgCountLarge(double times, int number){
        int first_dice;     //number of first dice
        int second_dice;    //number of second dice
        int sum;     //sum of two dices
        int count;     //times of rolling to get n
        int j;       //number of times to do test
        double total_count;
        double avg_count;

        total_count=0;

        for(j = 1; j <= times; j++){
            count = 0;
            do {
                first_dice = (int)(Math.random()*6) + 1;
                second_dice = (int)(Math.random()*6) + 1;
                sum = first_dice + second_dice;
                if (number == sum) {
                    count++;
                    break;
                } else {
                    count++;
                }
            }while (true);
            total_count = total_count + count;
        }
        TextIO.putln("Total count of " + times + " times tests is " + total_count);
        avg_count = total_count/times;
        TextIO.putln("The average count of the number is " + avg_count);
    }
}
```
