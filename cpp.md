#C++
#Warmup

##Save the Prisoner
###Problem
A jail has  prisoners, and each prisoner has a unique id number, S, ranging from 1 to M. There are  sweets that must be distributed to the prisoners.

###Input Format
T           // Number of test cases
N M S       // T lines with three numbers
            // N: # of prisoners
            // M: # of sweets
            // S: first prisoner to get sweet

###Output Format
Print the ID number of the prisoner who gets the last sweet for every test case.

```
using namespace std;

int main() {
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */  
    int tests;
    long int num, sweets, id, sol;
    cin >> tests;
    for (int t = 0; t < tests; t++) {
        cin >> num >> sweets >> id;
        id--;
        if (sweets % num == 0)
            sweets = num;
        else 
            sweets %= num;
        if ((sol = id + sweets) > num)
            sol -= num;
        cout << sol << endl;
    }
    return 0;
}
```
###Notes
Always optimize algorithms! Always try to remove unnecessary iteration or repitition--think about what other data sets could be passed other than the one shown first.

##Data Types
###Input Format
i       // integer
d       // double
s       // string

###Output Format
i + 4
d + 4.0
givenString + s

```
    // Declare second integer, double, and String variables.
    int j = 0;
    double e = 0.;
    string t;
    // Read and save an integer, double, and String to your variables.
    cin >> j;
    cin >> e;
    cin.ignore();
    getline (cin, t);
    // Print the sum of both integer variables on a new line.
    cout << i + j << endl;    
    // Print the sum of the double variables on a new line.
    cout << fixed << setprecision(1) << d + e << endl;
    // Concatenate and print the String variables on a new line
    // The 's' variable above should be printed first.
    cout << s << t << endl;
```

###NOTES_Reading string from stdin
```
std::getline(std::cin, string)
```
* Different from ```istream::getline(input, sizeof(input))``` which uses ```char``` buffers
* ```getline()``` does not ignore leading whitespace characters. If there is a ```cin >>``` command before this function is called, getline will consider the leading newline character as the end.
* Resolve by calling ```cin.ignore()```


##Plus Minus
###Problem
Given an array of integers, calculate which fraction of its elements are positive, which fraction of its elements are negative, and which fraction of its elements are zeroes, respectively. Print the decimal value of each fraction on a new line.

###Input Format
N       // Size of array
...     // Array

```
int main(){
    int n;
    cin >> n;
    vector<int> arr(n);
    for(int arr_i = 0;arr_i < n;arr_i++){
       cin >> arr[arr_i];
    }
    
    double pos, neg, z, t;
    pos = neg = z = t = 0.;
    for (int i = 0; i < n; i++) {
        t = arr[i];
        if (t>0)
            pos++;
        else if (t<0)
            neg++;
        else 
            z++;
    }
    pos /= n;
    neg /= n;
    z /= n;
    
    printf ("%.6f\n%.6f\n%.6f", pos, neg, z);
    return 0;
}
```

###NOTES_Printing numbers
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


##Time Conversion
Change AM/PM format (07:05:45PM) to 24-hour time (19:05:45).
```
int main(){
    string time;
    cin >> time;

    int h;
    string hh, mm, ss;
    string str("PM");
    hh = time.substr(0, 2);
    mm = time.substr(3, 2);
    ss = time.substr(6, 2);
    h  = stoi(hh);
    
    size_t found = time.find(str);
    if (found == string::npos) { //if AM
        if (h == 12)
            cout << "00:" << mm << ":"<< ss <<endl;
        else
            cout << hh << ":" << mm << ":" << ss << endl;
    }
    else {
        if (h == 12)
            cout << hh << ":" << mm << ":" << ss << endl;
        else
            cout << h+12 << ":" << mm << ":" << ss << endl;
    }
    
    return 0;
}
```

###NOTES_Split string
```
string string::substr (size_t pos = 0, size_t len = npos) const;
size_t string::find (const string& str, size_t pos = 0) const;
```
* ```substr()``` returns a string starting at ```pos``` of length ```len```
* ```find()``` looks for the occurence of ```str``` starting at position ```pos``` --the function can contain many other arguments the specify the length of search sequence, individual ```char```, etc. Returns the position of the first character of the first match.
* If no matches were found, ```string::npos``` is returned.


