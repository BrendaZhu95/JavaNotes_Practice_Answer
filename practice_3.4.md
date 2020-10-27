## Question 3.4
4. Write a program that reads one line of input text and breaks it up into words. The</br>
words should be output one per line. A word is defined to be a sequence of letters. Any</br>
characters in the input that are not letters should be discarded. For example, if the user</br>
inputs the line</br>
He said, "That’s not a good idea."
then the output of the program should be
```
He
said
that
s
not
a
good
idea
```

An improved version of the program would list “that’s” as a single word. An apostrophe </br>
can be considered to be part of a word if there is a letter on each side of the apostrophe.</br>
To test whether a character is a letter, you might use (ch >= ’a’ && ch <= ’z’) ||</br>
(ch >= ’A’ && ch <= ’Z’). However, this only works in English and similar languages.</br>
A better choice is to call the standard function Character.isLetter(ch), which returns</br>
a boolean value of true if ch is a letter and false if it is not. This works for any Unicode</br>
character.

## Answer

```
public class Chap3Practice {
    public static void main(String[] args) {
        String str;
        char letter;
        int i;
        boolean didCR;

        TextIO.putln("Please input your statement: ");
        str = TextIO.getln();
        didCR = true;

        for ( i = 0;  i < str.length(); i++ ) {
            letter = str.charAt(i);
            if ( Character.isLetter(letter) ) {
                System.out.print(letter);
                didCR = false;  // previous output was not a CR
            }
            else {
                if ( didCR == false ) {  // output CR, if previous output was NOT a CR
                    System.out.println();
                    didCR = true;  // previous output was a CR
                }
            }
        }
    }
}
```

## Notes
The space is also counted as a CR, so if there is a space, it will also goes to else statment, </br>
and if the previous one is word, it will print enter, if not, it will print nothing, </br>
until there comes another word, the didCR will become false again.
