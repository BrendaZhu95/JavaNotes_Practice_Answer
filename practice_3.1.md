>1. How many times do you have to roll a pair of dice before they come up snake eyes? You
>could do the experiment by rolling the dice by hand. Write a computer program that
>simulates the experiment. The program should report the number of rolls that it makes
>before the dice come up snake eyes. (Note: “Snake eyes” means that both dice show a
>value of 1.)

###Answer

(```)
public class Chap3Practice {
    public static void main(String[] args) {
        int first_dice;
        int second_dice;
        int count;

        count = 0;

        while (true){
            first_dice = (int) (Math.random() * 6) + 1;
            second_dice = (int) (Math.random() * 6) + 1;
            if (first_dice == 1 && second_dice ==1 ) {
                    count++;
                    System.out.println("(" + first_dice + "," + second_dice + ")");
                    System.out.println("Here comes snake eye!");
                    System.out.println("Snake eye comes after " + count + " times rolls");
                    break;
            } else {
                count++;
                System.out.println("(" + first_dice + "," + second_dice + ")");
            }
        }
    }
}
(```)
