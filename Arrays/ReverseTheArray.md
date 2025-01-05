# Intuition:
Here we basicaly move the element at 0th index to (n-1)th index where n = size of the array, 1st to (n-2)th and so on.

# Approach 1: Brute Force
In the brute froce approach we use another array here specifically I have used an array of name "nums[]" inorder to store elements in the reversed order by looping through once and then another loop to store the elements back from nums[] to arr[]
## Steps:
1. Create a new array of the same size.
2. Copy the elements from the original array to the new array, but in reverse order.
3. Copy the reversed elements back into the original array.
## Code:

```c

#include <bits/stdc++.h>
using namespace std;

void reverseArray(int arr[], int n){
    int nums[n];
    for(int i=0;i<n;i++){
        nums[n-i-1] = arr[i];
    }
    for(int i=0;i<n;i++){
        arr[i] = nums[i];
    }
}

int main() {
    int arr[]={1, 2, 3, 4, 5};
    int n=sizeof(arr)/sizeof(arr[0]);
    reverseArray(arr, n);
    for(int i=0;i<n;i++){
        cout<<arr[i]<<" ";
    }
    return 0;
}

```
## Time Complexity: O(n)
Since we have looped through the arrays twice so O(n) + O(n) = O(2n) ->ignoring the constant-> O(n)

## Space Complexity: O(n)
Here we have used an extra array nums[] of size n(numbers of elements in the original array) to store the elements of the array in reversed order 


# Approach 2: Better
Here I am using the 2 pointers approach considering 2 pointers : i and j
## Steps:
1. Initialise i to 0 and j to n-1
2. 2. while(i<j), keep swapping the elements
## Code:

```c


```
## Time Complexity: O(n)


## Space Complexity: O(n)
