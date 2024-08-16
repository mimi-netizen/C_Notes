## STRUCTURES

A structure is a user-defined data type that groups related variables of different data
types.
A structure declaration includes the keyword struct, a structure tag for referencing the
structure, and curly braces { } with a list of variable declarations called members.

```c
                                 For example:

                              struct course {
                                 int id;
                                 char title[40];
                                 float hours;
                              };


This struct statement defines a new data type named course that has three members.
Structure members can be of any data type, including basic types, strings, arrays,
pointers, and even other structures, as you will learn in a later lesson.
Do not forget to put a semicolon after structure declaration.
A structure is also called a composite or aggregate data type. Some languages refer to
structures as records.

To declare variables of a structure data type, you use the keyword struct followed by the
struct tag, and then the variable name.
For example, the statements below declares a structure data type and then uses the student
struct to declare variables s1 and s2:

                                struct student {
                                  int age;
                                  int grade;
                                  char name[40];
                                };

                           /* declare two variables */
                                struct student s1;
                                struct student s2;

A struct variable is stored in a contiguous block of memory. The sizeof operator must be
used to get the number of bytes needed for a struct, just as with the basic data types.
Here's an example of how you can use these variables to store and access data:


                              #include <stdio.h>
                              struct student {
                                int age;
                                int grade;
                                char name[40];
                              };

                              int main() {
                                struct student s1;
                                struct student s2;

                                s1.age = 18;
                                s1.grade = 12;
                             strcpy(s1.name, "John");

                                s2.age = 17;
                                s2.grade = 11;
                            strcpy(s2.name, "Jane");

                            printf("Student 1: Age = %d, Grade = %d, Name = %s\n", s1.age,
                                   s1.grade, s1.name);
                            printf("Student 2: Age = %d, Grade = %d, Name = %s\n", s2.age,
                                   s2.grade, s2.name);

                            return 0;
                            }
In this example, we assign values to the members of s1 and s2 using the dot (.) operator.
We then use printf to display the values stored in each structure variable.
Note that we include the <string.h> header to use the strcpy function for copying the
name string into the name member of each structure variable.

Output:

                           Student 1: Age = 18, Grade = 12, Name = John
                           Student 2: Age = 17, Grade = 11, Name = Jane

This demonstrates how to declare variables of a structure type and access their members
to store and retrieve data.


A struct variable can also be initialized in the declaration by listing initial values in
order inside curly braces:

                     struct student s1 = {19, 9, "John"};
                     struct student s2 = {22, 10, "Batman"};

If you want to initialize a structure using curly braces after declaration, you will also
need to type cast, as in the statements:

                      struct student s1;
                      s1 = (struct student) {19, 9, "John"};

You can use named member initialization when initializing a structure to initialize
corresponding members:

                   struct student s1
                  = { .grade = 9, .age = 19, .name = "John"};

In the example above, .grade refers to the grade member of the structure.
Similarly, .age and .name refer to the age and name members.

Example two:
                         #include <stdio.h>
                          struct student {
                            int age;
                            int grade;
                            char name[40];
                          };

                          int main() {
                            struct student s1;

                            s1 = (struct student) {
                               .grade = 9,
                               .name = "John Birghimer",
                               .age = 19
                            };

                        printf("Name: %s, Age: %d, Grade: %d\n", s1.name, s1.age,
                                s1.grade);
                        printf("%s will turn %d in 2 years time\n", s1.name, s1.age + 2);

                        return 0;
                        }
Output:

                      Name: John Birghimer, Age: 19, Grade: 9
                      John Birghimer will turn 21 in 2 years time

In this code, the structure s1 is initialized with the provided values using the compound
literal syntax. The printf statements then display the values of the name, age, and grade
members of the s1 structure.
Additionally, the second printf statement shows an example of performing arithmetic using
the values of the structure members.

**** char name[40] is a member of the struct student structure. It represents a character
array of size 40, which can store up to 39 characters plus a null terminator ('\0')
character.
In C, character arrays are used to store strings. By declaring char name[40], you are
allocating memory for a string of up to 39 characters (plus one for the null terminator).
This allows you to store a name or any other sequence of characters up to the specified
size.
In the above code, the name member of the struct student is initialized with the value
"John Birghimer", which is a string literal. The string literal is automatically
null-terminated by the compiler, so it occupies exactly 14 characters (including the null
terminator) in memory.
By declaring char name[40], you allow the name member to hold strings of up to 39
characters in length, providing some buffer space for potential future modifications or
longer names.****
```

## STRING.H FUNCTIONS

```c

In C, there are several functions available in the `<string.h>` header that can be used
to manipulate strings. Here are some commonly used functions:

1. `strlen`: Calculates the length of a string.


   size_t strlen(const char* str);


2. `strcpy`: Copies a string from one location to another.


   char* strcpy(char* dest, const char* src);


3. `strcat`: Concatenates two strings, appending the contents of the second string to the
    first.


   char* strcat(char* dest, const char* src);


4. `strcmp`: Compares two strings lexicographically.


   int strcmp(const char* str1, const char* str2);


5. `strchr`: Searches for the first occurrence of a character in a string.


   char* strchr(const char* str, int c);


6. `strstr`: Searches for the first occurrence of a substring in a string.


   char* strstr(const char* haystack, const char* needle);


7. `strncpy`: Copies a specified number of characters from one string to another.


   char* strncpy(char* dest, const char* src, size_t n);


8. `strncat`: Concatenates a specified number of characters from the source string to the
    destination string.


   char* strncat(char* dest, const char* src, size_t n);


9. `strncmp`: Compares a specified number of characters between two strings.


   int strncmp(const char* str1, const char* str2, size_t n);


These are just a few examples of functions available for string manipulation in C.
There are additional functions and variations that provide different functionalities.
It's recommended to refer to the C standard library documentation for a comprehensive
list of string manipulation functions and their usage.
```

## STRCPY

```c

                                 #include <stdio.h>
                                 #include <string.h>

                                 struct course {
                                   int id;
                                   char title[40];
                                   float hours;
                                 };

                                 int main() {
                                   struct course cs1 = {341279, "Intro to C++", 12.5};
                                   struct course cs2;

                                   /* initialize cs2 */
                                   cs2.id = 341281;
                                   strcpy(cs2.title, "Advanced C++");
                                   cs2.hours = 14.25;

                                    /* display course info */
                                    printf("%d\t%s\t%4.2f\n", cs1.id, cs1.title,
                                            cs1.hours);
                                    printf("%d\t%s\t%4.2f\n", cs2.id, cs2.title,
                                            cs2.hours);

                                     return 0;
                                    }
In this code, you include the necessary headers <stdio.h> and <string.h>.
You then define a structure named course, which has three members: id (of type int),
title (a character array of size 40), and hours (of type float).
In the main() function, you declare two variables of type struct course: cs1 and cs2.
For cs1, you initialize its members using an initializer list: {341279, "Intro to C++",
12.5}. This assigns the values 341279 to cs1.id, "Intro to C++" to cs1.title, and 12.5 to
cs1.hours.
For cs2, you initialize its members individually. First, you assign 341281 to cs2.id
using the assignment operator (=). Then, you use strcpy() from <string.h> to copy the
string "Advanced C++" into cs2.title. Finally, you assign 14.25 to cs2.hours.
After initializing the structures, you use printf() to display the course information
stored in the cs1 and cs2 variables.
The output will be:

                              341279   Intro to C++    12.50
                              341281   Advanced C++    14.25

This code demonstrates how to declare and initialize structure variables and access their
members to display the stored information.

The `strcpy` function in C is used to copy a string from one character array to another.
It stands for "string copy." It is defined in the `<string.h>` header.

The function signature of `strcpy` is as follows:


                   char* strcpy(char* destination, const char* source);



The `strcpy` function takes two arguments:
- `destination`: A pointer to the destination character array where the string will be
   copied.
- `source`: A pointer to the source string that will be copied.

The `strcpy` function copies the characters from the source string to the destination
character array until it encounters a null terminator (`'\0'`) in the source string.
It then adds a null terminator at the end of the destination string to mark the end of
the copied string.

Here's an example usage of `strcpy`:

                             #include <stdio.h>
                             #include <string.h>

                             int main() {
                               char source[] = "Hello, World!";
                               char destination[20];

                               strcpy(destination, source);

                               printf("Source: %s\n", source);
                               printf("Destination: %s\n", destination);

                               return 0;
                            }

In this example, the `source` character array contains the string "Hello, World!".
The `destination` character array is initially empty.
The `strcpy(destination, source)` statement copies the contents of the `source` array
into the `destination` array. After the `strcpy` call, both `source` and `destination`
will contain the same string.

The output of this code will be:

                                  Source: Hello, World!
                                  Destination: Hello, World!

Note that it is essential to ensure that the destination character array has enough space
to accommodate the copied string, including the null terminator. Otherwise, a buffer
overflow may occur, leading to undefined behavior.
```

## TYPEDEF

The typedef keyword creates a type definition that simplifies code and makes a program
easier to read.
typedef is commonly used with structures because it eliminates the need to use the keyword
struct when declaring variables.

```c
For example:

                             typedef struct {
                                  int id;
                                  char title[40];
                                  float hours;
                            } course;

                              course cs1;
                              course cs2;

Note that a structure tag is no longer used, instead a typedef name appears before the
struct declaration.
Now the word struct is no longer required in variable declarations, making the code
cleaner and easier to read.

                        #include <stdio.h>
                        #include <string.h>

                        typedef struct {
                          int id;
                          char title[40];
                          float hours;
                       } course;

                       int main() {
                          course cs1;
                          course cs2;

                          cs1.id = 123456;
                          strcpy(cs1.title, "JavaScript Basics");
                          cs1.hours = 12.30;

                          /* initialize cs2 */
                          cs2.id = 341281;
                          strcpy(cs2.title, "Advanced C++");
                          cs2.hours = 14.25;

                          /* display course info */
                          printf("%d\t%s\t%4.2f\n", cs1.id, cs1.title, cs1.hours);
                          printf("%d\t%s\t%4.2f\n", cs2.id, cs2.title, cs2.hours);

                          return 0;
                        }

In the code, we included the necessary headers <stdio.h> and <string.h>.
We then defined a typedef for a structure named course inline using the typedef keyword.
This allows ud to use course as a type name for the structure, without explicitly
including the struct keyword every time.

The course structure has three members: id (of type int),
                                        title (a character array of size 40)
                                        hours (of type float).

In the main() function, we declared two variables of type course: cs1 and cs2.
then initialized the members of cs1 and cs2 individually using assignment statements (=)
and strcpy() to copy the string values.
After initializing the structures, we used printf() to display the course information
stored in the cs1 and cs2 variables.

The output will be:

                           123456  JavaScript Basics   12.30
                           341281  Advanced C++        14.25

This code demonstrates how to define and use a typedef for a structure, initialize
structure variables, and access their members to display the stored information.
```

## STRUCTURES WITH STRUCTURES

The members of a structure may also be structures.
For example, consider the following statements:

```c
                           typedef struct {
                             int x;
                             int y;
                           } point;

                           typedef struct {
                             float radius;
                             point center;
                           } circle;

Nested curly braces are used to initialize members that are structs.
The dot operator is used twice to access members of members, as in the statements:

                       circle c = {4.5, {1, 3}};
                  printf("%3.1f %d,%d", c.radius, c.center.x, c.center.y);
                  /* 4.5  1,3 */

A struct definition must appear before it can be used inside another struct.
                           #include <stdio.h>

                           typedef struct {
                             int x;
                             int y;
                           } point;

                           typedef struct {
                             float radius;
                             point center;
                           } circle;

                          int main() {
                             point p;
                             p.x = 3;
                             p.y = 4;

                             circle c;
                             c.radius = 3.14;
                             c.center = p;

                       printf("Circle radius is %.2f, center is at (%d, %d)",
                               c.radius, c.center.x, c.center.y);

                       return 0;
                       }
In this code, you include the necessary header <stdio.h>.
You then define two typedef structures: point and circle.
The point structure has two members: x and y, both of type int.
The circle structure has two members: radius (of type float) and center (of type point).
The center member is an instance of the point structure, representing the center
coordinates of the circle.
In the main() function, you declare a variable p of type point and initialize its x and y
members with the values 3 and 4, respectively.
You also declare a variable c of type circle and initialize its radius member with the
value 3.14. You then assign the p variable to the center member of c, effectively copying
the values of p into c.center.
Finally, you use printf() to display the information about the circle.
The printf() statement uses format specifiers to print the values of c.radius, c.center.x,
and c.center.y.

The output will be:

                      Circle radius is 3.14, center is at (3, 4)

This code demonstrates how to define nested structures, initialize structure variables
with nested structure members, and access the nested structure members to display the
stored information.

Just like pointers to variables, pointers to structures can also be defined.

✔struct myStruct *struct_ptr;
  defines a pointer to the myStruct structure.

✔struct_ptr = &struct_var;
  stores the address of the structure variable struct_var in the pointer struct_ptr.

✔struct_ptr -> struct_mem;
  accesses the value of the structure member struct_mem.

For example:

                        struct student{
                          char name[50];
                          int number;
                          int age;
                       };

                      // Struct pointer as a function parameter
                      void showStudentData(struct student *st) {
                      printf("\nStudent:\n");
                      printf("Name: %s\n", st->name);
                      printf("Number: %d\n", st->number);
                      printf("Age: %d\n", st->age);
                      }

                     struct student st1 = {"Krishna", 5, 21};
                     showStudentData(&st1);

The -> operator allows to access members of the struct though the pointer.
(*st).age is the same as st->age.

Also, when a typedef has been used to name the struct, then a pointer is declared using
only the typedef name along with * and the pointer name.
The code above provided declares a structure named `student` with three members: `name`,
`number`, and `age`. It also defines a function named `showStudentData` that takes a
pointer to a `struct student` as a parameter and prints the data stored in the structure.
To call the `showStudentData` function and pass the address of the `st1` variable, you can
use the following code:

                           #include <stdio.h>
                           struct student {
                             char name[50];
                             int number;
                             int age;
                          };

                          void showStudentData(struct student *st) {
                             printf("\nStudent:\n");
                             printf("Name: %s\n", st->name);
                             printf("Number: %d\n", st->number);
                             printf("Age: %d\n", st->age);
                          }

                          int main() {
                            struct student st1 = {"Krishna", 5, 21};
                            showStudentData(&st1);
                            return 0;
                         }

In this code, you include the necessary header `<stdio.h>`.
The `student` structure is defined with three members: `name` (a character array of size 50)
, `number` (of type `int`), and `age` (also of type `int`).
The `showStudentData` function is defined to take a pointer to a `struct student` as a
parameter. Inside the function, it prints the data stored in the structure using the
`printf` function along with the arrow operator (`->`) to access the structure members
through the pointer.
In the `main` function, you declare a variable `st1` of type `struct student` and
initialize its members with the values `"Krishna"`, `5`, and `21`.
Finally, you call the `showStudentData` function and pass the address of the `st1` variable
using the address-of operator (`&`).

The output will be:

                        Student:
                        Name: Krishna
                        Number: 5
                        Age: 21

This code demonstrates how to define a structure, pass a structure pointer as a function
parameter, and access the structure members through the pointer.

                                  ▪✔🌧🗨🗯😂😅👩‍💻👩🆙

In the above code, the use of `void` in the function declaration `void
showStudentData(struct student *st)` indicates that the function does not return a value.
The `void` keyword is used as the return type of a function to indicate that the function
doesn't return any value. In other words, it signifies that the function is a "void"
function, which means it performs a specific action or task but doesn't produce a result
that needs to be returned.
In the case of the `showStudentData` function, it is responsible for displaying the data
of a student structure passed as a parameter. It doesn't need to return any value back to
the caller, so the return type is specified as `void`.
By using `void` as the return type, you're informing the compiler and other programmers
that the `showStudentData` function doesn't produce a result that needs to be captured or
used in any way. Its purpose is solely to display the student data, and the execution will
continue without expecting a return value from that function.

                                  ▪✔🌧🗨🗯😂😅👩‍💻👩🆙

To declare a pointer to a structure and access the structure members using the pointer,
you can use the following code:

                                    struct Point {
                                      int x;
                                      int y;
                                    };

                                    struct Point p1;
                                    struct Point *ptr = &p1;
                                    ptr->x = 3;
                                    ptr->y = 4;

In this code, a structure named Point is defined with two members: x and y, both of type
int.
A variable p1 of type struct Point is declared, which represents an instance of the
structure.
A pointer ptr of type struct Point* is declared, which is initialized with the address of
p1 using the address-of operator (&).
*ptr is where we store the address of p1. The address of p1 is obtained using &p1.
Addresses in memory are normally hexadecimal numbers (eg: 0x13a4) and that's the address
where the pointer *ptr points to.
To access the structure members using the pointer, the arrow operator (->) is used. For
example, ptr->x refers to the x member of the structure pointed to by ptr, and ptr->y
refers to the y member of the same structure.
Therefore, the code ptr->x = 3; sets the value of x to 3, and ptr->y = 4; sets the value of
y to 4.
Note that the -> operator is used specifically with pointers to structures to access their
members, while the dot operator (.) is used with actual structure variables.
Make sure to appropriately name your variables and ensure that the semicolon (;) is placed
after each statement.

```

## STRUCTURES AS FUNCTION PARAMETERS

A function can have structure parameters that accept arguments by value when a copy of the
structure variable is all that is needed.
For a function to change the actual values in a struct variable, pointer parameters are
required.

```c
For example:

                               #include <stdio.h>
                               #include <string.h>

                               typedef struct {
                                 int id;
                                 char title[40];
                                 float hours;
                               } course;

                              void update_course(course *class);
                              void display_course(course class);

                              int main() {
                                 course cs2;
                                 update_course(&cs2);
                                 display_course(cs2);
                                 return 0;
                              }

                             void update_course(course *class) {
                                 strcpy(class->title, "C++ Fundamentals");
                                 class->id = 111;
                                 class->hours = 12.30;
                             }

                            void display_course(course class) {
                                 printf("%d\t%s\t%3.2f\n", class.id, class.title,
                                         class.hours);
                            }

As you can see, update_course() takes a pointer as the parameter, while display_course()
takes the structure by value.
The course structure is defined with three members: id (of type int)
                                                    title (a character array of size 40)
                                                    hours (of type float)

The update_course function is declared and defined to take a pointer to a course structure
as a parameter (course *class). Inside the function, it uses strcpy from <string.h> to copy
the string "C++ Fundamentals" to the title member of the structure pointed to by class. It
also assigns values directly to the id and hours members using the -> operator.

The display_course function is declared and defined to take a course structure as a
parameter (course class). Inside the function, it uses printf to display the values of the
id, title, and hours members of the class structure.

In the main function, a course variable named cs2 is declared. The update_course function
is called with the address of cs2 (&cs2) passed as an argument to update its values. Then,
the display_course function is called with cs2 passed as an argument to display its
information.

The output will be:

                                111     C++ Fundamentals        12.30

This code demonstrates how to define a structure, use pointers to modify the structure
members, and pass structures (by value) as function parameters.
```

## UNIONS

A union allows to store different data types in the same memory location.
It is like a structure because it has members. However, a union variable uses the same
memory location for all its member's and only one member at a time can occupy the memory
location.
A union declaration uses the keyword union, a union tag, and curly braces { } with a list
of members.
Union members can be of any data type, including basic types, strings, arrays, pointers,
and structures.

```c
For example:

                                     union val {
                                     int int_num;
                                     float fl_num;
                                     char str[20];
                                     };

After declaring a union, you can declare union variables. You can even assign one union to
another of the same type:

                                    union val u1;
                                    union val u2;
                                    u2 = u1;

Unions are used for memory management. The largest member data type is used to determine
the size of the memory to share and then all members use this one location. This process
also helps limit memory fragmentation. Memory management is discussed in a later lesson.

The code you provided declares a union named `val` with three members: `int_num` of type
`int`, `fl_num` of type `float`, and `str` of type `char` array with a size of 20.
A union in C is a special data type that can hold different types of data, but only one
member can be accessed at a time. The size of a union is determined by the size of its
largest member.

Here's an example demonstrating the usage of the `val` union:

                                 #include <stdio.h>

                                 union val {
                                  int int_num;
                                  float fl_num;
                                  char str[20];
                                 };

                                 int main() {
                                 union val data;

                                 data.int_num = 42;
                                 printf("int_num: %d\n", data.int_num);

                                 data.fl_num = 3.14;
                                 printf("fl_num: %f\n", data.fl_num);

                                 strcpy(data.str, "Hello, world!");
                                 printf("str: %s\n", data.str);

                                 return 0;
                                 }

In the example above, we declare a variable `data` of type `union val`. We can access and
modify each member of the union interchangeably, but only one member should be accessed at
a time.
In the `main` function, we assign a value to `int_num`, print it out, then assign a value
to `fl_num` and print it out as well. Finally, we use `strcpy` from `<string.h>` to assign
a string to `str` and print it out.
Since all the members `int_num`, `fl_num`, and `str` share the same memory location within
the union, modifying one member will affect the other members. It is crucial to keep track
of which member is currently being used to avoid unexpected behavior and data corruption.

Note: When using unions, it's important to ensure proper typecasting and avoid accessing
members that were not assigned a value.
```

## ACCESSING UNION MEMBERS

You access the members of a union variable by using the . dot operator between the variable
name and the member name.
When assignment is performed, the union memory location will be used for that member until
another member assignment is performed.
Trying to access a member that isn't occupying the memory location gives unexpected results.
The following program demonstrates accessing union members:

```c
                                  #include <stdio.h>
                                  #include <string.h>

                                  union val {
                                     int int_num;
                                     float fl_num;
                                     char str[20];
                                  };

                                  int main() {
                                  union val test;

                                  test.int_num = 123;
                                  test.fl_num = 98.76;
                                  strcpy(test.str, "hello");

                                  printf("%d\n", test.int_num);
                                  printf("%f\n", test.fl_num);
                                  printf("%s\n", test.str);

                                  return 0;
                                  }

The last assignment overrides previous assignments, which is why str stores a value and
accessing int_num and fl_num is meaningless.
In this code, the union val is declared with the members int_num, fl_num, and str as you
provided.
Inside the main function, a union variable test of type val is declared. The code then
assigns different values to its members: 123 to int_num, 98.76 to fl_num, and "hello" to
str using strcpy from <string.h>.
Finally, the code prints the values of the members using printf. %d is used to print
int_num, %f is used to print fl_num, and %s is used to print str.

The output of the code will be:

                                       123
                                       98.760002
                                       hello

Note that the output of fl_num might have additional decimal places due to floating-point
precision.
```

## STRUCTURES WITH UNIONS

Unions are often used within structures because a structure can have a member to keep track
of which union member stores a value.
For example, in the following program, a vehicle struct uses either a vehicle identification
number (VIN) or an assigned id, but not both:

```c
                               typedef struct {
                                 char make[20];
                                 int model_year;
                                 int id_type; /* 0 for id_num, 1 for VIN */
                               union {
                                 int id_num;
                                 char VIN[20];
                                   } id;
                               } vehicle;

                               vehicle car1;
                               strcpy(car1.make, "Ford");
                               car1.model_year = 2017;
                               car1.id_type = 0;
                               car1.id.id_num = 123098;

Note that the union was declared inside the structure. When doing this, a union name was
required at the end of the declaration.
A union with a union tag could have been declared outside the structure, but with such a
specific use, the union within the struct provides easier to understand the code.

Note also the dot operator is used twice to access union members of struct members.

The id_type keeps track of which union member stores a value. The following statements
display car1 data, using the id_type to determine which union member to read:

                              /* display vehicle data */
                              printf("Make: %s\n", car1.make);
                              printf("Model Year: %d\n", car1.model_year);
                              if (car1.id_type == 0)
                                printf("ID: %d\n", car1.id.id_num);
                              else
                              printf("ID: %s\n", car1.id.VIN);

A union can also contain a structure.
The code you provided demonstrates the usage of a struct named `vehicle` with members `make`,
 `model_year`, `id_type`, and a union named `id` inside it.

Here's the code with the appropriate formatting:

                             #include <stdio.h>
                             #include <string.h>

                             typedef struct {
                               char make[20];
                               int model_year;
                               int id_type; /* 0 for id_num, 1 for VIN */
                            union {
                               int id_num;
                               char VIN[20];
                               } id;
                            } vehicle;

                           int main() {
                              vehicle car1;

                              strcpy(car1.make, "Ford");
                              car1.model_year = 2017;
                              car1.id_type = 0;
                              car1.id.id_num = 123098;

                              printf("Make: %s\n", car1.make);
                              printf("Model Year: %d\n", car1.model_year);

                             if (car1.id_type == 0)
                               printf("ID: %d\n", car1.id.id_num);
                             else
                               printf("ID: %s\n", car1.id.VIN);

                             return 0;
                           }

In this code, a struct named `vehicle` is defined with the members `make`, `model_year`,
`id_type`, and a union named `id`. The union `id` has two members: `id_num` of type `int`
and `VIN` of type `char` array with a size of 20.
Inside the `main` function, a variable `car1` of type `vehicle` is declared. The code then
assigns values to its members using `strcpy` for `make`, direct assignment for `model_year`,
and `id_type`. It also assigns a value to `id_num` using `car1.id.id_num = 123098`.
Finally, the code uses `printf` to print the values of the members. It checks the value of
`id_type` and prints either `id_num` or `VIN` depending on the condition.

The output of the code will be:


                         Make: Ford
                         Model Year: 2017
                         ID: 123098



This output demonstrates how to access and print the members of the `vehicle` struct, including
the union member `id` based on the value of `id_type`.
```

## POINTERS TO UNIONS

A pointer to a union points to the memory location allocated to the union.
A union pointer is declared by using the keyword union and the union tag along with \* and the
pointer name.

```c
For example, consider the following statements:

                      #include <stdio.h>

                      union val {
                        int int_num;
                        float fl_num;
                        char str[20];
                      };

                     int main() {
                       union val info;
                       union val *ptr = NULL;
                       ptr = &info;

                       ptr->int_num = 10;
                       printf("info.int_num is %d\n", info.int_num);

                       return 0;
                     }
When you want to access the union members through a pointer, the -> operator is required.
(*ptr).int_num is the same as ptr->int_num.

In this code, the union val is declared with the members int_num, fl_num, and str as you
provided.
Inside the main function, a union variable info and a pointer to the union ptr are declared. The
ptr is assigned the address of info using ptr = &info.
The code then assigns the value 10 to int_num using the pointer ptr and the arrow operator (->).
This is equivalent to (*ptr).int_num = 10 but provides a more convenient syntax.
Finally, the code uses printf to print the value of info.int_num.

The output of the code will be:

                    info.int_num is 10

This output demonstrates how to declare a union, assign a value to one of its members using a
pointer, and print the value of the member.
```

## UNION AS FUNCTION PARAMETERS

A function can have union parameters that accept arguments by value when a copy of the union
variable is all that is needed.
For a function to change the actual value in a union memory location, pointer parameters are
required.

```c
For example:

                                  #include <stdio.h>

                                  union id {
                                    int id_num;
                                    char name[20];
                                  };

                                  void set_id(union id *item) {
                                    item->id_num = 42;
                                  }

                                  void show_id(union id item) {
                                     printf("ID is %d\n", item.id_num);
                                  }

                                 int main() {
                                    union id my_id;

                                    set_id(&my_id);
                                    show_id(my_id);

                                    return 0;
                                  }

In this code, the union id is declared with the members id_num and name as provided.
The set_id function takes a pointer to a union item as an argument and sets the value of the
id_num member to 42 using the arrow operator (->).
The show_id function takes a union item as an argument and prints the value of the id_num member
using printf.
Inside the main function, a union variable my_id is declared. The set_id function is called with
a pointer to my_id using &my_id to set the value of id_num to 42. The show_id function is then
called with my_id to print the value of id_num.

The output of the code will be:

                                    ID is 42

This output demonstrates how to declare a union, pass a pointer to the union to a function,
modify the value of a member through the pointer, and print the value of a member of the union.
```

## ARRAY OF UNIONS

An array can store elements of any data type, including unions.
With unions, it is important to keep in mind that only one member of the union can store data
for each array element.
After declaring an array of unions, an element is accessible with the index number. The dot
operator is then used to access members of the union, as in the program:

```c
                    #include <stdio.h>

                    union val {
                      int int_num;
                      float fl_num;
                      char str[20];
                    };

                    int main() {
                     union val nums[10];
                     int k;

                     for (k = 0; k < 10; k++) {
                     nums[k].int_num = k;
                   }

                   for (k = 0; k < 10; k++) {
                     printf("%d  ", nums[k].int_num);
                   }

                  return 0;
                  }

In this code, the union val is declared with the members int_num, fl_num, and str provided.
Inside the main function, an array of unions nums with a size of 10 and an integer variable k
are declared.
The first for loop iterates from k = 0 to k < 10. Inside the loop, the int_num member of each
union in the nums array is assigned the value of k.
The second for loop also iterates from k = 0 to k < 10. Inside the loop, the code uses printf to
print the value of nums[k].int_num.

The output of the code will be:

                       0  1  2  3  4  5  6  7  8  9

This output demonstrates how to declare an array of unions, assign values to the members of the
unions in the array, and print the values of the int_num member.

An array is a data structure that stores collection values that are all the same type. Arrays of
unions allow storing values of different types.

For example:

                       #include <stdio.h>

                       union type {
                        int i_val;
                        float f_val;
                        char ch_val;
                       };

                      int main() {
                        union type arr[3];

                        arr[0].i_val = 42;
                        arr[1].f_val = 3.14;
                        arr[2].ch_val = 'x';

                        return 0;
                      }

In this code, the union type is declared with the members i_val, f_val, and ch_val as provided.
Inside the main function, an array of unions arr with a size of 3 is declared.
The code then assigns the value 42 to the i_val member of arr[0] using the dot operator (.). It
assigns the value 3.14 to the f_val member of arr[1]. Finally, it assigns the value 'x' to the
ch_val member of arr[2].

No output is produced by this code. It assigns values to the members of the unions in the array
but does not perform any further operations.

This code demonstrates how to declare an array of unions and assign values to the members of the
unions in the array.
```

## MEMORY MANAGEMENT

Understanding memory is an important aspect of C programming. When you declare a variable using a
basic data type, C automatically allocates space for the variable in an area of memory called the
stack.
An int variable, for example, is typically allocated 4 bytes when declared. We know this by using
the sizeof operator:

```c
                                    int x;
                                    printf("%ld", sizeof(x)); /* output: 4 */

As another example, an array with a specified size is allocated contiguous blocks of memory with
each block the size for one element:

                                 int arr[10];
                                 printf("%ld", sizeof(arr)); /* output: 40 */

So long as your program explicitly declares a basic data type or an array size, memory is
automatically managed. However, you have probably already been wishing to implement a program where
the array size is undecided until runtime.
Dynamic memory allocation is the process of allocating and freeing memory as needed. Now you can
prompt at runtime for the number of array elements and then create an array with that many elements.
Dynamic memory is managed with pointers that point to newly allocated blocks of memory in an area
called the heap.
In addition to automatic memory management using the stack and dynamic memory allocation using the
heap, there is statically managed data in main memory for variables that persist for the lifetime
of the program.
```

## MEMORY MANAGEMENT FUNCTIONS

```c
The stdlib.h library includes memory management functions.
The statement #include <stdlib.h> at the top of your program gives you access to the following:

▪malloc(bytes) Returns a pointer to a contiguous block of memory that is of size bytes.

▪calloc(num_items, item_size) Returns a pointer to a contiguous block of memory that has num_items
items, each of size item_size bytes. Typically used for arrays, structures, and other derived data
types. The allocated memory is initialized to 0.

▪realloc(ptr, bytes) Resizes the memory pointed to by ptr to size bytes. The newly allocated memory
is not initialized.

▪free(ptr)  Releases the block of memory pointed to by ptr.

When you no longer need a block of allocated memory, use the function free() to make the block
available to be allocated again.
```

### THE MALLOC FUNCTION

```c
The malloc() function allocates a specified number of contiguous bytes in memory.

For example:

                               #include <stdlib.h>

                               int *ptr;
                               /* a block of 10 ints */
                               ptr = malloc(10 * sizeof(*ptr));

                               if (ptr != NULL) {
                                  *(ptr + 2) = 50;  /* assign 50 to third int */
                               }

malloc returns a pointer to the allocated memory.
Notice that sizeof was applied to *ptr instead of int, making the code more robust should the *ptr
declaration be changed to a different data type later.
Let's break down the code and explain what it does:

                     #include <stdlib.h>

                     int *ptr;
                     /* a block of 10 ints */
                     ptr = malloc(10 * sizeof(*ptr));

In this section, the code includes the necessary header file <stdlib.h> which contains the definition for the malloc function. It then declares a pointer ptr of type int. The malloc function is used to allocate memory dynamically. In this case, it allocates memory for a block of 10 integers (10 * sizeof(*ptr)).
The sizeof(*ptr) calculates the size of the int type on the current system. By multiplying it by 10,
we ensure enough memory is allocated to hold 10 integers.

                    if (ptr != NULL) {
                     *(ptr + 2) = 50;  /* assign 50 to third int */
                    }

The if statement checks if the memory allocation was successful. When malloc fails to allocate memory
, it returns NULL. If the allocation was successful, the code proceeds to assign the value 50 to the
third integer in the allocated block.
The expression *(ptr + 2) accesses the third integer in the block. ptr + 2 calculates the memory
address of the third integer by adding the offset of 2 int-sized units from the base address ptr.
Dereferencing that address with * allows us to assign a value to that memory location.

It's important to note that after using dynamically allocated memory, it should be freed using the
free function to avoid memory leaks.
```

### THE MALLOC FUNCTION

The allocated memory is contiguous and can be treated as an array. Instead of using brackets [ ] to
refer to elements, pointer arithmetic is used to traverse the array. You are advised to use + to
refer to array elements. Using ++ or += changes the address stored by the pointer.
If the allocation is unsuccessful, NULL is returned. Because of this, you should include code to
check for a NULL pointer.

A simple two-dimensional array requires (rows*columns)*sizeof(datatype) bytes of memory.

### THE FREE FUNCTION

```c
The free() function is a memory management function that is called to release memory. By freeing
memory, you make more available for use later in your program.

                        int* ptr = malloc(10 * sizeof(*ptr));
                        if (ptr != NULL)
                          *(ptr + 2) = 50;  /* assign 50 to third int */
                        printf("%d\n", *(ptr + 2));

                        free(ptr);







                                 THE CALLOC FUNCTION

The calloc() function allocates memory based on the size of a specific item, such as a structure.

The program below uses calloc to allocate memory for a structure and malloc to allocate memory for the
string within the structure:

                                 typedef struct {
                                   int num;
                                   char *info;
                                 } record;

                                 record *recs;
                                 int num_recs = 2;
                                 int k;
                                 char str[ ] = "This is information";

                                 recs = calloc(num_recs, sizeof(record));
                                 if (recs != NULL) {
                                 for (k = 0; k < num_recs; k++) {
                                    (recs+k)->num = k;
                                    (recs+k)->info = malloc(sizeof(str));
                                    strcpy((recs+k)->info, str);
                                    }
                                  }

calloc allocates blocks of memory within a contiguous block of memory for an array of structure
elements. You can navigate from one structure to the next with pointer arithmetic.
After allocating room for a structure, memory must be allocated for the string within the structure.
Using a pointer for the info member allows any length string to be stored.
Dynamically allocated structures are the basis of linked lists and binary trees as well as other data
structures.`

The code snippet provided allocates memory for an array of two `record` structures and populates the
`num` and `info` members of each structure. However, it does not include any output statements to
display the results. If you want to see the output, you can add code to print the values of the `num`
and `info` members after populating them. Here's an example of how you can modify the code to include
output statements:

                               #include <stdio.h>
                               #include <stdlib.h>
                               #include <string.h>

                                typedef struct {
                                   int num;
                                   char* info;
                                } record;

                               int main() {
                                 record* recs;
                                 int num_recs = 2;
                                 int k;
                                 char str[] = "This is information";

                                 recs = calloc(num_recs, sizeof(record));
                                 if (recs != NULL) {
                                     for (k = 0; k < num_recs; k++) {
                                         (recs + k)->num = k;
                                         (recs + k)->info = malloc(sizeof(str));
                                         strcpy((recs + k)->info, str);
                                     }

                                 // Output the values
                                 for (k = 0; k < num_recs; k++) {
                                      printf("Record %d:\n", k);
                                      printf("  num: %d\n", (recs + k)->num);
                                      printf("  info: %s\n\n", (recs + k)->info);
                                      }

                                // Free the allocated memory
                                for (k = 0; k < num_recs; k++) {
                                    free((recs + k)->info);
                                    }
                                free(recs);
                              }

                              return 0;
                              }

In this modified version, after populating the `num` and `info` members, the code includes a loop to
output the values of each record. The `printf` function is used to display the values of `num` and
`info` for each record.
After printing the values, the code also includes a loop to free the dynamically allocated memory to
prevent memory leaks. The `free` function is called for each `info` member and then for the `recs`
array itself.

When you run this code, it will print the values of `num` and `info` for each record in the allocated
array.
```

### THE REALLOC FUNCTION

```c
The realloc() function expands a current block to include additional memory.

                                  int *ptr;
                                  ptr = malloc(10 * sizeof(*ptr));
                                  if (ptr != NULL) {
                                        *(ptr + 2) = 50;  /* assign 50 to third int */
                                  }
                                  ptr = realloc(ptr, 100 * sizeof(*ptr));
                                  *(ptr + 30) = 75;

realloc leaves the original content in memory and expands the block to allow for more storage.
The code above allocates an initial block of memory for 10 integers using `malloc` and assigns the
value 50 to the third integer. Then, it reallocates the memory block to accommodate 100 integers using
 `realloc` and assigns the value 75 to the 31st integer.

However, it's important to note that after calling `realloc`, the memory block may have been moved to
a new location in memory. Therefore, it is necessary to assign the return value of `realloc` back to
the pointer variable `ptr` to ensure that it points to the correct memory address.

To see the output, you can add code to print the values of the third and 31st integers. Here's an
example:

                                  #include <stdio.h>
                                  #include <stdlib.h>

                                  int main() {
                                      int* ptr;
                                      ptr = malloc(10 * sizeof(*ptr));

                                      if (ptr != NULL) {
                                         *(ptr + 2) = 50;  /* assign 50 to third int */
                                      }

                                      ptr = realloc(ptr, 100 * sizeof(*ptr));

                                      if (ptr != NULL) {
                                          *(ptr + 30) = 75;  /* assign 75 to 31st int */

                                         // Output the values
                                         printf("Third int: %d\n", *(ptr + 2));
                                         printf("31st int: %d\n", *(ptr + 30));

                                         // Free the allocated memory
                                         free(ptr);
                                     }

                                     return 0;
                                     }

In this modified code, the values of the third and 31st integers are printed using `printf`. After
reallocating the memory and assigning the value 75 to the 31st integer, the output statements print the values of the third and 31st integers.

When you run this code, it will display the following output:


                             Third int: 50
                             31st int: 75



This indicates that the value 50 is assigned to the third integer before the reallocation, and the
value 75 is assigned to the 31st integer after the reallocation.
```

## ALLOCATING MEMORY STRINGS

When allocating memory for a string pointer, you may want to use string length rather than the sizeof
operator for calculating bytes.

```c
Consider the following program:

                                     char str20[20];
                                     char *str = NULL;

                                     strcpy(str20, "12345");
                                     str = malloc(strlen(str20) + 1);
                                     strcpy(str, str20);
                                     printf("%s", str);

This approach is better memory management because you aren’t allocating more space than is needed to a
pointer. When using strlen to determine the number of bytes needed for a string, be sure to include one
extra byte for the NULL character '\0'.

A char is always one byte, so there is no need to multiply the memory requirements by sizeof(char).
```

## DYNAMIC ARRAYS

```c
Many algorithms implement a dynamic array because this allows the number of elements to grow as needed.
Because elements are not allocated all at once, dynamic arrays typically use a structure to keep track
of current array size, current capacity, and a pointer to the elements, as in the following program.

                                        typedef struct {
                                          int *elements;
                                          int size;
                                          int cap;
                                        } dyn_array;

                                        dyn_array arr;

                                        /* initialize array */
                                        arr.size = 0;
                                        arr.elements = calloc(1, sizeof(*arr.elements) );
                                        arr.cap = 1;  /* room for 1 element */

To expand by more elements:

                           arr.elements = realloc(arr.elements, (5 + arr.cap) * sizeof(*arr.elements));
                           if (arr.elements != NULL)
                           arr.cap += 5; /* increase capacity */

Adding an element to the array increases its size:

                                     if (arr.size < arr.cap) {
                                        arr.elements[arr.size] = 50;
                                        arr.size++;
                                     } else {
                                        printf("Need to expand the array.");
                                     }

The entire program is written in main() for demonstration purposes. To properly implement a dynamic
array, sub-tasks should be broken down into functions such as init_array(), increase_array(),
add_element(), and display_array(). The error checking was also skipped to keep the demo short.
```

## ACCESSING FILES

An external file can be opened, read from, and written to in a C program. For these operations, C
includes the FILE type for defining a file stream. The file stream keeps track of where reading and
writing last occurred.

```c
The stdio.h library includes file handling functions:

FILE  Typedef for defining a file pointer.

fopen(filename, mode) Returns a FILE pointer to file filename which is opened using mode. If a file
cannot be opened, NULL is returned.

Mode options are:

 - r open for reading (file must exist)

 - w open for writing (file need not exist)

 - a open for append (file need not exist)

 - r+ open for reading and writing from beginning

 - w+ open for reading and writing, overwriting file

 - a+ open for reading and writing, appending to file

fclose(fp) Closes file opened with FILE fp, returning 0 if close was successful. EOF (end of file) is
returned if there is an error in closing.

The following program opens a file for writing and then closes it:

                               #include <stdio.h>

                               int main() {
                                 FILE *fptr;

                                 fptr = fopen("myfile.txt", "w");
                                 if (fptr == NULL) {
                                   printf("Error opening file.");
                                   return -1;
                                 }
                               fclose(fptr);
                               return 0;
                               }

When a string literal is used to specify a filename, the escape sequence \\ indicates a single
backslash. In this program, if there is an error when opening the file, a -1 error code is returned to
the system. Error handling is explained in a future lesson.

Closing a file when you are done using it is a good programming practice.
```

## READING FROM A FILE

```c
The stdio.h library also includes functions for reading from an open file. A file can be read one
character at a time or an entire string can be read into a character buffer, which is typically a char
array used for temporary storage.

fgetc(fp) Returns the next character from the file pointed to by fp. If the end of the file has been
reached, then EOF is returned.

fgets(buff, n, fp) Reads n-1 characters from the file pointed to by fp and stores the string in buff.
A NULL character '\0' is appended as the last character in buff. If fgets encounters a newline
character or the end of file before n-1 characters is reached, then only the characters up to that
point are stored in buff.

fscanf(fp, conversion_specifiers, vars) Reads characters from the file pointed to by fp and assigns
input to a list of variable pointers vars using conversion_specifiers. As with scanf, fscanf stops
reading a string when a space or newline is encountered.

The following program demonstrates reading from a file:

                                  #include <stdio.h>

                                  int main() {
                                     FILE *fptr;
                                     int stock;
                                     char buffer[200], item[10], c;
                                     float price;

                                     /* myfile.txt: Inventory\n100 Widget 0.29\nEnd of List */
                                     fptr = fopen("myfile.txt", "w");

                                     /* write to file */
                                     fprintf(fptr, "Inventory\n");
                                     fprintf(fptr, "%d %s %f\n", 100, "Widget", 0.29);
                                     fputs("End of List", fptr);
                                     fclose(fptr);

                                     /* myfile.txt: Inventory\n100 Widget 0.29\nEnd of List */
                                     fptr = fopen("myfile.txt", "r");
                                     fgets(buffer, 20, fptr); /* read a line */
                                     printf("%s\n", buffer);
                                     fscanf(fptr, "%d%s%f", &stock, item, &price); /* read data */
                                     printf("%d %s %4.2f\n", stock, item, price);
                                     while ((c = fgetc(fptr)) != EOF) /* read the rest of the file */
                                     printf("%c", c);
                                     fclose(fptr);
                                     return 0;
                                  }

The gets() function reads up until the newline. fscanf() reads data according to conversion specifiers.
And then the while loop reads one character at a time until the end of file. Checking for a problem
when opening the file (a NULL pointer) was left out to shorten the example.
```

## WRITING TO A FILE

```c
The stdio.h library also includes functions for writing to a file. When writing to a file, newline
characters '\n' must be explicitly added.

fputc(char, fp) Writes character char to the file pointed to by fp.

fputs(str, fp) Writes string str to the file pointed to by fp.

fprintf(fp, str, vars) Prints string str to the file pointed to by fp. str can optionally include
format specifiers and a list of variables vars.

The following program demonstrates writing to a file:

                                  FILE *fptr;
                                  char filename[50];
                                  printf("Enter the filename of the file to create: ");
                                  gets(filename);
                                  fptr = fopen(filename, "w");

                                  /* write to file */
                                  fprintf(fptr, "Inventory\n";
                                  fprintf(fptr, "%d %s %f\n", 100, "Widget", 0.29);
                                  fputs("End of List", fptr);

The "w" argument defines "writing mode" for the fopen function.
```

## BINARY FILE I/O

```c
Writing only characters and strings to a file can become tedious when you have an array or structure.
To write entire blocks of memory to a file, there are the following binary functions:

Binary file mode options for the fopen() function are:

 - rb open for reading (file must exist)

 - wb open for writing (file need not exist)

 - ab open for append (file need not exist)

 - rb+ open for reading and writing from beginning

 - wb+ open for reading and writing, overwriting file

 - ab+ open for reading and writing, appending to file

fwrite(ptr, item_size, num_items, fp) Writes num_items items of item_size size from pointer ptr to the
file pointed to by file pointer fp.

fread(ptr, item_size, num_items, fp) Reads num_items items of item_size size from the file pointed to
by file pointer fp into memory pointed to by ptr.

fclose(fp) Closes file opened with file fp, returning 0 if close was successful. EOF is returned if
there is an error in closing.

feof(fp) Returns 0 when the end of the file stream has been reached.

The following program demonstrates writing to and reading from binary files:

                             FILE *fptr;
                             int arr[10];
                             int x[10];
                             int k;

                             /* generate array of numbers */
                             for (k = 0; k < 10; k++)
                             arr[k] = k;

                             /* write array to file */
                             fptr = fopen("datafile.bin", "wb");
                             fwrite(arr, sizeof(arr[0]),
                             sizeof(arr)/sizeof(arr[0]), fptr);
                             fclose(fptr);

                             /* read array from file */
                             fptr = fopen("datafile.bin", "rb");
                             fread(x, sizeof(arr[0]), sizeof(arr)/sizeof(arr[0]), fptr);
                             fclose(fptr);

                             /* print array */
                             for (k = 0; k < 10; k++)
                                printf("%d", x[k]);

This program wrote an array of ints to a file, but an array of structures could just as easily have
been written to a file. Notice that the item size and number of items were determined by using the size
of an element and the size of the entire variable.

File extensions alone do not determine the format of data in a file, but they are useful for indicating
the type of data to expect. For example, a .txt extension indicates a text file, .bin is for binary
data, .csv indicates comma separated values, and .dat is a data file.
```

## CONTROLLING THE FILE POINTER

```c
There are functions in stdio.h for controlling the location of the file pointer in a binary file:

ftell(fp) Returns a long int value corresponding to the fp file pointer position in number of bytes
from the start of the file.

fseek(fp, num_bytes, from_pos) Moves the fp file pointer position by num_bytes bytes relative to
position from_pos, which can be one of the following constants:

- SEEK_SET start of file

- SEEK_CUR current position

- SEEK_END end of file

The following program reads a record from a file of structures:

                          typedef struct {
                               int id;
                               char name[20];
                          } item;

                          int main() {
                             FILE *fptr;
                             item first, second, secondf;

                             /* create records */
                             first.id = 10276;
                             strcpy(first.name, "Widget");
                             second.id = 11786;
                             strcpy(second.name, "Gadget");

                             /* write records to a file */
                             fptr = fopen("info.dat", "wb");
                             fwrite(&first, 1, sizeof(first), fptr);
                             fwrite(&second, 1, sizeof(second), fptr);
                             fclose(fptr);

                             /* file contains 2 records of type item */
                             fptr = fopen("info.dat", "rb");

                             /* seek second record */
                             fseek(fptr, 1*sizeof(item), SEEK_SET);
                             fread(&secondf, 1, sizeof(item), fptr);
                             printf("%d  %s\n", secondf.id, secondf.name);
                             fclose(fptr);
                             return 0;
                           }

This program wrote two item records to a file. To read just the second record, fseek() moved the file
pointer to 1*sizeof(item) bytes from the start of the file. For example, if you wanted to move the
pointer to the fourth record, then you seek to 3*sizeof(item) from the beginning of the file (SEEK_SET)

```

## EXCEPTION HANDLING

```c
Central to good programming practices is using error handling techniques. Even the most solid coding
skills may not keep a program from crashing should you forget to include exception handling.

An exception is any situation that causes your program to stop normal execution. Exception handling,
also called error handling, is an approach to processing runtime errors.

C does not explicitly support exception handling, but there are ways to manage errors:

 - Write code to prevent the errors in the first place. You can't control user input, but you can check
to be sure that the user entered valid input. When performing division, take the extra step to ensure
that division by 0 won't occur.

 - Use the exit statement to gracefully end program execution. You may not be able to control if a file
is available for reading, but you don't need to allow the problem to crash your program.

Use errno, perror(), and strerror() to identify errors through error codes.
```

## THE EXIT COMMAND

```c
The exit command immediately stops the execution of a program and sends an exit code back to the
calling process. For example, if a program is called by another program, then the calling program may
need to know the exit status.

Using exit to avoid a program crash is a good practice because it closes any open file connections and
processes.

You can return any value through an exit statement, but 0 for success and -1 for failure are typical.
The predefined stdlib.h macros EXIT_SUCCESS and EXIT_FAILURE are also commonly used.

Example

                           int x = 10;
                           int y = 0;

                           if (y != 0)
                           printf("x / y = %d", x/y);
                           else {
                             printf("Divisor is 0. Program exiting.");
                             exit(EXIT_FAILURE);
                           }







                                          USING ERRNO

Some library functions, such as fopen(), set an error code when they do not execute as expected. The
error code is set in a global variable named errno, which is defined in the errno.h header file. When
using errno you should set it to 0 before calling a library function.

To output the error code stored in errno, you use fprintf to print to the stderr file stream, the
standard error output to the screen. Using stderr is a matter of convention and a good programming
practice.

You can output the errno through other means, but it will be easier to keep track of your exception
handling if you only use stderr for error messages.

To use errno, you need to declare it with the statement extern int errno; at the top of your program
(or you can include the errno.h header file).

For example:

                                 #include <stdio.h>
                                 #include <stdlib.h>
                                 // #include <errno.h>

                                 extern int errno;

                                 int main() {
                                   FILE *fptr;

                                   errno = 0;
                                   fptr = fopen("c:\\nonexistantfile.txt", "r");
                                   if (fptr == NULL) {
                                   fprintf(stderr, "Error opening file. Error code: %d\n", errno);
                                   exit(EXIT_FAILURE);
                                 }

                                 fclose(fptr);
                                 return 0;
                                 }

```

## THE PERROR AND STRERROR FUNCTIONS

```c
When a library function sets errno, a cryptic error number is assigned. For a more descriptive message
about the error, you can use perror(). You can also obtain the message using strerror() in the string.h
header file, which returns a pointer to the message text.

perror() must include a string that will precede the actual error message. Typically, there is no need
for both perror() and strerror() for the same error, but both are used in the program below for
demonstration purposes:

                          FILE *fptr;
                          errno = 0;

                          fptr = fopen("c:\\nonexistantfile.txt", "r");
                          if (fptr == NULL) {
                            perror("Error");
                            fprintf(stderr, "%s\n", strerror(errno));
                            exit(EXIT_FAILURE);
                          }

There are more than a hundred error codes. Use these statements to list them:

                        for (int x = 0; x < 135; x++)
                        fprintf(stderr, "%d: %s\n", x, strerror(x));
```

## EDOM and ERANGE Error Codes

```c
Some of the mathematical functions in the math.h library set errno to the defined macro value EDOM when
a domain is out of range.

Similarly, the ERANGE macro value is used when there is a range error.

For example:

                            float k = -5;
                            float num = 1000;
                            float result;

                            errno = 0;
                            result = sqrt(k);
                            if (errno == 0)
                              printf("%f ", result);
                            else if (errno == EDOM)
                              fprintf(stderr, "%s\n", strerror(errno));

                            errno = 0;
                              result = exp(num);
                            if (errno == 0)
                              printf("%f ", result);
                            else if (errno == ERANGE)
                              fprintf(stderr, "%s\n", strerror(errno));
```

## THE FEOF AND FERROR FUNCTIONS

```c
In addition to checking for a NULL file pointer and using errno, the feof() and ferror() functions can
be used for determining file I/O errors:

feof(fp)  Returns a nonzero value if the end of stream has been reached, 0 otherwise. feof also sets
EOF.

ferror(fp)  Returns a nonzero value if there is an error, 0 for no error.

The following program incorporates several exception handling techniques:

                              FILE *fptr;
                              int c;

                              errno = 0;

                              fptr = fopen("myfile.txt", "r");
                              if (fptr == NULL) {
                                fprintf(stderr, "Error opening file. %s\n",
                              strerror(errno));
                                exit(EXIT_FAILURE);
                              }

                              while ((c = getc(fptr)) != EOF) /* read the rest of the file */
                                printf("%c", c);

                              if (ferror(fptr)) {
                                 printf("I/O error reading file.");
                                 exit(EXIT_FAILURE);
                              }
                              else if (feof(fptr)) {
                                 printf("End of file reached.");
                              }

Program output will vary. But if the file opens properly and the program completes reading the entire
file, then the following message displays: "End of file reached."
```

## PREPROCESSOR DIRECTIVES

```c
The C preprocessor uses the # directives to make substitutions in program source code before compilation
For example, the line #include <stdio.h> is replaced by the contents of the stdio.h header file before a
program is compiled.

Preprocessor directives and their uses:

#include Including header files.

#define, #undef Defining and undefining macros.

#ifdef, #ifndef, #if, #else, #elif, #endif Conditional compilation.

#pragma Implementation and compiler specific.

#error, #warning Output an error or warning message An error halts compilation.

Do NOT put a semicolon character at the end of a # directive.
```

## THE #INCLUDE DIRECTIVE

```c
The #include directive is for including header files in a program. A header file declares a collection
of functions and macros for a library, a term that comes from the way the collection of code can be
reused.

Some useful C libraries are:

stdio input/output functions, including printf and file operations.

stdlib memory management and other utilities

string functions for handling strings

errno errno global variable and error code macros

math common mathematical functions

time time/date utilities

Corresponding header files for the libraries end with .h by convention. The #include directive expects
brackets <> around the header filename if the file should be searched for in the compiler include paths.

A user-defined header file is also given the .h extension, but is referred to with quotation marks, as
in "myutil.h". When quotation marks are used, the file is searched for in the source code directory.

For example:

                                #include <stdio.h>
                                #include “myutil.h”

Some developers use .hpp extension for header files.
```

## THE #DEFINE DIRECTIVE

```c
The #define directive is used to create object-like macros for constants based on values or expressions.

#define can also be used to create function-like macros with arguments that will be replaced by the
preprocessor.

Be cautious with function-like definitions. Keep in mind that the preprocessor does a direct replacement
without any calculations, which can lead to unexpected results, as demonstrated with the following
program:

                                   #include <stdio.h>
                                   #define PI 3.14
                                   #define AREA(r) (PI*r*r)

                                   int main() {
                                     float radius = 2;
                                     printf("%3.2f\n", PI);
                                     printf("Area is %5.2f\n", AREA(radius));
                                     printf("Area with radius + 1: %5.2f\n",
                                   AREA(radius+1));
                                   return 0;
                                   }

Before compilation, the preprocessor expands every macro identifier. In this case, every occurrence of
PI is replaced with 3.14 and AREA(arg) is replaced with the expression PI*arg*arg. The final code sent
to the compiler will already have the constant values in place.

Not what we may expect! However, if you consider that #define works strictly by replacing text, you will
see that AREA(radius+1) becomes PI*radius+1*radius+1, which is 3.14*2+1*2+1.

The solution to this is to enclose each parameter in parentheses to obtain the correct order of
operations.

For example:

                                    #define AREA(r) (PI*(r)*(r))

The code produces the output: Area with radius + 1: 28.26.
```

## FORMATTING PROCESSOR DIRECTIVES

```c
When using preprocessor directives, the # must be the first character on a line. But there can be any
amount of white space before # and between the # and the directive.

If a # directive is lengthy, you can use the \ continuation character to extend the definition over more
than one line.

For example:

                                  #define VERY_LONG_CONSTANT \
                                  23.678901

                                  #define MAX 100
                                  #define MIN 0
                                  #    define SQUARE(x) \
                                         x*x

There can be any amount of white space before # and between the # and the directive.
```

## PREDEFINED MACRO DEFINITIONS

```c
In addition to defining your own macros, there are several standard predefined macros that are always
available in a C program without requiring the #define directive:

__DATE__  The current date as a string in the format Mm dd yyyy

__TIME__  The current time as a string in the format hh:mm:ss

__FILE__  The current filename as a string

__LINE__ The current line number as an int value

__STDC__ 1

For example:

                              char curr_time[10];
                              char curr_date[12];
                              int std_c;

                              strcpy(curr_time, __TIME__);
                              strcpy(curr_date, __DATE__);
                              printf("%s %s\n", curr_time, curr_date);
                              printf("This is line %d\n", __LINE__);
                              std_c = __STDC__;
                              printf("STDC is %d", std_c);





                          THE #IFDEF, #IFNDEF, AND #UNDEF DIRECTIVES

The #ifdef, #ifndef, and #undef directives operate on macros created with #define.

For example, there will be compilation problems if the same macro is defined twice, so you can check for
this with an #ifdef directive. Or if you may want to redefine a macro, you first use #undef.

The program below demonstrates these directives:

                           #include <stdio.h>

                           #define RATE 0.08
                           #ifndef TERM
                             #define TERM 24
                           #endif

                          int main() {
                             #ifdef RATE  /* this branch will be compiled */
                             #undefRATE
                             printf("Redefining RATE\n");
                               #define RATE 0.068
                             #else  /* this branch will not be compiled */
                               #define RATE 0.068
                             #endif

                             printf("%f  %d\n", RATE, TERM);

                             return 0;
                           }

Because RATE is defined at the top, only the #ifdef clause will be compiled. The optional #else branch
compiles when #ifdef RATE is false during preprocessing.

An #endif is required to close the block of code.

An #elif directive is like an else if and can be used to provide additional alternatives after #else.
```

## CONDITIONAL COMPILATION DIRECTIVES

```c
Conditional compilation of segments of code is controlled by a set of directives: #if, #else, #elif, and
#endif.

For example:

                        #define LEVEL 4

                        int main() {
                          #if LEVEL > 6
                            /* do something */
                          #elif LEVEL > 5
                            /* else if branch */
                          #elif LEVEL > 4
                            /* another else if */
                          #else
                           /* last option here */
                          #endif

                          return 0;
                       }

There are instances where such conditional compilation can be useful, but this type of code should be
used sparingly.

The defined() preprocessor operator can be used with #if, as in:

                       #if !defined(LEVEL)
                         /* statements */
                       #endif

The #if and if statement are not interchangeable. The #if is evaluated using data available to the
preprocessor, which then sends only the true branch for compilation.

An if statement uses data provided at runtime with the possibility of branching to any else clause.
```

## PREPROCESSOR OPERATORS

```c
The C preprocessor provides the following operators.

The # Operator

The # macro operator is called the stringification or stringizing operator and tells the preprocessor to
convert a parameter to a string constant.

White space on either side of the argument are ignored and escape sequences are recognized.

For example:

                               #define TO_STR(x) #x

                               printf("%s\n", TO_STR( 123\\12 ));






                                 THE ## OPERATOR

The ## operator is also called the token pasting operator because it appends, or "pastes", tokens
together.

For example:

                              #define VAR(name, num) name##num

                              int x1 = 125;
                              int x2 = 250;
                              int x3 = 500;

                              printf("%d\n", VAR(x, 3));
```
