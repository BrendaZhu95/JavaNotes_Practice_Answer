## Question 4.2

2. The hexadecimal digits are the ordinary, base-10 digits ’0’ through ’9’ plus the letters ’A’<br/>
through ’F’. In the hexadecimal system, these digits represent the values 0 through 15,<br/>
respectively. Write a function named hexValue that uses a switch statement to find the<br/>
hexadecimal value of a given character. The character is a parameter to the function, and<br/>
its hexadecimal value is the return value of the function. You should count lower case<br/>
letters ’a’ through ’f’ as having the same value as the corresponding upper case letters.<br/>
If the parameter is not one of the legal hexadecimal digits, return -1 as the value of the<br/>
function.<br/>
A hexadecimal integer is a sequence of hexadecimal digits, such as 34A7, FF8, 174204,<br/>
or FADE. If str is a string containing a hexadecimal integer, then the corresponding<br/>
base-10 integer can be computed as follows:<br/>
value = 0;<br/>
for ( i = 0; i < str.length(); i++ )<br/>
value = value*16 + hexValue( str.charAt(i) );<br/>
Of course, this is not valid if str contains any characters that are not hexadecimal digits.<br/>
Write a program that reads a string from the user. If all the characters in the string are<br/>
hexadecimal digits, print out the corresponding base-10 value. If not, print out an error<br/>
message.<br/>

## Answer
```
public class Chapter4Practice {
    public static void main(String[] args) {
        String hex;     //Hexnumber that user input
        long dec;       //decimal equivalent of hexnumber
        int i;         //position in hexnumber
        do {
            TextIO.put("Enter a hexadecimal number: ");
            hex = TextIO.getlnWord();
            dec = 0;
            for (i = 0; i < hex.length(); i++) {
                int digit = hexValue(hex.charAt(i));
                if (digit == -1) {
                    TextIO.putln("Error: Input is not a hexadecimal number.");
                    return;
                }
                dec = 16 * dec + digit;
            }
            TextIO.putln("Base - 10 value:   " + dec);
        }while(true);
    }

    static int hexValue(char ch){
        switch (ch) {
            case '0':
                return 0;
            case '1':
                return 1;
            case '2':
                return 2;
            case '3':
                return 3;
            case '4':
                return 4;
            case '5':
                return 5;
            case '6':
                return 6;
            case '7':
                return 7;
            case '8':
                return 8;
            case '9':
                return 9;
            case 'a':
            case 'A':
                return 10;
            case 'b':
            case 'B':
                return 11;
            case 'c':
            case 'C':
                return 12;
            case 'd':
            case 'D':
                return 13;
            case 'e':
            case 'E':
                return 14;
            case 'f':
            case 'F':
                return 15;
            default:
                return -1;
        }
    }
}
```

## Note
The program will run until user input a wrong number in.<br/>
-- how to calculate hexadecimal number to 10 base?<br/>
> How to convert from hex to decimal<br/>
> A regular decimal number is the sum of the digits multiplied with power of 10.<br/>
> 137 in base 10 is equal to each digit multiplied with its corresponding power of 10:<br/>
> 13710 = 1×102+3×101+7×100 = 100+30+7<br/>
> Hex numbers are read the same way, but each digit counts power of 16 instead of power of 10.<br/>
> For hex number with n digits:<br/>
> dn-1 ... d3 d2 d1 d0<br/>
> Multiply each digit of the hex number with its corresponding power of 16 and sum:<br/>
> decimal = dn-1×16n-1 + ... + d3×163 + d2×162 + d1×161+d0×160<br/>
> Example<br/>
> 3B in base 16 is equal to each digit multiplied with its corresponding 16n:<br/>
> 3B16 = 3×16^1+11×16^0 = 48+11 = 5910<br/>

十六进制 → 十进制
　　方法：十六进制数从低位到高位（即从右往左）计算，第0位的权值是16的0次方，第1位的权值是16的1次方，第2位的权值是16的2次方，依次递增下去，把最后的结果相加的值就是十进制的值了。

　　十六进制就是逢16进1，十六进制的16个数为0123456789ABCDEF。

　　例：将十六进制的(2B)H转换为十进制的步骤如下：

1. 第0位 B x 16^0 = 11；

2. 第1位 2 x 16^1 = 32；

3. 读数，把结果值相加，11+32=43，即(2B)H=(43)D。
