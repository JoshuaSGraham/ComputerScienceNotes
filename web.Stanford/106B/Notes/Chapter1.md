# String in C++

## What are the key characteristics of strings in C++

* Strings are mutable in C++
* You can add characters to strings and strings to strings using += and +
  * Strings must use double quotes ("") while characters use sing ('').
* You can use logical operators to compare strings
  * Under-the-hood, C++ is using the ASCII values of their first characters to compare.


## String Utility functions

There are three categories of functions
* Built-in C++ char functions (<cctype> library)
* Built-in C++ string methods (<String> library)
* Stanford string library functions ("strlib.h" library)

![image1]

[image1]: https://i.imgur.com/xHDu0Cx.png

![image2]

[image2]: https://i.imgur.com/UruQVn8.png

# Two types of C++ strings

- C strings have no methods
    - This is why you can't do something like "hi".length() in C++

* Conversion fixes
  * **Store the C string in variable first** to convert it to a C++ string
  * Use a conversion function

string("text"); converts the C string literal into a C++ string
string.c_str() returns a C string from a C++ string

# Console Programs

## How do we build programs that interact with users?
**Console Program:** A program that uses the interactive terminal (console) as a communication boundary with the user. 

### The console and the getLine() function
- The console is the text-output area that we have already seen when using cout to display information. In addition to displaying text, the console can also solicit text form a user
- The getLine() function takes in a single parameter, which is a prompt to show to the user.
- The function will then wait while the user types in text into the console.
- After the user submits their answer by hitting the "Enter/Return" key, the function returns the value that the user types into the console.

## Summary
* use getLine(prompt) to read in information from the user.
* Use a while loop to enable multiple runs of your program.
  * While(true) paired with a break is a powerful construct but also dangerous!
* Console programs must be run directly from main()

# How do we structure data using abstractions in code?

## Abstract Data Types

- Data structures, or **abstract data types (ADTs)**, are powerful abstractions that allow programmer to store data in structured, organized ways.
- These ADTs give us certain guarantees about the organization and properties of our data, whithout our having to worry about managing the underlying details.













