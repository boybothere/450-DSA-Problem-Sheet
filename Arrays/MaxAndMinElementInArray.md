# Intuition
It's simple just find the maximum and minimum elemnt in the array.There are 2 approaches:

# Approach 1: Brute Force
Here we sort the lements using sort() function for simplicity, incase of minimum elemnt we access first element while incase of maximum element we access the last element

## Code for minimum element:

```c
#include <bits/stdc++.h>
using namespace std;

void minimumElement(vector<int> &arr){
    int n = arr.size();
    sort(arr.begin(), arr.end());
    cout<<arr[0];
}

int main() {
    vector<int> arr={1, 2, 3, 4, 5};
    minimumElement(arr);
    return 0;
}
```
 ## Code for maximum element:

```c
#include <bits/stdc++.h>
using namespace std;

void maximumElement(vector<int> &arr){
    int n = arr.size();
    sort(arr.begin(), arr.end());
    cout<<arr[n-1];
}

int main() {
    vector<int> arr={1, 2, 3, 4, 5};
    maximumElement(arr);
    return 0;
}
```

## Time Complexity: O(nlogn)
Sorting takes O(n log n), where log n comes from the number of divisions or recursive steps, and n comes from the number of elements that are processed at each level
The general idea is O(n log n) for sorting algorithms like MergeSort, QuickSort

# Space Complexity: O(n)
Here the function uses extra space to store the subarrays which are dealt with which are proportional to the number of elements in the sorted array

# Approach 2: Optimal
Here we assume maximum element to be INT_MIN and minimum element to be INT_MAX 
So what is this am talking about well, 
INT_MIN: The smallest value an int can store, typically -2,147,483,648 for a 32-bit system.
INT_MAX: The largest value an int can store, typically 2,147,483,647 for a 32-bit system.
Here's the code and comparison logic for further clarification:
## Code for minimum element:

```c
#include <bits/stdc++.h>
using namespace std;

void minimumElement(vector<int> &arr){
    int mini = INT_MAX, n = arr.size();
    for(int i=0;i<n;i++){
        if(arr[i]<mini){
            mini = arr[i];
        }
    }
    cout<<mini;
}

int main() {
    vector<int> arr={1, 2, 3, 4, 5};
    minimumElement(arr);
    return 0;
}

```

## Code for minimum element:

```c
#include <bits/stdc++.h>
using namespace std;

void minimumElement(vector<int> &arr){
    int maxi = INT_MIN, n = arr.size();
    for(int i=0;i<n;i++){
        if(arr[i]>maxi){
            maxi = arr[i];
        }
    }
    cout<<maxi;
}

int main() {
    vector<int> arr={1, 2, 3, 4, 5};
    minimumElement(arr);
    return 0;
}

```
## Time Complexity: O(n)
A single traversal through the array
## Space Complexity: O(1)

