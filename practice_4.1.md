## Question 4.1

1. To “capitalize” a string means to change the first letter of each word in the string to upper <br/>
case (if it is not already upper case). For example, a capitalized version of “Now is the time <br/>
to act!” is “Now Is The Time To Act!”. Write a subroutine named printCapitalized <br/>
that will print a capitalized version of a string to standard output. The string to be printed <br/>
should be a parameter to the subroutine. Test your subroutine with a main() routine that <br/>
gets a line of input from the user and applies the subroutine to it. <br/>
Note that a letter is the first letter of a word if it is not immediately preceded in <br/>
the string by another letter. Recall that there is a standard boolean-valued function <br/>
Character.isLetter(char) that can be used to test whether its parameter is a letter. <br/>
There is another standard char-valued function, Character.toUpperCase(char), that <br/>
returns a capitalized version of the single character passed to it as a parameter. That is, <br/>
if the parameter is a letter, it returns the upper-case version. If the parameter is not a <br/>
letter, it just returns a copy of the parameter. <br/>

## Answew

```
public class Chapter4Practice {
    public static void main(String[] args) {
        String str;     //sentence user input

        TextIO.putln("Please input a sentence: ");
        str = TextIO.getln();
        TextIO.putln("Capitalized version is: ");
        Capitalize(str);
    }
    static void Capitalize(String str){
        int i;          //i-th character of the sentence
        char ch;        //character of the sentence
        char prevch;     //previous one character of ch

        for(i = 0; i < str.length(); i++){
            ch = str.charAt(i);
            if(i == 0) {
                if (Character.isLetter(ch)) {
                    TextIO.put(Character.toUpperCase(ch));
                } else {
                    TextIO.put(ch);
                }
            }
            else{
                prevch = str.charAt(i-1);
                if(Character.isLetter(ch) && ! Character.isLetter(prevch)){
                    TextIO.put(Character.toUpperCase(ch));
                }
                else{
                    TextIO.put(ch);
                }
            }
        }
        TextIO.putln();
    }
}
```

## Note
I used str.replace() at first time to replace the old character with new capitalized character, <br/>
but this command is used to replace all old character in the string with new character, so <br/>
if I input "this is a test" it will come out "ThIs Is A TesT".
