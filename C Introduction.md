# Introduction

`int` is used to hold whole numbers (integers)
`float` and `double` store decimals.
`float` is similar to `double`, but has less precision and requires less memory.
`char` holds a single character.
The `const` keyword is used to define a constant, which is a variable that cannot be changed (is read-only)

You can use basic math operators to perform calculations with values and variables.

- `+` is addition
- `-` is subtraction
- `/` is division

Dividing `integers` results in an integer, while dividing `floats` results in a float.

- `%` finds the remainder of a division.

- `//` starts a single line comment.
- `/* */` is used for multi-line comments.

## THE SCANF()

The `scanf` function is used to take user input based on the given format specifier.
It works similar to the `printf()` function.  
Remember, you need to use the `&` sign before the variable name in the `scanf()` function

it is used to get the address of the variable, which tells scanf() where to store the
given value.

It is important to use the correct type for the variable that will store the input.
Examples:

```c
              int num;
              scanf("%d", &num);
              printf("You entered: %d", num);
```

_If the user enters a number when prompted by the scanf function, the printf statement will output the entered number._

          For example, if the user enters 42, the output will be:

                You entered: 42

The `%d` format specifier in the printf statement corresponds to an integer value, and the `num` variable holds the value entered by the user using `scanf`.

Therefore, when the printf statement is executed, it will display the entered number in place of the `%d` format specifier.

```c
              float x;
              scanf("%f", &x);
              printf("%f", x/100);
```

_If the user enters a floating-point number when prompted by scanf, the printf statement will output the value of x divided by 100._

           For example, if the user enters 500.0, the output will be:

               5.000000

           This is because x is divided by 100, resulting in 5.0.


The `%f` format specifier in the `printf` statement is used to display the floating-point value.

```c
              int x, y;
              scanf("%d %d", &x, &y);
              printf("%d", x+y)
```

\*If the user enters two integer values separated by a space when prompted by `scanf`, the `printf` statement will output the sum of the two values.

For example, if the user enters `10 20`, the output will be:

               30

This is because `x` and `y` are assigned the values 10 and 20, respectively, using the `%d` format specifier in the `scanf` statement. The `printf`
statement then adds `x` and `y` together and displays the sum using the `%d` format specifier.

## IF STATEMENT

The following comparison operators may be used to form the condition:

- `<` less than
- `>` greater than
- `!=` not equal to
- `==` equal to
- `<=` less than or equal to
- `>=` greater than or equal to

### IF ELSE

statements work the same as javascript

```c
           if(score >= 100) {
           printf("Level Completed!");
           }
           else {
           printf("Game Over");
           }
```

### ELSE IF STATEMENT

In case you need to check for multiple different values, you can use else if statements.
For example, let's check the position variable and output the corresponding medal:

```c
           if(position == 1) {
           printf("Gold");
           }
           else if(position == 2) {
           printf("Silver");
           }
           else {
           printf("Something else");
           }
      // You can include as many else if statements as you need.
```

### SWITCH

The switch statement can be used to check for equality against a list of values,
instead of multiple else if statements.
example

```c
if(position == 1) {
    printf("Gold");
} else if(position == 2) {
    printf("Silver");
} else if(position == 3) {
    printf("Bronze");
} else {
    printf("No medal");
}

switch(position) {
    case 1:
        printf("Gold");
    break;
    case 2:
        printf("Silver");
    break;
    case 3:
        printf("Bronze");
    break;
    default:
        printf("No medal");
}
```

The `break` statement is used to terminate the `switch`, when the `case` it matched.
If you forget to add the `break` after each `case`, the program will continue to execute the
code in the next `case` statements,
even if their value does not match the variable's value, resulting in a `fall=through` error.

```c
       //What is the value of x after this code?
                    int x = 2;
                    switch(x) {
                        case 1:
                            x = 4;
                        case 2:
                            x = 8;
                        case 3:
                            x = 7;
                        break;
                        case 4:
                            x = 3;
                    }
```

```c
       After executing the given code, the value of `x` would be 7.
       The switch statement evaluates the value of `x` and executes the corresponding
       case. In this case, `x` is initially assigned the value 2.
       The code inside the switch statement falls through each case because there are
       no explicit `break` statements after each case. This means that once a matching
       case is found, the code will continue executing the subsequent cases until a
       `break` statement is encountered.
       In this scenario, since `x` is equal to 2, the case `case 2:` is matched.
       The code then assigns `x` the value 8. It continues to execute the subsequent
       cases without any breaks.
       So, `x` is assigned the value 7 when it falls through to `case 3:`.
       However, since there is a `break` statement after `x = 7;`, the execution of the
       switch statement is terminated, and the final value of `x` is 7.
```

There is a default case at the end of the switch statement.
It is used to run code, when none of the cases match. No break is needed in the default
case, as it is always the last statement in the switch.

## COMBINING CONDITIONS

In some scenarios we need to combine multiple conditions. Let's say we want to check
that the age value is between 18 and 45.
This can be done using the `&&` operator:

```c
             if(age >= 18 && age <= 45) {
                  printf("OK");
             }
```

The `&&` operator is also referred to as the logical AND operator.

### OR

The logical OR operator, written as `||` combines conditions. The code will run if any one
of the conditions is satisfied.

```c
           if(balance > 1000 || level > 3) {
               printf("Gold Tier");
           }
```

### NOT

The logical NOT operator `!` reverses the condition.

```c
           if( !(age < 18) ) {
                printf("Adult");
           }
```

```c
             //What is the output of this code?

                       int x = 2;
                       int y = 8;
                       if(x>5 && y < 3) {
                          printf("A");
                       } else if (!(x>y || y > 10)) {
                          printf("B");
                       }

           //The output of the given code will be:
                          B
```

**_Let's break down the code:_**

1. `x` is assigned the value 2, and `y` is assigned the value 8.
2. The first condition `(x > 5 && y < 3)` evaluates to false because `x` is not greater
   than 5, and `y` is not less than 3.
3. The second condition `!(x > y || y > 10)` evaluates to true because `x` is not greater
   than `y` (2 is not greater than 8), and `y` is not greater than 10 (8 is not greater
   than 10).
4. Since the second condition is true, the code inside the corresponding `else if`
   statement is executed.
5. The `printf("B");` statement is executed, which outputs "B" to the console.
   Therefore, the output of the code will be "B".

### MULTIPLE CONDITIONS

You can chain multiple conditions using parentheses and the logical operators.

```c
                if(balance > 1000 || (level > 2 && type == 'V')) {
                            printf("Welcome");
                }
```

```c
        //Which of the following conditions will be satisfied if a = 5, b = 2?

                                1. (a>9 && b<4)
                                2. !(a>=5)
                                3. (a<b || b > 1)

          //Let's evaluate each of the conditions using the given values:

              1. `(a>9 && b<4)`:
                  Substituting `a = 5` and `b = 2`:
                  `(5 > 9 && 2 < 4)`:
                  This condition evaluates to `false && true`, which overall evaluates
                  to `false`.
                  Therefore, the condition `(a>9 && b<4)` is not satisfied.

              2. `!(a>=5)`:
                  Substituting `a = 5`:
                  `!(5 >= 5)`:
                  This condition evaluates to `!(true)`, which overall evaluates to
                  `false`.
                  Therefore, the condition `!(a>=5)` is not satisfied.

              3. `(a<b || b > 1)`:
                  Substituting `a = 5` and `b = 2`:
                  `(5 < 2 || 2 > 1)`:
                   This condition evaluates to `false || true`, which overall e   valuates
                   to `true`.
                   Therefore, the condition `(a<b || b > 1)` is satisfied.

         //To summarize, out of the three conditions given, only the condition `(a<b || b > 1)` is satisfied when `a = 5` and `b = 2`.
```

- `LOGICAL OPERATORS` allow you to combine multiple conditions.
  ▪ The AND operator `&&` combines two conditions.
  ▪The OR operator `||` check if any of the conditions hold.  
  ▪The NOT operator `!` reverses the condition.  
  ▪You can combine and chain conditions using parentheses and logical operators.

## BOOLEAN

Logic AND(&&) is true if and only if both operands are true, otherwise false.

```C
                    X                     Y
                    true                  true              true
                    true                  false             false
                    false                 true              false
                    false                 false             false
```

Logic OR(||) is true if and only if at least one operand is true, otherwise false.

```C
                    X                     Y
                    true                  true              true
                    true                  false             true
                    false                 true              true
                    false                 false             false
```

Logic NOT(!) inverts the value of its operand.

```C
                    X                     Y
                    true                  false
                    false                 true
```

## WHILE LOOP

The while loop takes a condition and repeats its statements while the condition is
satisfied.

```C
//For example:

                                          int num = 1;
                                          while (num < 5) {
                                             printf("%d \n", num);
                                             num = num + 1;
                                           }

//The output of the given code will be:

1
2
3
4
```

Let's break down the code:

1. `num` is initialized with a value of 1.
2. The `while` loop condition `num < 5` is evaluated. Since `num` is initially 1, which is
   less than 5, the condition is true, and the loop body is executed.
3. Inside the loop body, `printf("%d \n", num);` is executed, which prints the value of
   `num` followed by a newline character. In the first iteration, it will print `1`.
4. After that, `num` is incremented by 1 using the statement `num = num + 1;`, making
   `num` equal to 2.
5. The loop condition is checked again. Since `num` is now 2, which is still less than 5,
   the condition is true, and the loop body is executed again.
6. The value of `num` (2) is printed, resulting in `2` being output.
7. The process continues in this manner until `num` reaches 5. At that point, the loop
   condition `num < 5` becomes false, and the loop terminates.

Overall, the loop iterates four times, printing the values 1, 2, 3, and 4 on separate lines.
The statement num = num + 1 increases the value of num by 1 each time the loop runs.
This is important, as without it the loop would run forever.
The loop stops as soon as the value of num reaches the value 5.

```C
                       //How many numbers will the following loop output?

                                         int x = 3;
                                         while (x <= 6) {
                                           printf("%d \n", x);
                                           x = x + 2;
                                         }


                       //The loop will output two numbers: 3 and 5.
```

Let's break down the code:

- x is initialized with a value of 3.
- The while loop condition x <= 6 is evaluated. Since x is initially 3, which is less than
  or equal to 6, the condition is true, and the loop body is executed.
- Inside the loop body, printf("%d \n", x); is executed, which prints the value of x
  followed by a newline character. In the first iteration, it will print 3.
- After that, x is incremented by 2 using the statement x = x + 2;, making x equal to 5.
- The loop condition is checked again. Since x is now 5, which is still less than or equal
  to 6, the condition is true, and the loop body is executed again.
- The value of x (5) is printed, resulting in 5 being output.
- At this point, x is incremented by 2 again using x = x + 2;, making x equal to 7.
- The loop condition x <= 6 is checked again. Since x is now 7, which is greater than 6,
  the condition becomes false, and the loop terminates.
  Overall, the loop iterates twice, printing the values 3 and 5 on separate lines.

## INCREMENT

_`num=num+1` can be shortened to `num++`:_

```C
                         int num = 1;
                         while (num < 5) {
                            printf("%d \n", num);
                         num++;
                         }
```

## DECREMENT

`*num--` will decrease the value of `num by 1:`\*

```C
                         int num = 10;
                         while (num > 0) {
                            printf("%d \n", num);
                         num--;
                         }
//The output of the given code will be:

10
9
8
7
6
5
4
3
2
1
```

Let's break down the code:

1. `num` is initialized with a value of 10.
2. The `while` loop condition `num > 0` is evaluated. Since `num` is initially 10, which
   is greater than 0, the condition is true, and the loop body is executed.
3. Inside the loop body, `printf("%d \n", num);` is executed, which prints the value of
   `num` followed by a newline character. In the first iteration, it will print `10`.
4. After that, `num` is decremented by 1 using the statement `num--;`, making `num` equal
   to 9.
5. The loop condition is checked again. Since `num` is now 9, which is still greater than
   0, the condition is true, and the loop body is executed again.
6. The value of `num` (9) is printed, resulting in `9` being output.
7. The process continues in this manner, with `num` being decremented by 1 and printed in
   each iteration until `num` reaches 0.
8. At `num = 0`, the loop condition `num > 0` becomes false, and the loop terminates.

Overall, the loop iterates 10 times, printing the values 10, 9, 8, 7, 6, 5, 4, 3, 2,
and 1 on separate lines.

## SHORTHAND OPERATORS

Sometimes you might need to increase or decrease the value of a variable by a different
value than 1.
For these cases, C provides shorthand operators, too!
For example, `num=num+3` can be shortened to `num+=3`:

```C
                    int num = 0;
                    while (num < 10) {
                       printf("%d \n", num);
                       num += 3;
                    }
```

This will output only the numbers 0, 3, 6 and 9.

Similarly, there are shorthand operators for other mathematical operations,
such as `-=` for subtraction, `*=` for multiplication, etc.

```C
                      //What is the output of this code?

                                 int x = 2;
                                 int y = 5;
                                 x += 1;
                                 y -= x;
                                 y++;
                                   printf("%d", y);

                     //The output of the given code will be: 3
```

Let's break down the code:  
x is initialized with a value of 2.  
y is initialized with a value of 5.  
The statement x += 1; increments the value of x by 1.

After this statement, x becomes 3.  
The statement y -= x; subtracts the value of x from y.  
Since x is 3 and y is 5, y becomes
5 - 3, which is 2.  
The statement y++; increments the value of y by 1. After this statement, y becomes 3.  
The printf("%d", y); statement outputs the value of y, which is 3.

Therefore, the output of the code will be "3".

## DO WHILE

Another variation of the while loop is do-while.

```C
                   //Here is an example:

                         do {
                            printf("%d \n", num);
                            num += 3;
                         }
                        while (num < 10);

//The output of the given code will be:

0
3
6
9
```

Let's break down the code:

1. The code starts with an initialization of `num` with an unknown value.
2. The `do-while` loop is entered.
3. Inside the loop body, `printf("%d \n", num);` is executed, which prints the value of
   `num` followed by a newline character.
4. After printing the value of `num`, `num` is incremented by 3 using the statement
   `num += 3;`.
5. The loop condition `num < 10` is checked. If the condition is true, the loop body will
   execute again; otherwise, the loop will terminate.
6. Steps 3-5 are repeated until the loop condition becomes false.
7. The loop terminates when `num` becomes 9 because after incrementing `num` by 3, it
   will no longer be less than 10.
8. The loop body is executed four times with `num` taking the values 0, 3, 6, and 9.
9. These values are printed on separate lines.

Therefore, the output of the code will be "0", "3", "6", and "9", each on a separate line.
The difference with a while loop is that the condition is checked after the code,
meaning the code in the do is executed at least once, even if the condition is not
satisfied.

Also, note the semicolon after the while condition.

## FOR LOOPS

Another loop structure is the for loop. It has the following form:

```C
                  for(int i=1; i<10; i++) {
                          printf("%d \n", i);
                     }
```

This will output the numbers 1 to 9, each number on a new line.  
The for loop has 3 components in the parentheses:

▪The first part runs once when we enter the loop and initializes the variable.

▪The second part is the condition of the loop.

▪The third part runs every time the loop runs.

Note the semicolons between the components.

You can have any type of condition and any type of increment statements in the for loop.

For example, let's output the even numbers from 2 to 100:

```C
                    for(int i=2; i<=100; i+=2) {
                          printf("%d \n", i);
                       }
//The output of the given code will be all the even numbers from 2 to 100, inclusive.

//Here's the expected output:


2
4
6
8
...
98
100
```

Explanation:

1. The `for` loop is initialized with `int i = 2`, which sets the initial value of `i`
   to 2.
2. The loop condition is `i <= 100`, which means the loop will continue as long as `i`
   is less than or equal to 100.
3. After each iteration of the loop, `i` is incremented by 2 using the statement `i += 2`,
   which ensures that `i` will always be an even number.
4. Inside the loop body, `printf("%d \n", i);` is executed, which prints the value of
   `i` followed by a newline character.
5. The loop continues to execute until `i` reaches 102.
6. When `i` is 102, the loop condition `i <= 100` becomes false, and the loop terminates.

Remember the break; statement that was used in switch to stop it when a case was matched?
It can also be used to stop a loop.

```C
                                //For example:

                          for(int i=1; i<10; i++) {
                              if(i == 5) {
                                 break;
                          }
                          printf("%d \n", i);
                          }

//The output of the given code will be:


1
2
3
4
```

Explanation:

1. The `for` loop is initialized with `int i = 1`, which sets the initial value of `i`
   to 1.
2. The loop condition is `i < 10`, which means the loop will continue as long as `i` is
   less than 10.
3. After each iteration of the loop, `i` is incremented by 1 using the statement `i++`.
4. Inside the loop body, the conditional statement `if(i == 5)` is evaluated. When `i` is
   equal to 5, the condition becomes true.
5. In the `if` block, the `break` statement is encountered, which causes the loop to
   terminate immediately.
6. The `printf("%d \n", i);` statement is not executed when `i` is equal to 5 because
   the loop is terminated before reaching that point.
7. The loop only executes for values of `i` from 1 to 4.
8. Inside the loop body, the value of `i` is printed using `printf("%d \n", i);`,
   resulting in the output of 1, 2, 3, and 4 on separate lines.

Therefore, the code will output 1, 2, 3, and 4, each on a separate line, before
terminating due to the `break` statement when `i` is equal to 5.

## CONTINUE

The continue statement skips the current loop iteration and continues with the next one.

```C
                                  //For example:

                           for(int i=1; i<10; i++) {
                                 if(i == 5) {
                                 continue;
                            }
                               printf("%d \n", i);
                            }

/* This will skip the number 5 but will run until i reaches 10.
The output of the given code will be: */


1
2
3
4
6
7
8
9
```

Explanation:

1. The `for` loop is initialized with `int i = 1`, which sets the initial value of `i`
   to 1.
2. The loop condition is `i < 10`, which means the loop will continue as long as `i` is
   less than 10.
3. After each iteration of the loop, `i` is incremented by 1 using the statement `i++`.
4. Inside the loop body, the conditional statement `if(i == 5)` is evaluated. When `i`
   is equal to 5, the condition becomes true.
5. In the `if` block, the `continue` statement is encountered, which causes the loop to
   skip the remaining code in the loop body for the current iteration and move on to the
   next iteration.
6. The `printf("%d \n", i);` statement is not executed when `i` is equal to 5 because
   the `continue` statement causes the loop to skip to the next iteration.
7. The loop executes for values of `i` from 1 to 4 and from 6 to 9.
8. Inside the loop body, the value of `i` is printed using `printf("%d \n", i);`,
   resulting in the output of 1, 2, 3, 4, 6, 7, 8, and 9 on separate lines.

Therefore, the code will output 1, 2, 3, 4, 6, 7, 8, and 9, each on a separate line,
skipping the number 5 due to the `continue` statement.

```C
                   // How many numbers will the following loop output?

                               for(int x=3;x<10;x++) {
                                   if(x == 5) {
                                 continue;
                               }
                                   if(x == 7) {
                                 break;
                               }
                                  printf("%d \n", x);
                               }
// The loop will output the following numbers:
3
4
6
```

Explanation:

The loop starts with x = 3 and iterates until x is less than 10. Inside the loop:

If x is equal to 5, the continue statement is executed, which skips to the next iteration
without printing anything.  
If x is equal to 7, the break statement is executed, which terminates the loop altogether.  
Otherwise, the value of x is printed.  
Therefore, the loop outputs the numbers 3, 4, and 6.

## ARRAYS

Arrays allow to store multiple values in a single variable.
When creating an array, we need to provide the type of the items and the size of the
array, like this:

```C
                           int cart[12];
```

Array items are accessed using their indexes, placed in square brackets. The first item
has the index 0.
You can also create an array with values using the following syntax, initializing its
values:

```C
                         int nums[] = {1, 2, 3, 4};
```

```C
//Fill in the required symbols to create a char array, then output the 3rd item.

                             char letters[] = 'A', 'B', 'C', 'D' ;
                             printf("%c", letters[]);

//To create a char array and output the 3rd item, you would replace the blanks in the code as follows:

                            char letters[] = {'A', 'B', 'C', 'D'};
                            printf("%c", letters[2]);

//Explanation:

- The char array `letters` is created with the elements 'A', 'B', 'C', 'D'.
- The elements are enclosed within curly braces `{}` and separated by commas.
- To access the 3rd item (index 2) in the `letters` array, we use `letters[2]`.
- The `%c` format specifier is used to print a single character.

By substituting the blanks with the correct code, the updated code will create the char
array and output the value of the 3rd item in the `letters` array, which is 'C'.
```

We can use a loop to iterate over the items of an array.

For example, let's simply output all the items using a for loop:

```C
                          int ages[] = {31, 18, 24, 55, 29};
                                for(int i=0;i<5;i++) {
                          printf("%d \n", ages[i]);
                          }

//The output of the code you provided will be:

31
18
24
55
29
```

Here's a breakdown of how the code works:

Array initialization: You create an integer array named ages and initialize it with five
values: 31, 18, 24, 55, and 29.  
For loop setup: You initiate a for loop with three statements:  
`int i = 0;`: Declares and initializes an integer variable i to 0, which will act as the
loop counter.  
`i < 5;`: Sets the loop condition to continue as long as i is less than 5.  
`i++`: Increments i by 1 after each iteration of the loop.  
Loop body: Inside the loop, you execute the following statement:

`printf("%d \n", ages[i]);`: This line prints the element at index i of the ages array.

Since indexes start at 0, it will print the first element in the first iteration,
the second element in the second iteration, and so on. The \n at the end adds a newline
character after each printed number.  
As the loop iterates from 0 to 4, it prints the elements at corresponding indexes,
resulting in the output you see above.

We can also use loops to perform calculations with arrays.
For example, let's calculate the sum of all values of the ages array:

```C
                   int ages[] = {31, 18, 24, 55, 29};
                               int total = 0;

                       for(int i=0;i<5;i++) {
                              total += ages[i];
                    }
                    printf("Sum: %d", total);

//The given code will calculate the sum of the elements in the `ages` array and print it as follows:

Sum: 157
```

Explanation:

- The `ages` array is initialized with the values `{31, 18, 24, 55, 29}`.
- The variable `total` is declared and initialized to 0.
- The `for` loop is set up to iterate from `i = 0` to `i < 5`.
- In each iteration of the loop, the value of `ages[i]` is added to the `total` variable
  using the `+=` operator.
- After the loop completes, the `printf` statement is executed, printing the value of
  `total` preceded by the string "Sum: ".

Therefore, the output will display "Sum: 157", indicating that the sum of the elements in
the `ages` array is 157.

## MULTIDIMENSIONAL ARRAYS

To create multidimensional arrays, place each array within its own set of square brackets:

````C
                       int ages[2][4] = {{1, 2, 3, 4}, {5, 6, 7, 8}};

The array has two dimensions: 2 rows and 4 columns.

What is the output of this code?
```C
                       int nums[3][2] = { {1, 2}, {3, 4}, {5, 6} };
                        printf("%d", nums[1][0]);
````

Answer is 3 because {1, 2} is at index 0,  
{3, 4} at index 1 and  
{5, 6} at index 2.

Now we are ask to print nums[1] [0],  
index 1 already we know it's {3, 4}  
now we get index 0 of this index 1, which is 3.

We can loop over a two-dimensional array using nested for loops:

```C
                     int ages[2][4] = {
                         {1, 2, 3, 4},
                         {5, 6, 7, 8}
                       };

                     for(int i=0;i<2;i++) {
                     for(int j=0;j<4;j++) {
                        printf("%d ", ages[i][j]);
                     }
                     printf("\n");
                     }
```

The given code will output the following:

```C
1 2 3 4
5 6 7 8
```

Explanation:

- The `ages` array is a two-dimensional array with dimensions 2x4.
- It is initialized with the values `{ {1, 2, 3, 4}, {5, 6, 7, 8} }`.
- The outer `for` loop iterates over the rows of the `ages` array, with `i` ranging from
  0 to 1.
- The inner `for` loop iterates over the columns of the `ages` array, with `j` ranging
  from 0 to 3.
- Inside the nested loops, the `printf` statement prints the value of `ages[i][j]` using
  the `%d` format specifier.
- After printing each row of the `ages` array, the `printf("\n")` statement is executed
  to print a newline character, moving to the next line.

Therefore, the output will display the elements of the `ages` array, with each row
printed on a new line, as shown above.

## STRINGS

The format specifier for strings is `%s`:

```C
                 char name[] = "James";
                     int age = 42;
                 printf("%s is %d years old.", name, age);
```

In order to insert special characters into the string, we need to use the special \
escape character.
We have already seen it used for new lines \n.
We can also use it to insert, for example, a double quote into the string:

```C
           char txt[] = "The title says \"The Great Gatsby\".";

                   //the output will be:
             The title says "The Great Gatsby".
```

Here's an example of a valid code that takes a string input from the user and then
outputs it:

```C

               #include <stdio.h>
               int main() {
                   char word[20];
                   printf("Enter a word: ");
                   scanf("%19s", word);
                   printf("You entered: %s", word);

                   return 0;
               }
```

When you run this code, it will wait for the user to enter a word. After the user enters
the word and presses enter, it will be stored in the word array and then displayed as the
output with the "You entered: " prefix.

## STRING INPUT

In case we need to take multiple words as input, we can use the fgets() function.
Here is the syntax:

```C
                        fgets(name, 50, stdin);
```

It has 3 parts: the variable to store the input, the maximum size, and the stdin keyword,
which tells to take the input from the user.
The code `fgets(name, 50, stdin);` is using `fgets()` to read a line of input from the
user and store it in the `name` variable, with a maximum length of 49 characters
(leaving one space for the null-terminating character). The input is read from the
`stdin` stream, which represents the standard input.

Here's an example of how this code could be used in a complete program:

```C
                           #include <stdio.h>

                           int main() {
                               char name[50];
                               printf("Enter your name: ");
                               fgets(name, sizeof(name), stdin);
                               printf("Hello, %s", name);

                           return 0;
                           }
```

Explanation:

- The code includes the `<stdio.h>` header for the necessary declarations.
- The `main()` function serves as the entry point of the program.
- The `name` array is declared as a character array with a size of 50, allowing it to
  store a string of up to 49 characters (leaving one space for the null-terminating
  character).
- The `printf` function is used to prompt the user to enter their name.
- The `fgets` function is used to read a line of input from the user using the `stdin`
  stream. The input is stored in the `name` array, with a maximum length of `sizeof(name)`
  characters.
- The second `printf` statement is used to display a greeting message, including the name
  entered by the user.
- Finally, the `return 0` statement signifies the successful execution of the `main()`
  function.

When you run this code, it will wait for the user to enter their name. After the user
enters their name and presses enter, it will be stored in the `name` array and then
displayed as part of the greeting message.

Here is how you take a string from input:
▪The %s format specifier can be used to take a string as input using the scanf() function.
▪However, this method will only store the first word of the input, before the first space.
▪The fgets() function can be used to take a line of text, that contains spaces

## FUNCTIONS

The code below defines a function named `greeting` that prints two lines of text:

```C
                               void greeting() {
                                  printf("Hello! \n");
                                  printf("I am an example function.");
                               }
```

To use this function in a complete program, you would need to include a `main` function
and call the `greeting` function. Here's an example:

```C
                              #include <stdio.h>
                              void greeting() {
                                  printf("Hello! \n");
                                  printf("I am an example function.");
                              }
                              int main() {
                                   greeting();

                              return 0;
                              }
```

Explanation:

- The code includes the `<stdio.h>` header for the necessary declarations.
- The `greeting` function is defined with a `void` return type, indicating that it does
  not return a value.

- Inside the `greeting` function, there are two `printf` statements that print the lines
  "Hello!" and "I am an example function." respectively.
- The `main` function serves as the entry point of the program.
- Inside the `main` function, the `greeting` function is called using `greeting();`.
- Finally, the `return 0` statement signifies the successful execution of the `main`
  function.

When you run this program, it will call the `greeting` function, which will print the
two lines of text:

````C
                                  ```
                                 Hello!
                                 I am an example function.
                                  ```
````

Note: Make sure to include the necessary header files and compile the program correctly
for it to run successfully.
You can call a function multiple times.

```C
                               int main() {
                                 greeting();
                                 greeting();
                                 greeting();

                              return 0;
                              }
```

## FUNCTION PARAMETERS

Functions can have parameters, which they can use in their code.
The parameters are defined in the parentheses, and can be used like variables in the
function.

For example, let's add a string name parameter to our greeting() function:

```C
                       void greeting(char name[]) {
                          printf("Hello, %s!", name);
                       }
```

The function above takes a string called name as its parameter, which is used in the
function's output.
Reminder: a string is defined as a char array.
To use this function in a complete program, you would need to include a main function and
call the greeting function with a valid argument. Here's an example:

```C
                            #include <stdio.h>
                            void greeting(char name[]) {
                               printf("Hello, %s!", name);
                             }

                            int main() {
                            char myName[] = "John";
                                greeting(myName);

                            return 0;
                            }
```

Explanation:

The code includes the <stdio.h> header for the necessary declarations.
The greeting function is defined with a void return type and a parameter name which is a
character array.
Inside the greeting function, the printf statement is used to print the greeting message
"Hello, " followed by the provided name using the %s format specifier.
The main function serves as the entry point of the program.
Inside the main function, a character array myName is declared and initialized with the
name "John".
The greeting function is called with the myName array as an argument using
greeting(myName);.
Finally, the return 0 statement signifies the successful execution of the main function.
When you run this program, it will call the greeting function with the name "John" as an
argument, which will print the greeting message:

```C
                                Hello, John!

```

## MULTIPLE PARAMETERS

Functions can take multiple parameters. For that, we simply need to separate them using
commas, for example:

```C
                         void greeting(char name[], int age) {
                            printf("Hello, %s! \n", name);
                            printf("You are %d years old. \n\n", age);
                         }
```

Now, our greeting() function takes two parameters: one string and one integer.
Note, that we need to define the data type and name for each parameter.
To use this function in a complete program, you would need to include a
main function and call the greeting function with valid arguments. Here's an example:

```C
                         #include <stdio.h>
                         void greeting(char name[], int age) {
                            printf("Hello, %s! \n", name);
                            printf("You are %d years old. \n\n", age);
                         }

                         int main() {
                         char myName[] = "John";
                         int myAge = 25;

                         greeting(myName, myAge);

                         return 0;
                         }
```

Explanation:

The code includes the <stdio.h> header for the necessary declarations.
The greeting function is defined with a void return type and two parameters: name[],
which is a character array, and age, which is an integer.
Inside the greeting function, the first printf statement is used to print the greeting
message "Hello, " followed by the provided name using the %s format specifier.
The second printf statement is used to print the age using the %d format specifier.
The main function serves as the entry point of the program.
Inside the main function, a character array myName is declared and initialized with the
name "John", and an integer variable myAge is declared and initialized with the value 25.
The greeting function is called with the myName array and myAge variable as arguments
using greeting(myName, myAge);.
Finally, the return 0 statement signifies the successful execution of the main function.
When you run this program, it will call the greeting function with the name "John" and
age 25 as arguments, which will print the following output:

                         Hello, John!
                         You are 25 years old.

## MEMORY

Every variable in the memory has its unique address.
The address of a variable can be accessed using the & operator.
For example, let's create a sample variable, assign it a value, then output its memory
address:

```C
                   int age = 24;
                   printf("%p", &age);
```

The code above will output the memory address of the variable, which is a hexadeciimal.
Note, that the format specifier for hexadecimals is %p.
The code you provided declares an integer variable `age` and assigns it a value of `24`.
Then, it uses `printf` to print the memory address of the `age` variable using the `%p`
format specifier along with the `&` operator to get the address.
The output of the code will be the memory address of the `age` variable, which will be
displayed as a hexadecimal value. The specific address will depend on the system and
compiler you are using. Here's an example of the expected output:

```C
                    0x7ffeed09aabc
```

Note that the actual memory address displayed may vary from system to system, so the
output you see may differ.

## POINTERS

A pointer is a variable that stores the memory address of another variable as its value.
It is defined using the asterisk sign and is defined just like a variable:

```C
                       int age = 24;
                       int* p = &age;
                       printf("%p", p);
```

p is a pointer to an int variable, thats why it is declared as int\*, which reads as
"a pointer to an int".
p is assigned to the memory address of the age variable, so it holds that address as its
value.\*\*\*

_\*\*The asterisk _ is also used to access the value stored at a memory address.
It is called the dereference operator.
Let's output the value stored at the address to which the pointer p points:

```C
                      printf("%d", *p);
```

Note, that we used %d as the format specifier, as we are outputting the integer value,
stored at the address p.\*\*\*

Another thing we can accomplish using pointer parameters is to return multiple values
from a function.
As you remember, the return keyword was used to return a value from the function,
however it can only return a single value.

In case of pointer parameters, we can use any number of pointers and set their values
from the function.

```C
                          For example:

                   void divide(int* x, int* y, int by) {
                           *x /= by;
                           *y /= by;
                    }
```

The function takes two pointers and another integer, then divides the two pointer values
by the integer value.
This way, two values are changed by the function.
Note, that the function accesses the values of the pointers using the \* operator.
To use this function, you can pass the addresses of the variables you want to divide.
Here's an example of how you can call the divide function:

```C
                     #include <stdio.h>
                     void divide(int* x, int* y, int by) {
                        *x /= by;
                        *y /= by;
                     }

                    int main() {
                     int a = 10;
                     int b = 20;
                     int divisor = 2;

                   printf("Before division: a = %d, b = %d\n", a, b);

                     divide(&a, &b, divisor);

                   printf("After division: a = %d, b = %d\n", a, b);

                   return 0;
                   }
```

In this example, the main function declares two integer variables a and b and initializes
them with values of 10 and 20, respectively. It also declares an integer variable divisor
with a value of 2 that will be used as the divisor in the divide function.
The printf statement before the division prints the initial values of a and b. Then, the
divide function is called with the addresses of a and b as arguments, along with the
divisor.
After the division, the printf statement after the division is used to print the updated
values of a and b.

When you run this code, it will output:

```C
                      Before division: a = 10, b = 20
                      After division: a = 5, b = 10
```

What is the output of this code?

```C
                      void change(int *x, int y) {
                         *x = y;
                          y = *x;
                      }
                      int main() {
                        int a = 8;
                        int b = 3;
                     change(&b, a);
                     printf("%d", b);

                     return 0;
                     }
```

The code provided defines a function named `change` that takes an integer pointer `x` and
an integer `y` as parameters. Inside the function, it assigns the value of `y` to the
memory location pointed to by `x` using the dereference operator `*`.
It also assigns the value of the memory location pointed to by `x` to `y`.

In the `main` function, two integer variables `a` and `b` are declared and initialized
with values `8` and `3`, respectively. Then, the `change` function is called with the
address of `b` and the value of `a` as arguments. Finally, the value of `b` is printed
using `printf`.

Let's analyze the code step by step:

1. `int a = 8;` declares and initializes `a` with a value of `8`.
2. `int b = 3;` declares and initializes `b` with a value of `3`.
3. `change(&b, a);` calls the `change` function with the address of `b` and the value of
   `a` as arguments.
4. Inside the `change` function, `*x = y;` assigns the value of `y` (which is `8`) to the
   memory location pointed to by `x`, which is the address of `b`. So, `*x` (which is `b`)
   is updated to `8`.
5. `y = *x;` assigns the value of the memory location pointed to by `x` (which is `8`)
   to `y`. However, this assignment does not affect the value of `b` in the `main` function,
   as `y` is a local variable within the `change` function.
6. `printf("%d", b);` prints the value of `b` using `printf`. Since the value of `b` was
   updated to `8` inside the `change` function, the output will be `8`.

Therefore, the output of the code will be:

```C
                                  8
```

Another use-case of pointers are arrays.

The name of an array is actually a pointer to its first element.
For example:

```C
               int x[] = {1, 2, 3, 4};
                 printf("%d", *x);
```

This will output the value of the first element of the array.
Array values are stored continuously in memory.
Thus, each next element can be accessed by incrementing the pointer:

```C
                 int* p = x;
                  for(int i=0;i<4;i++) {
                   printf("%d \n", *p);
                  p++;
                  }
```

During each loop iteration, we increment the memory address of the pointer by 1, using
p++.This sets the pointer to the next element of the array.
This allows to easily access any array element.
