# Containers
## Intro to the Standard Template Library (STL)

![image1]

[image1]: https://i.imgur.com/e8mhb1H.png

## Sequence Containers
Sequence containers store elements of a particular type in an *ordered fashion*

![image2]

[image2]: https://i.imgur.com/WgPip3j.png

* Vector: use for most purposes
* Deque: frequent insert/remove at the front
* list: very rarely - if needed for splitting/joining

## Best Practices

What's the best way to create a vector of the first 1,000,000 integers?

```cpp
std::vector<int> vec;

for (size_t i = 0; i < 1000000; ++i)
{
    vec.push_back(i);
}
```
This implementation has a problem; Internally the array is resized and copied many times.

if possible, reverse before insert.
```cpp
std::vector<int> vec;
vec.reserve(1000000);
for (size_t i = 0; i < 1000000; ++i)
{
    vec.push_back(i);
}
```
* Consider using shrink_to_fit if you don't need the memory.
* Call empty(), rather than check if size() == 0

# Container Adaptors
## What is a wrapper?
A wrapper for an object changes how external users can interact with that object.

**Container adaptors** provide a different interface for sequence containers. You can choose what the underlying container is!

## How do you design a stack?

![image3]

[image3]: https://i.imgur.com/IW1QtFa.png

## std::stack & std::queue

![image4]

[image4]: https://i.imgur.com/H7TPAgb.png

https://en.cppreference.com/w/cpp/container/stack
https://en.cppreference.com/w/cpp/container/queue

# Associative Containers
### STL maps stores std::pairs
The underlying type stored in a std::map<K, V> is a std::pair<const K, V>.

## STL sets + maps require comparison operator
By default, the type (for sets) or key-type (for maps) must have a comparison (<) operator defined.

```cpp
std::set<int> set1;                 // Okay - comparable
std::set<std::ifstream> set2;       // Error - not comparable

std::map<int, int> map1;            // Okay - comparable
std::map<Std::ifstream, int> map2;  // Error - not comparable
```

## Iterating over the elements of a STL set/map
* The elements are ordered based on the operator< for element/key
* Because maps store pairs, each element m is an std::pair that you can use structured binding on.

```cpp
for (const auto& element : s)
{
    //do stuff with key
}

for (const auto& [key, value] : m)
{
    // do stuff with key, value
}
```

### unordered_map and unordered_set

Each STL set/map comes with an *unordered* sibling. Their usage is the same, with two differences:
- Instead of a comparison operator, the element (set) or key (map) must have a hash function defined for it
- The unordered_map/unordered_set is generally faster than map/set