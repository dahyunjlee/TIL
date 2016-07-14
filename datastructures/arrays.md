#Arrays

##2D Arrays
###Problem
Given a 6x6 2D Array, and hourglass is the subset of values in
a b c
  d
e f g
pattern. An hourglass sum is the sum of an hourglass' values. Print the maximum hourglass sum in the given 2D Array.

```
using namespace std;

int main(){
    vector< vector<int> > arr(6,vector<int>(6));
    for(int arr_i = 0;arr_i < 6;arr_i++){
       for(int arr_j = 0;arr_j < 6;arr_j++){
          cin >> arr[arr_i][arr_j];
       }
    }
    int maxsum = 0;
    int sum = 0;
    bool first = true;
    for(int j = 0; j < 4; j++) {
        for(int i = 0; i < 4; i++) {
            sum  = arr[i][j] + arr[i][j+1] + arr[i][j+2];
            sum += arr[i+1][j+1];
            sum += arr[i+2][j] + arr[i+2][j+1] + arr[i+2][j+2];
            if (first) {
                maxsum = sum;
                first = false;
            }
            if (sum > maxsum && !first)
                maxsum = sum;
        }
    }
    cout<< maxsum << endl;
    return 0;
}
```

###Notes
Denoting 2D Arrays:
```
array[*row*][*column*]
```
