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

## Answer from http://math.hws.edu/javanotes/c4/ex3-ans.html
```/**
 * This program simulates rolling a pair of dice over and over until the
 * total showing on the two dice is 2.  It reports the number of rolls 
 * it took to get a 2.  (This was written to test the subroutine, rollFor.)
 */
public class RollFor2 {
  
   public static void main(String[] args) {
      int numberOfRolls;  // Number of rolls to get a 2.
      numberOfRolls = rollFor(2);
      System.out.println("It took " + numberOfRolls + " rolls to get snake eyes.");
   }  // end main()
   
   /**
    * Simulates rolling a pair of dice until a given total comes up.
    * Precondition:  The desired total is between 2 and 12, inclusive.
    * @param N the total that we want to get on the dice
    * @return the number of times the dice are rolled before the
    *    desired total occurs
    * @throws IllegalArgumentException if the parameter, N, is not a number
    *    that could possibly come up on a pair of dice
    */
   public static int rollFor( int N ) {
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

}  // end class RollFor2
```


## Note
The question asks for "Snake eyes" rolling number, the answer is for all possible input number, <br/>
if we want to know how many times of rolling to get snake eyes, we can just input 2 to get the answer.
