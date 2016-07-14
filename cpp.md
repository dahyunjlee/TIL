#C++

###Reading string from stdin
```
std::getline(std::cin, string)
```
* Different from ```istream::getline(input, sizeof(input))``` which uses ```char``` buffers
* ```getline()``` does not ignore leading whitespace characters. If there is a ```cin >>``` command before this function is called, getline will consider the leading newline character as the end.
* Resolve by calling ```cin.ignore()```

###Printing numbers
```
std::setpricision(int n)
```
* ```include <iomanip>```
* ``` cout << setprecision (2) ``` accounts for the whole number. To specify decimal precision only, also call ```<< std::fixed```

```
printf(%f)
printf(%.2f)
```
* ```include <cstdio>```
* f is for ```double``` -- the number tha comes after %. and before f determines the number of decimals

###Split string
```
string string::substr (size_t pos = 0, size_t len = npos) const;
size_t string::find (const string& str, size_t pos = 0) const;
```
* ```substr()``` returns a string starting at ```pos``` of length ```len```
* ```find()``` looks for the occurence of ```str``` starting at position ```pos``` --the function can contain many other arguments the specify the length of search sequence, individual ```char```, etc. Returns the position of the first character of the first match.
* If no matches were found, ```string::npos``` is returned.