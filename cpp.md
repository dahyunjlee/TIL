##cpp

#Reading string from stdin
```
std::getline(std::cin, string)
```
* getline does not ignore leading whitespace characters. If there is a cin >> command before this function is called, getline will consider the leading newline character as the end.
* Resolve by calling ```cin.ignore()```
