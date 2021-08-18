# Streams

A stream is an *abstraction* for input/output. Streams can take different types of input.
Any primitive type can be inserted; for other types, you need to explicitly tell c++ how to do this.

```cpp
cout << "Strings work!" << endl;
cout << 1729 << endl;
cout << 3.14 << endl;
cout << "Mixed types: " << 1123 << endl;
```

streams convert between the **string representation** of data and the data itself.

## Types of Streams
### Output Streams
* of type **std::ostream**
* Can only *receive* data with the << operator
  * Converts data to string and sends it to the stream

```cpp
std::cout << 5 << std::endl;    // prints 5 to the console

std::ofstream out("out.txt", std::ofstream::out);
out << 5 << std::endl;          // out.txt contains 5
```

### Input Streams
* Of type **std::isteam**
* Can only *give you* data with the >> operator
  * Receives string from stream and converts it to data

```cpp
// input: 5 abc 7
int x, z; string y;
std::cin >> x > y > z;          // x = 5, y = "xyz", z = 7

// std::ifstream does the same for files
std::ifstream in("out.txt", std::ifstream::in);
in >> x >> y >> z;              // out.txt contains 5
```
#### Why does this work?

![image1]

[image1]: https://i.imgur.com/3dlPum7.png

![image2]

[image2]: https://i.imgur.com/sVbvfW9.png

![image3]

[image3]: https://i.imgur.com/IgJiHa1.png

![image4]

[image4]: https://i.imgur.com/LMw4yvT.png


Reading using >> extracts a single "word" including for strings. To read a whole line, use getline(istream& stream, string& line);

### Don't mix >> with getline!

- >> reads up to the next whitespace character and does not go past that whitespace character.
- getline reads up to the next delimiter (by default, '\n'), and does go past that delimiter.
- Don't mix the two or bad things will happen.


## Stringstreams






