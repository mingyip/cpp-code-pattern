# cpp-code-pattern


## string

#### Delete a char from string
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


#### Sort `vector` with a custom function
```
sort(words.begin(), words.end(), []
  (const std::string& first, const std::string& second){
      return first.size() < second.size();
  });
```
```words: {"a", "b", "ba", "bca", "bda", "bdca"}```

## `unordered_map`

## `map`

## `unordered_set`

## `set`

## `priority_queue`
