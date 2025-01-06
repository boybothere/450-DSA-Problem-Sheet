# Longest sum of contiguous subarray

# Brute Force approach
Here we run 3 loops in total, 2 for discovering and evaluating every possible subarray and another loop for sum calculation using the foollowing logic embraced in this code
```c
#include <bits/stdc++.h>
using namespace std;

int maxSubarraySum(vector<int> &arr) {
        int maxi = INT_MIN;
        for(int i=0;i<arr.size();i++){
            int sum=0;
           for(int j=i;j<arr.size();j++){
               for(int k=i;k<=j;k++){
                   sum+=arr[k];
               }
               maxi=max(sum, maxi);
           }
        }
        return maxi;
    }
int main() {
    vector<int> arr={1, 2, 3, 4, 3};;
    int maxi = maxSubarraySum(arr);
    cout<<maxi;
    return 0;
}
```

## Time Complexity: O($n^3$)
## Space Complexity: O(1)

# Better approach
Here we run 2 loops in total, 2 for discovering and evaluating every possible subarray as well as we devise another way to reduce one loop logically by some observation
```c
#include <bits/stdc++.h>
using namespace std;

int maxSubarraySum(vector<int> &arr) {
        int maxi = INT_MIN;
        for(int i=0;i<arr.size();i++){
            int sum=0;
           for(int j=i;j<arr.size();j++){
                   sum+=arr[j];
               maxi=max(sum, maxi);
           }
        }
        return maxi;
    }
int main() {
    vector<int> arr={1, 2, 3, 4, 3};;
    int maxi = maxSubarraySum(arr);
    cout<<maxi;
    return 0;
}
```
## Time Complexity: O($n^2$)
## Space Complexity: O(1)


