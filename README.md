PRAC 1
Aim: Create an ABAP program that declares 2 variables and display the sum of 2 variables in output using write statement.

Theory: 
Steps to Create the ABAP Program in SE38

1. Access SE38 (ABAP Editor):

o Go to the SAP GUI and enter the transaction code SE38 in the command field, then press Enter.

o This opens the ABAP Editor where you can create, edit, and run ABAP programs.

2. Create a New Program:

o In SE38, enter a program name starting with Z or Y (custom naming 
conventions in SAP), such as ZPRACT1_SUM.

o Select Create to open the program creation screen.

o Enter a title for your program, such as “Sum of Two Numbers.”

o Choose Type as "Exectable Program" since you want to run it directly.

o Click Save, select a package or save it as a local object ($TMP), and press 
Enter.

3. Write the ABAP Code:

o In the editor, write your ABAP code to declare two variables, calculate their sum, and display the result.

CODE:

REPORT ZPRACT1_SUM. " Program Name

* Declare variables

DATA: num1 TYPE I VALUE 20, " First number with an initial value of 10

 num2 TYPE I VALUE 10, " Second number with an initial value of 20

 sum TYPE I,

 sub TYPE I,

 mul TYPE I,

 div TYPE I.

* Calculate the sum

sum = num1 + num2. " Add num1 and num2, store result in sum

sub = num1 - num2.

mul = num1 * num2.
div = num1 / num2.
*To Display the Output.
WRITE : / 'Program by: Himanshu Singh',
/'num1', num1,
/ 'num2', num2,
/ 'Addition', sum,
/ 'Subtraction', sub,
/ 'Multiplication', mul,
/ 'Division', div.


PRAC 2
Aim: Write an ABAP program that uses an IF statement to check if a number is positive, 
negative, or zero, and displays the result.

Theory:
1) Declare Input Parameter: The program starts by declaring an input parameter for a 
number using the PARAMETERS statement. This allows the user to enter a number 
when the program runs.
2) Use an IF Statement: An IF statement is used to evaluate the number:
o If the number is greater than 0, it is positive.
o If the number is less than 0, it is negative.
o If the number is 0, it is identified as zero.
3) Display the Result: The WRITE statement is used to display whether the number is 
positive, negative, or zero.

CODE:
REPORT ZPRACT2_IF_STATEMENT. " Program name

* Declare variables

DATA: user_input TYPE c LENGTH 10, " Variable to store user input of type numc
 number TYPE I. " Integer variable to store the converted number

* Get input from user

PARAMETERS: p_input TYPE c LENGTH 10. " Accept user input

* Convert input to integer

number = p_input.

* Check if the number is positive, negative, or zero

IF number > 0.

 WRITE: / 'The number is positive.'.

ELSEIF number < 0.

 WRITE: / 'The number is negative.'.

ELSE.

 WRITE: / 'The number is zero.'.

ENDIF.

Write : / 'Program By: Himanshu Singh - 010'.


PRAC 3 
