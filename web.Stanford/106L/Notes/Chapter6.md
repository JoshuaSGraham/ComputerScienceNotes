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






