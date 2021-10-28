# Types and Structs

cpp uses namespaces. e.g. **std::count, std::cin, std::lower_bound**

## Whats a type?
Types specify different "categories" for different variables

**int, double, string, bool**

cpp is a statically-typed language

### Why static typing?
* Better performance
* Easier to understand
* Better error checking

errors are caught at compile time

### Method Overloading
Define two functions with the same name but different call signatures

```cpp

double func(int x)
{
    return (double) x + 3;
}

double func(double x)
{
    return x * 3;
}

func(2) // Uses version (1), returns 5.0
func(2.0) // Uses version (2), returns 6.0
```

# Structs

A *struct* is a group of named variables each with their own type and let you group information together.

## Pairs
```cpp
int main()
{
    std::pair<bool, Student> query_result;
    query_result.first = true;
    query_result.second = {"Ethan", "CA", 30};
}
```

**std::pair** is a template. You can use any type inside it; type goes in the <>.

# Type Deduction with auto

## Type deduction using auto

```cpp 
// What types are these?
auto a = 3;
auto b = 4.3;
auto c = 'X';
auto d = "Hello";
auto e = std::make_pair(3, 3);
```

**Answers**: int, double, char, char* (a C String), std::pair<int, int>

*auto* does not mean that the variable doesn't have a type. It means that the type is deduced by the compiler.

## When should we use auto?

Typing these types out is a pain...

```cpp
std::pair<bool, std::pair<double, double>> result = quadratic(a, b, c);
std::pair<double, double> solutions = result.second;
```

Its much easier to use this

```cpp
auto result = quadratic(a, b, c);
auto solutions = result.second;
```