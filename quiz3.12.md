## Question 13:

What output is produced by the following program segment? Why? </br>
(Recall that name.charAt(i) is the i-th character in the string, name.)
</br>
</br>

```
String name;
int i;
boolean startWord;

name = "Richard M. Nixon";
startWord = true;
for (i = 0; i < name.length(); i++) {
   if (startWord)
      System.out.println(name.charAt(i));
   if (name.charAt(i) == ' ')
      startWord = true;
   else
      startWord = false;
}
```

## Answer:

The output from this program consists of the three lines:</br>
```
    R
    M
    N
```

As the for loop in this code segment is executed, name.charAt(i) represents **each of the characters** </br>
in the string "Richard M. Nixon" in succession. The statement System.out.println(name.charAt(i)) outputs</br>
the single character name.charAt(i) on a line by itself. However, this output statement occurs inside </br>
an if statement, so only some of the characters are output. The character is output if startWord is true. </br>
This variable is initialized to true, so when i is 0, startWord is true, and the first character in the string,</br>
'R', is output. Then, since 'R' does not equal ' ', startWorld becomes false, **so no more characters are output </br>
until startWord becomes true again.** This happens when name.charAt(i) is a space, that is, just before the 'M' </br>
is processed and again just before the 'N' is processed. In fact whatever the value of name, this for statement</br>
would print the first character in name and **every character in name that follows a space**. (It is almost true </br>
that this for statement prints the first character of each word in the string, but something goes wrong when </br>
the first character is a space or when there are two spaces in a row.)</br>
