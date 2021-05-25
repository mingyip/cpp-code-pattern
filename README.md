# cpp-code-pattern


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

## `set`

## `priority_queue`
