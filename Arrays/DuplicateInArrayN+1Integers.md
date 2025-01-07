# Find the Duplicate Number
Given an array of integers nums containing n + 1 integers where each integer is in the range [1, n] inclusive.

There is only one repeated number in nums, return this repeated number.

# Brute Force Approach:
## Code:
```c
#include <bits/stdc++.h>
using namespace std;

int findDuplicate(vector<int>& arr) {
        int ans=0;
        for(int i=0;i<arr.size();i++){
            for(int j=i+1;j<arr.size();j++){
                if(arr[j]==arr[i]){
                    ans=arr[j];
                    return ans;
                }
            }
        }
        return ans;
    }
int main() {
    vector<int> arr={1, 2, 3, 4, 3};;
    int duplicate = findDuplicate(arr);
    cout<<duplicate;
    return 0;
}
```

Here we use 2 nested loops to check all possible comparisons to arrive at the duplicate number.

## Time Complexity: O(n)
## Space Complexity: O(1)

# Better Approach:
Here we try and reduce the time complexity to O(n) by using maps - here i will illustrate both map and unordered_map in C++, so let's go
# First we go for map
## Code
```c
#include <bits/stdc++.h>
using namespace std;

int findDuplicate(vector<int>& nums) {
        map<int, int> m;
        int ans = 0;
        for(int i=0;i<nums.size();i++){
            m[nums[i]]++;
        }
        for(auto it:m){
            if(it.second>1){
                ans = it.first;
            }
        }
        return ans;
    }
int main() {
    vector<int> arr={1, 2, 3, 4, 3};;
    int duplicate = findDuplicate(arr);
    cout<<duplicate;
    return 0;
}
```
## Time Complexity: O(nlogn)
Now we should note tht insertion of elemnts into maps takes O(logn) to break it down map uses balanced binary search tree to store the elements in ordered fashion
## Space Complexity: O(n)
Here we use map to store the n elements of the array hence given by O(n)

# Next, unordered_map

## Code
```c
#include <bits/stdc++.h>
using namespace std;

int findDuplicate(vector<int>& nums) {
        unordered_map<int, int> m;
        int ans = 0;
        for(int i=0;i<nums.size();i++){
            m[nums[i]]++;
        }
        for(auto it:m){
            if(it.second>1){
                ans = it.first;
            }
        }
        return ans;
    }
int main() {
    vector<int> arr={1, 2, 3, 4, 3};;
    int duplicate = findDuplicate(arr);
    cout<<duplicate;
    return 0;
}
```

## Time Complexity: O(n)
Though this code takes O(n) which is quite better than map it is worth noting that in its worst case it can go to O($n^2$) but these cases are very rare and the reason it occurs is due to hashing

To make it simpler and clearer, unordered_map uses hash table to store elements in no specific order so if all the lements get mapped to a single bucket then is when inserting and retreiving specially will get tedious, but in most cases it is preferred to use unordered_map over map

## Space Complexity: O(n)



