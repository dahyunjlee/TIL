#Strings

###Notes
```cpp
string s;
for (int i = 0; i < s.size() - 1; ++i)
    char c = s[i];
```
* `size()` returns the length of the string
* `string_name[int]` simply refers to the character in that index

##Palindromes
```
string s;
int i, j, sol;
for (i = 0, j=s.size()-1; i < j; ++i, --j) {
    sol += abs(s[i] - s[j]);
}
```