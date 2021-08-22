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









