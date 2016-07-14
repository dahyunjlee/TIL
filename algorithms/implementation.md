# Implementation Challenges #

##Kangaroo
###Problem
There are two kangaroos on an x-axis ready to jump in the positive direction (i.e, toward positive infinity). The first kangaroo starts at location  and moves at a rate of  meters per jump. The second kangaroo starts at location  and moves at a rate of  meters per jump. Given the starting locations and movement rates for each kangaroo, can you determine if they'll ever land at the same location at the same time?

###Input Format
A single line of four space-separated integers denoting the respective values of x1, v1, x2, and v2.

###Output Format
Print YES or NO

```
using namespace std;
int main(){
    int x1;
    int v1;
    int x2;
    int v2;
    cin >> x1 >> v1 >> x2 >> v2;
    double n = (double)(x1-x2) / (double)(v2-v1);
    int i = (int)n;
    if (n>0 && (n-i)==0)
        cout<< "YES"<< endl;
    else
        cout<<"NO"<< endl;
    
    return 0;
}
```

##Equal Stacks
###Problem
Three stacks of cylinders. Remove some off the top to make the three stacks the same height.

###Input Format
n1, n2, n3  // number of cylinders in each stack
            // Three lines describing each cylinder height

```
using namespace std;

int main(){
    int n1;
    int n2;
    int n3;
    int sum1, sum2, sum3;
    sum1 = sum2 = sum3 = 0;
    cin >> n1 >> n2 >> n3;
    vector<int> h1(n1);
    for(int h1_i = 0;h1_i < n1;h1_i++){
       cin >> h1[h1_i];
       sum1 += h1[h1_i];
    }
    vector<int> h2(n2);
    for(int h2_i = 0;h2_i < n2;h2_i++){
       cin >> h2[h2_i];
       sum2 += h2[h2_i];
    }
    vector<int> h3(n3);
    for(int h3_i = 0;h3_i < n3;h3_i++){
       cin >> h3[h3_i];
       sum3 += h3[h3_i];
    }
    vector<vector<int>> hs;
    hs.push_back(h1);
    hs.push_back(h2);
    hs.push_back(h3);
    
    vector<int> sums;
    sums.push_back(sum1);
    sums.push_back(sum2);
    sums.push_back(sum3);
    
    int minh = min(min(sum1, sum2), sum3);
    while (sums[0] != sums[1] || sums[1] != sums[2]) {
        for (int i = 0; i < 3; i++) {
            if (sums[i] > minh) {
                sums[i] -= hs[i][0];
                hs[i].erase(hs[i].begin());
                minh = min(min(sums[0], sums[1]), sums[2]);
            }
        }
    }
    cout << minh << endl;
    
    return 0;
}
```

##Cut the Sticks
###Problem
You are given  sticks, where the length of each stick is a positive integer. A cut operation is performed on the sticks such that all of them are reduced by the length of the smallest stick.

###Input Format
int N       // number of sticks
N integers  // lenght of each stick

###Output Format
Print the number of sticks that are cut before each operation.

```
using namespace std;

int minimum(vector<int>& v, int& n) {
    int minimum = 1001;
    for (int i = 0; i < n; i++) {
        if(v[i] < minimum && v[i] > 0)
            minimum = v[i];
    }
    if (minimum == 1001)
        return 0;
    return minimum;
}
int cut(vector<int>& v, int& sol, int& n) {
    int c = minimum(v, n);
    if (c == 0)
        return 0;
    for (int i = 0; i < n; i++) {
        if (v[i] > 0) {
            v[i] -= c;
            if (v[i] <= 0)
                sol--;
        }
    }
    return 0;
}

int main(){
    int n;
    cin >> n;
    vector<int> arr(n);
    for(int arr_i = 0;arr_i < n;arr_i++){
       cin >> arr[arr_i];
    }
    int sol = n;
    while (sol > 0) {
        cout << sol << endl;
        cut(arr, sol, n);
    }
    return 0;
}
```