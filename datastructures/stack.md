#Stacks

##std::vector operations
```cpp
vector<int> stack;
stack.push_back()     //push
stack.pop_back();     //pop -- erases last element

stack.erase(stack.begin()) // erases first element

stack.back()        // reference to last element
stack.end()         // iterator pointing to one past the last element
```

##Balanced Brackets
###Problem
```cpp
int main(){
    int t;
    cin >> t;
    for(int a0 = 0; a0 < t; a0++){
        string s;
        cin >> s;
        int len = s.size();
        bool flag = true;
        vector<char> brackets;
        
        for (int i = 0; i < len; ++i) {
            char c = s[i];
            if (c=='{'||c=='['||c=='(') {
                brackets.push_back(c);
            }
            else {
                if (brackets.size() == 0) {
                    flag = false;
                    break;
                }
                char b = brackets.back();
                if (c - b > 2) {
                    flag = false;
                    break;
                }
                brackets.pop_back();
            }
        }
        if (flag && brackets.size()==0)
            cout << "YES" << endl;
        else
            cout << "NO" << endl;
    }
    return 0;
}
```