# Intuition
We have to tradiitonally sort the elements as 0s first then 1s and then 2s

# Approach 1: Using sort() function
## Code:

```c
#include <bits/stdc++.h>
using namespace std;

void sort0s1s2s(vector<int> &arr){
    sort(arr.begin(), arr.end());
    for(int i=0;i<arr.size();i++){
        cout<<arr[i]<<" ";
    }
}

int main() {
    vector<int> arr={1, 2, 1, 1, 2, 2, 0, 0, 2, 0, 1};
    sort0s1s2s(arr);
    return 0;
}
```
## Time Complexity: O(nlogn)
## Space Complexity: O(1)

# Approach 2: 
Here we count occurence of 0s, 1, and 2s and sort accordingly

## Code:

```c
#include <bits/stdc++.h>
using namespace std;

void sort0s1s2s(vector<int> &arr){
    int count0 = 0, count1 = 0, count2 = 0;
    for(int i=0;i<arr.size();i++){
        if(arr[i]==0){
             count0++;
        }else if(arr[i]==1){
             count1++;
        }else{
             count2++;
        }
    }
    int index = 0;
    for(int i=0;i<count0;i++){
        arr[index++] = 0;
    }
     for(int i=0;i<count1;i++){
        arr[index++] = 1;
    }
     for(int i=0;i<count2;i++){
        arr[index++] = 2;
    }
    for(int i=0;i<arr.size();i++){
        cout<<arr[i]<<" ";
    }
}

int main() {
    vector<int> arr={1, 2, 1, 1, 2, 2, 0, 0, 2, 0, 1};
    sort0s1s2s(arr);
    return 0;
}
```
## Toime Complexity: O(n)
Here we traverse through the arrays so O(n) is justified
## Space Complexity: O(1)
Here no auxiliary space is used but if we argue that we manipulated the array then we can state it as O(n), normally it is bbter to specify both these statements

# Approach 3
Now we use the Dutch National Flag Algorithm
It is used to sort an array of three distinct values (often 0, 1, 2) in linear time. It uses three pointers to partition the array into three regions, efficiently sorting the elements in a single pass.

This algorithm contains 3 pointers i.e. low, mid, and high, and 3 main rules.  The rules are the following:

arr[0….low-1] contains 0. [Extreme left part]
arr[low….mid-1] contains 1.
arr[high+1….n-1] contains 2. [Extreme right part], n = size of the array
Refer: https://takeuforward.org/data-structure/sort-an-array-of-0s-1s-and-2s/

## Code:

```c
#include <bits/stdc++.h>
using namespace std;

void sort0s1s2s(vector<int> &arr){
    int n=arr.size(),low = 0, mid = 0, high = n-1;
    while(mid<=high){
        if(arr[mid]==0){
            swap(arr[mid],arr[low]);
            low++;
            mid++;
        }else if(arr[mid]==1){
            mid++;
        }else{
            swap(arr[mid],arr[high]);
            high--;
        }
    }
    for(int i=0;i<n;i++){
        cout<<arr[i]<<" ";
    }
}

int main() {
    vector<int> arr={1, 2, 1, 1, 2, 2, 0, 0, 2, 0, 1};
    sort0s1s2s(arr);
    return 0;
}
```

## Time Complexity: O(n)
## Space Complexity: O(1)
