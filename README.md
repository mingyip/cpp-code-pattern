# cpp-code-pattern


## A. Fundamental

### 1. object construction/ initialization

### 2. object destruction

### 3. object copying - shallow vs deep

### 4. const correctness

### 5. virtual keyword

### 6. virtual destructors

### 7. pure virtual fuctions

### 8. function overloading

### 9. operator overloading

### 10. exceptions

### 11. exception safety

### 12. streams

### 13. templates

### 14. standard template library (STL)

### 15. memory management

### 16. operator new

### 17. stack objects

### 18. static objects

### 19. smart pointers

### 20. Resource acquisition is initialization (RAII)

### 21. Header file, static library and dynamic library

**Header** is typically used to contain the prototypes. Headers expand at pre-processing time so that at compile time, the code may have access to relevant function declarations/ prototypes. **Library** is the actual software that contains the definitions of the function prototypes (present in the header). Library is used at link time. The definitions (present in library) are resolved at link time.

A **static library** (also known as an **archive**) consists of routines that are compiled and linked directly into your program. When you compile a program that uses a static library, all the functionality of the static library that your program uses becomes part of your executable. On Windows, static libraries typically have a .lib extension, whereas on linux, static libraries typically have an .a (archive) extension. One advantage of static libraries is that you only have to distribute the executable in order for users to run your program. Because the library becomes part of your program, this ensures that the right version of the library is always used with your program. Also, because static libraries become part of your program, you can use them just like functionality you’ve written for your own program. On the downside, because a copy of the library becomes part of every executable that uses it, this can cause a lot of wasted space. Static libraries also can not be upgraded easy -- to update the library, the entire executable needs to be replaced.

A **dynamic library** (also called a **shared library**) consists of routines that are loaded into your application at run time. When you compile a program that uses a dynamic library, the library does not become part of your executable -- it remains as a separate unit. On Windows, dynamic libraries typically have a .dll (dynamic link library) extension, whereas on Linux, dynamic libraries typically have a .so (shared object) extension. One advantage of dynamic libraries is that many programs can share one copy, which saves space. Perhaps a bigger advantage is that the dynamic library can be upgraded to a newer version without replacing all of the executables that use it.

Because dynamic libraries are not linked into your program, programs using dynamic libraries must explicitly load and interface with the dynamic library. This mechanism can be confusing, and makes interfacing with a dynamic library awkward. To make dynamic libraries easier to use, an import library can be used.

An **import library** is a library that automates the process of loading and using a dynamic library. On Windows, this is typically done via a small static library (.lib) of the same name as the dynamic library (.dll). The static library is linked into the program at compile time, and then the functionality of the dynamic library can effectively be used as if it were a static library. On Linux, the shared object (.so) file doubles as both a dynamic library and an import library. Most linkers can build an import library for a dynamic library when the dynamic library is created.


---

## B. standard template library (STL)



## string

### string skip char
```
string str = "2C F4 32 3C B9 DE";
str.erase(remove(str.begin(),str.end(),' '),str.end()); //2CF4323CB9DE
```


### Split string by whitespace
Using isstringstream
```
std::vector<std::string> split(std::string const &input) { 
    std::istringstream buffer(input);
    std::vector<std::string> ret((std::istream_iterator<std::string>(buffer)), 
                                 std::istream_iterator<std::string>());
    return ret;
}
```
C++11 brace-initialization
```
std::vector<std::string> split(std::string const &input) { 
    std::istringstream buffer(input);
    std::vector<std::string> ret{std::istream_iterator<std::string>(buffer), 
                                 std::istream_iterator<std::string>()};
    return ret;
}
```
boost (TODO)

### Split string by a character
Using streamstring
```
#include <string>
#include <vector>
#include <sstream>

std::stringstream test("this_is_a_test_string");
std::string segment;
std::vector<std::string> seglist;

while(std::getline(test, segment, '_'))
{
   seglist.push_back(segment);
}
```
boost (TODO)

### Delete a char from string
```
  std::string str ("This is an example sentence.");
  std::cout << str << '\n';
                                           
  str.erase (10,8);                       // "This is an example sentence."
  std::cout << str << '\n';               //            ^^^^^^^^
                                           
  str.erase (str.begin()+9);              // "This is an sentence."
  std::cout << str << '\n';               //           ^
                                           
  str.erase (str.begin()+5, str.end()-9); // "This is a sentence."
  std::cout << str << '\n';               //       ^^^^^
```


### Sort `vector` with a custom function
```
sort(words.begin(), words.end(), []
  (const std::string& first, const std::string& second){
      return first.size() < second.size();
  });
```
```words: {"a", "b", "ba", "bca", "bda", "bdca"}```

## `unordered_map`

### Literating over unordered_map

```diff
+ Notice that an unordered_map object makes no guarantees 
+       on which specific element is considered its first element.
```

range based for loop
```
for (auto& it: A) {
    std::cout << it.first << " " << it.second << std::endl;;
}
```
iterator
```
std::unordered_map<string, int> wordMap({{ "First", 1 },{ "Second", 2 },{ "Third", 3 }});
for (unordered_map<string, int>::iterator it = wordMap.begin(); it != wordMap.end(); ++it) {
    std::cout << it->first << " :: " << it->second << std::endl;
}
```
for each and Lambda Functions
```
std::for_each(wordMap.begin(), wordMap.end() , [](std::pair<std::string, int > element){
            std::cout<<element.first << " :: "<<element.second<<std::endl;
            });
```


## `map`

## `unordered_set`

### Hash a dulpicated set and iterate through the set

```c++
for (auto& w : unordered_set<string> (words.begin(), words.end())) {
    ...
}
```

## `set`

## `priority_queue`

## Three Dots operator `...`

```c++
int array[10] = { [ 0 ... 9 ] = 5 };
```

The syntax you stumbled upon is a range initializer, it is a GNU extension to initialize all elements between 0and 9 to the given value, thus strictly equivalent to:

```c++
int array[10] = { [0] = 5, [1] = 5, [2] = 5, [3] = 5, [4] = 5, [5] = 5, [6] = 5, [7] = 5, [8] = 5, [9] = 5};
```

<br/>

Read more here:

https://stackoverflow.com/questions/56598905/three-dots-operator-for-initializing-an-array






