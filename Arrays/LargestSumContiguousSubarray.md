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

# Optimal Approach

This is a famous algorithm used specifically to find the largest sum of contiguous subarrays
1. Basically we add the array elements to the sum which we initialize to 0 
2. Then we perform a check to see if the calculated sum is greater than the maximum sum obtained yet and update the maximum accordingly
3. If sum calculated is negative we simply make sum = 0 because we need to maximize our sum

## Code:
 ```c
#include <bits/stdc++.h>
using namespace std;

int maxSubarraySum(vector<int> &arr) {
        int maxi = INT_MIN, sum=0;
        for(int i=0;i<arr.size();i++){
            sum+=arr[i];
            if(sum>maxi){
                maxi=sum;
            }
            if(sum<=0){
                sum=0;
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

## Time Complexity: O(n)
## Space Complexity: O(1)


