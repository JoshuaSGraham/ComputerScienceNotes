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
- These ADTs give us certain guarantees about the organization and properties of our data, without our having to worry about managing the underlying details.

# Vectors

- At a high level, a vector is an ordered collection of elements of the same type that can grow and shrink in size.
  - Each element in the collection has a specific location, or index
  - All elements in a vector must be of the same type. Unlike in other programming languages, a single vector cannot contain elements of mixed types.
  - Vectors are flexible when it comes to the number of elements they can store. You can easily add and remove elements from a vector. Vectors also know their size, meaning you can query them to see how many elements they currently contain.
- Analogs in other languages: list in Python and ArrayList in Java

![image3]

[image3]: https://i.imgur.com/BM5tbPR.png

## Vector Example

Consider the following task: Given a Vector of integers, write a function that eliminates negativity from the vector by changing the sign of all negative values to turn them into their positive equivalents

```cpp
void eliminateNegativity(Vector<int> v)
{
  for (int i = 0; i < v.size(); i++)
  {
      if (v[i] < 0)
      {
          v[i] = -1 * v[i];
      }
  }
}

int main()
{
  Vector<int> nums = {1, -4, 18, -11};
  eliminateNegativity(nums);
  cout << nums << endl;
}
```

Result: The vector is passed by value, so a copy is modified, and no changes persist.

So how do we allow functions to modify vectors?

# Pass by Reference
(i.e. How do we efficiently and effectively handle data structures in functions?)

### Definition
Pass by value: When a parameter is passed into a function, the new variable stores a copy of the passed in value in memory.

Pass by reference: When a parameter is passed into a function, the new variable stores a reference to the passed in value, which allows you to directly edit the original value.

## What exactly is a reference?

We will think of a variable as a named container storing a value. E.g. double weight = 1.06
We will think of a reference as a box that just refers to an existing variable.
Said references have names and types, just like regular variables. E.g. double& weight_ref
The type has an ampersand after it to indicate it's a reference to that data type rather than the type itself

Code example:

```cpp
void tripleWeight(double& weight_ref)
{
  weight_ref *= 3; // triple the weight
}

int main()
{
  double weight = 1.06;
  tripleWeight(weight);
  cout<< wight << endl; // prints 3.18
}

```


