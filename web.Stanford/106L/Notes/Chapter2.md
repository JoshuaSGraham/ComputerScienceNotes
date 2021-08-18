# Initialization and References

## Uniform Initialization
### What's initialization?
Initialization is how we provide initial values to variables.
```cpp
int x = 5;
int y;
y = 6;
```

Uniform initialization is useful as it provides a way for us to use brackets to initialize anything succinctly.

```cpp
before

std::pair<bool, int> some_pair = std::make_pair(false, 6);

Student s;
s.name = "Ethan";
s.state = "CA";
s.age = 20;

After using uniform initialization

std::pair<bool, int>
     some_pair = {false, 6};

Student s = {"Ethan", "CA", 20};
```

## References

Practice Problem
```cpp
std:vector<int> original = {1,2};
std:vector<int> copy = original;
std:vector<int>& ref = original;

original.push_back(3);
copy.push_back(4);
ref.push_back(5);

//orignal (and also ref!) = {1, 2, 3, 5}
//copy = {1, 2, 4}
ref = copy;
copy.push_back(6);
ref.push_back(7);

// Q1: what are the contents of original?
// Q2: what are the contents of copy?
```

Answers:

A reference is always an alias to the same variable. This means setting ref equals to a new value is exactly the same as setting original equal to that value! We can't change what variable ref aliases.
```cpp
// original = {1, 2, 4, 7}
// copy = {1, 2, 4, 6}
```

**Note: you can only create references to variables**. This has something to do with L-values.

## Const and Const References

The keyword *const* indicates a variable can't be modified!
Const variables can be references or not!
You can't declare non-const references to const variables.
You can't declare a non-const ref to a const ref.
if you don't write &, c++ will make a copy by default. 

You even need to explicitly specify const and & with auto!

```cpp
std::vactor<int> vec = {1, 2, 3};
const std::vector<int> c_vec = {7, 8};
std::vector<int>& ref = vec;
const std::vector<int>& c_ref = vec;

auto copy = c_ref;        // A non-const copy
const auto copy = c_ref;  // A const copy
auto& a_ref = ref;        // A non-const reference
const auto& c_aref = ref; // A const reference
```

**Remember: C++, by default, makes copies when we do variable assignment! We need to use & if we need references instead.**

## More about References
You can return references as well! This is a feature of c++ that the standard library frequently makes use of.
```cpp
// Note that the parameter must be a non-const reference to return
// a non-const reference to one of its elemnents!

int& front(std::vector<int>& vec)
{
    // assuming vec.size() > 0
    return [0];
}

int main()
{
std::vector<int> numbers = {1, 2, 3};
front(numbers) = 4; // vec = {4, 2, 3}
return 0;
}
```
Can also return const references
```cpp
const int& front(std::vector<int>& vec)
{
    // assuming vec.size() > 0
    return vec[0];
}
```

Dangling references: references to out-of-scope vars. Never return a reference to a local variable! They will go out of scope.
```cpp
int& front(const std::string& file)
{
    std::vector<int> vec = readFile(file);
    return vec[0];
}

int main()
{
    front("text.txt") = 4; // Undefined behavior
    return 0;
}
```

### When do we use references / const references?
- If we are working with a variable that takes up little space in memory (e.g. int, double), we don't need to use a reference and can just copy the variable.
- If we need to **alias** the variable to modify it, we can use references.
- If we don't need to modify the variable, but it's a big variable (e.g. std::vector), we can use const references.

# Recap
* **Uniform initialization**
    - A "uniform" way to initialize variables of different types
* **References**
    - Allows us to alias variables
* **Const**
    - Allows us to specify that a variable can't be modified