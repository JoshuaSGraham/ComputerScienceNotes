# Iterators

Iterators allow iteration over **any** container whether ordered or unordered.

Generally, STL iterators support the following operations:
```cpp
std::set<T> s;
auto iter = s.begin();      
iter++;                     // increment;
*iter;                      // dereference iter to get current value
(iter != s.end());          // equality comparison

iter = another_iter;        // copy constructor

// STL sets have the following operations:
s.begin();                  // an iterator pointing to the first element
s.end();                    // one past the last element
```

## Why use ++iter and not iter++?
**Answer**: ++iter returns the value after being incremented, so there's no need to store the old value of the iterator!

## Iterator Basics
```cpp
std::map<int, int> map {{1, 2}. {3, 4}};
// note that dereferencing a std::map::iterator returns a std::pair

auto iter = map.begin();            // what is *iter?
++iter;                             // what is (*iter).second now?
auto iter2 = iter;
++iter;                             // what does (*iter).first return?

// ++iter: go to the next element
// *iter: retrieve what's at iter's position
// copy constructor: create another iterator pointing to the same thing
```

*iter returns {1,2}
*iter is then incremented to the next element
*iter now points to {3, 4}, so *iter.second is 4
auto iter2 = iter  creates an independent copy of iter pointing to the same thing
Then we increment iter (iter2 is not impacted)
*iter.first returns undefined! as iter == map.end(); i.e. its pointing to after the map

## Types of Iterators
- All iterators are incrementable (++)
- **Input** iterators can be on the right side if =:
  - auto elem = *it;
- **Output** iterators can be on the left side of =:
  - *elem = value;
- **Forward** iterators can be traversed multiple times:
```cpp
iterator a;
b = a;
a++; b++;
assert (*a == *b)       //true
```
- **Random access** iterators support indexing by integers!
```cpp
it += 3;            // move forward by 3
it -= 70;           // move backwards by 7-
auto elem = it[5];  // offset by 5
```

# Template Functions

## Ternary Operator
```cpp
int my_min(int a, int b)
{
    return a < b ? a : b;
}

// is equivalent to
int my_min(int a, int b)
{
    if (a < b) return a;

    else return b;
}
```

## Can we handle different types?
```cpp
int main()
{
    auto min_int = my_min(1, 2);
    auto min_name = mymin("Nikhil", "Ethan");
}
```

One way would be to use overloaded functions
```cpp
int my_min(int a, int b)
{
    return a < b ? a : b;
}

std::string my_min(std::string a, std::string b)
{
    return a < b ? a : b;
}
```

But this leaves a bigger problem: how do we handle user-defined types? (e.g. our Student struct from a few chapters ago)

We can write a generic function!

```cpp
template <typename T>
T my_min(T a, T b)
{
    return a < b ? a : b;
}
```
the keyword template declares that the next declaration is a template.
typename specifies T is some arbitrary type
T stands for a list of template arguments that can be passed in
Note: the scope of the template argument T is limited to this one function!

In case we don't want to copy T
```cpp
template <typename T>
T my_min(const T& a, const T& b)
{
    return a < b > a : b;
}
```
There are two ways to call template functions.
1. Explicit instantiation of templates 
```cpp
my_min<std::string>("Nikhil", "Ethan");
```
This explicitly states T = string

2. Implicit instantiation of templates
```cpp
my_min(3, 4);
```
The compiler deduces T = int

This implementation is not perfect as if we call our method using my_min(4, 3.2). Returns 3. To fix this we will change our method slightly.

```cpp
template <typename T, typename U>
auto my_min(const T& a, const U& b)
{
    return a < b ? a : b;
}

my_min(4, 3.2);
// return 3.2
```
We set the return type to auto, so as to let the compiler figure out what type it is at compile time. And to account for the possibility of two different incoming types we change b to be a different lettering.

### Template Instantiation

When you call a template function, either:
* for explicit instantiation, compiler creates a function in the executable that matches the initial template, with the correct template parameters.
* for implicit instantiation, compiler deduces the template parameters, and creates the correct function in the same way.
* After instantiation, the compiled code looks as if you had written the instantiated version of the function yourself.

# Concept lifting

What assumptions are we making about the parameters?

Can we solve a more general problem by relaxing some of the constraints?

## Why write generic functions?

- Count the # of times **3** appears in a std::vector<int>
- Count the # of times **"X"** appears in a std::istream
- Count the # of times **a vowel** appears in the second half of a std::string
  
By writing generic functions, we can solve all of these problems with a single function!

We do this by removing as many assumptions as we can.

```cpp
int count_occurrences(const vector<int>& vec, int val)
{
    int count = 0;
    for (size_t i = 0; i < vec.size(); i++>)
    {
        if (vec[i] == val)
        {
            count++;
        }
    }

    return count;
}

vector<int> v; count_occurrences(v, 5);
```
What assumptions are we making here?
What if we want to generalize this beyond ints?

How many times does a <T> appear in a vector<t>?
```cpp

template <typename DataType>
int count_occurrences(const vector<DataType>& vec, DataType val)
{
    int count = 0;
    for (size_t i = 0; i < vec.size(); i++)
    {
        if (vec[i] == val)
        {
            count++;
        }
    }

    return count;
}

vector<string> v; vount_occurrences(v, "test");
```
This is much better! But what if we want to generalize this beyond a vector?

```cpp
template <typename InputIt, typename DataType>
int count_occurrences(INputIt begin, InputIt end, DataType value)
{
    int count = 0;
    for (auto iter = begin; iter != end; ++iter)
    {
        if (*iter == value)
        {
            count++
        }
    }

    return count;
}

vector<string> v; count_occurrences(v.begin(), v.end(), "test");
```

### We can now solve these questions...
* Count the number of times **3** appears in a list<int>
* Count the number of times **'X'** appears in a std::deque<char>
* Count the number of times **'Y'** appears in a string
* Count the number of time **5** appears in the second half of a vector<int>

## Predicates

### Unary Predicates
```cpp
bool isEqualTo3(int a)
{
    return (a == 3);
}

bool isVowel(char c)
{
    return std::find("aeiou", c) != -1;
}
```

### Binary Predicates
```cpp
bool isDivisibleBy(int a, int b)
{
    return (a % b == 0)
}

bool isLessThan(int a, int b)
{
    return (a < b);
}
```

### Calling this function with a predicate
```cpp
template <typename InputIt, typename DataType, typename UniPredicate>
int count_occurrences(InputIt begin, InputIt end, UniPredicate predicate)
{
    int count = 0;
    for (auto iter = begin; iter != end; ++iter)
    {
        if (pred(*iter) == val)
        {
            count++;
        }
    }

    return count;
}


bool is_even(int i)
{
    return (i % 2) == 0;
}
vector<int> v; count_occurences(v.begin(), v.end(), is_even);
// this is a function pointer
```

Function pointers generalize poorly
```cpp
bool is_greater_than_5(int i)
{
    return (i > 5);
}

bool is_greater_than_6(int i)
{
    return (i > 6);
}

bool is_greater_than_7(int i)
{
    return (i > 7);
}

// We can't add the limit as a parameter to the function (Why?)
```

This is fundamentally a **scope** problem. We need to pass the *limit* in without adding another parameter...