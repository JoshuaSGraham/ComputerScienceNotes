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



