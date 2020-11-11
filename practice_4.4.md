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


## Other Answers
The text book is assuming 10000 times of rolls, here is an answer from https://edoras.sdsu.edu/doc/javanotes5.0.1/c4/ex4-ans.html <br/>

```
/**
 * This program preforms the following type of experiment:  Given a desired 
 * total roll, such as 7, roll a pair of dice until the given total comes up, 
 * and count how many rolls are necessary.  Now do the over and over, and
 * find the average number of rolls.  The number of times the experiment is 
 * repeated is given by the constant, NUMBER_OF_EXPERIMENTS.  The average is
 * computed and printed out for each possible roll = 2, 3, ..., 12. 
 */

public class DiceRollStats {

   /**
    * The number of times that the the experiment "roll for a given total"
    * is to be repeated.  The program performs this many experiments, and
    * prints the average of the result, for each possible roll value, 
    */
   static final int NUMBER_OF_EXPERIMENTS = 10000;

   public static void main(String[] args) {
       double average;  // The average number of rolls to get a given total.
       System.out.println("Total On Dice     Average Number of Rolls");
       System.out.println("-------------     -----------------------");
       for ( int dice = 2;  dice <= 12;  dice++ ) {
          average = getAverageRollCount( dice );
          System.out.printf("%10d%22.4f\n", dice, average);
             // Use 10 spaces to output dice, and use 22 spaces to output
             // average, with 4 digits after the decimal.
       }
   } 
   
   /**
    * Find the average number of times a pair of dice must be rolled to get
    * a given total.  The experiment of rolling for the given total is
    * repeated NUMBER_OF_EXPERIMENTS times and the average number of rolls
    * over all the experiments is computed.
    * Precondition:  The given total must be be between 2
    * and 12, inclusive.
    * @param roll the total that we want to get on the dice
    * @return the average number of rolls that it taks to get the specified
    *    total
    */
   static double getAverageRollCount( int roll ) {
       int rollCountThisExperiment;  // Number of rolls in one experiment.
       int rollTotal;  // Total number of rolls in all the experiments.
       double averageRollCount;  // Average number of rolls per experiment.
       rollTotal = 0;
       for ( int i = 0;  i < NUMBER_OF_EXPERIMENTS;  i++ ) {
          rollCountThisExperiment = rollFor( roll );
          rollTotal += rollCountThisExperiment;
       }
       averageRollCount = ((double)rollTotal) / NUMBER_OF_EXPERIMENTS;
       return averageRollCount;
   }
   
   /**
    * Simulates rolling a pair of dice until a given total comes up.
    * Precondition:  The desired total is between 2 and 12, inclusive.
    * @param N the total that we want to get on the dice
    * @return the number of times the dice are rolled before the
    *    desired total occurs
    * @throws IllegalArgumentException if the parameter, N, is not a number
    *    that could possibly come up on a pair of dice
    */
   static int rollFor( int N ) {
       if ( N < 2 || N > 12 )
          throw new IllegalArgumentException("Impossible total for a pair of dice.");
       int die1, die2;  // Numbers between 1 and 6 representing the dice.
       int roll;        // Total showing on dice.
       int rollCt;      // Number of rolls made.
       rollCt = 0;
       do {
          die1 = (int)(Math.random()*6) + 1;
          die2 = (int)(Math.random()*6) + 1;
          roll = die1 + die2;
          rollCt++;
       } while ( roll != N );
       return rollCt;
   }
   
}  // end DiceRollStats
```
