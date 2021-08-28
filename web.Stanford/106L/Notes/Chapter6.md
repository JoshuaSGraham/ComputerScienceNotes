# Lambda Functions

Lambda functions let you make a new function on the fly


## Lambda Syntax

```cpp
auto is_less_than = [limit](auto val)
{
    return (val < limit);
}
```
* We don't know the type, but that doesn't matter here
* **[limit]** capture clause lets us use outside variables
* You can also use auto in lambda in the parameters
* Here, only val and limit are in scope in the lambda

```cpp
int main()
{
    auto print_int = [](int x){
                        count << x <<endl;
                    };

    // print_int is a function now!
    print_int(5); // "5"
    print_int(7); // "7"
}

// The type of print_int does not matter!
```
**Lambda capture** allows you to pass information in
```cpp
int main()
{
    int limit;
    std::cin >> limit;
    auto is_less_than = [limit](int val) { return (val < limit) };
}

// This solves our earlier problem
```

Counting how many numbers are less than a value
```cpp
template <typename InputIt, typename DataType, typename UniPred>
int count_occurrences(InputIt begin, InputIt end, UniPred pred)
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

auto is_less_than = [limit](int val) { return (val < limit) };
vector<int> v; count_occurrences(v.begin(), v.end(), is_less_than);
// This counts the number of times a number under limit appears
```

## Capture Values

```cpp
auto lambda = [capture-values](arguments)
{
    return expression;
}

[x](arguments)              // captures x from surrounding scop by value
[x&](arguments)             // captures x from surrounding scope by reference
[x, y](arguments)           // captures x, y by value
[&](arguments)              // captures everything by reference
[&, x](arguments)           // captures everything except x by reference
[=](arguments)              // captures everything by copy
```

Previously because we made too many assumptions, our code was not very portable
```cpp
int count_occurrences(const vector<int>& vec, int val)
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

vector<int> v; count_occurrences(v, 5);
```

But with lambdas we can make the same function look something like this...
```cpp
template <typename InputIt, typename DataType, typename UniPred>
int count_occurrences(InputIt begin, InputIt end, UniPred pred)
{
    int count = 0;
    for (auto iter = begin; iter != end; ++iter)
    {
        if (pred(*iter) == val) count++;
    }
    return count;
}
```

# Algorithms & STL

### STL is a collection of **generic template functions**

std::count_if(InputIt first, InputIt last, UnaryPredicate p);
Count the number of elements between *first* and *last* satisfying p.

std::find(InputIt first, InputIt last, UnaryPredicate p);
Finds the first element between *first* and *last* satisfying p.

std::sort(RandomIt first, RandomIt last);
Sorts the elements between *first* and *last*.

## STL functions operate on Iterators
std::minmax_element(InputIt first, InputIt last);
Returns a tuple[min,max] over the elements between *first* and *last*.

std::stable_partition(InputIt first, InputIt last, UnaryPredicate p);
Reorders the elements between *first* and *last* such that all elements for which p returns true come before those for which it returns false.

std::copy(InputIt first, InputIt last, OutputIt target);
Copies the elements between *first* and *last* into *target*. (There's also a std::copy_if)

![image]

[image]: https://i.imgur.com/yxntVuI.png

## Things you can do with the STL

- Binary search
- Heap building
- min/max lexicographical comparisons
- merge
- set union
- set difference
- set intersection
- partition
- sort nth sorted element
- shuffle
- selective removal
- selective copy
- for-each
- move backwards

**All in their most general form**