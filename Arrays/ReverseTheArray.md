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
2. while(i<j), keep swapping the elements, increment i and decrement j
## Code:

```c
#include <bits/stdc++.h>
using namespace std;

void reverseArray(int arr[], int n){
    int i=0, j=n-1;
    while(i<=j){
        int temp=arr[i];
        arr[i]=arr[j];
        arr[j]=temp;
        i++;
        j--;
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
Here we loop through the entire array beginning from either sides till i>j

## Space Complexity: O(1)
Here no extra space is used hence the given space complexity

# Approach 3: Optimal
Here instead of 2 pointers we use just 1 pointer which is a slight optimization
## Steps:
1. Initialise i to 0 
2. while(i<n/2), keep swapping the elements, increment i
## Code:

```c
#include <bits/stdc++.h>
using namespace std;

void reverseArray(int arr[], int n){
    int i=0, j=n-1;
    while(i<n/2){
        int temp=arr[i];
        arr[i]=arr[n-i-1];
        arr[n-i-1]=temp;
        i++; 
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
Here we loop through the first half of the array hence O(n/2) but we we knwo we take this as O(n) according to the Big-O notation

## Space Complexity: O(1)
Here no extra space is used hence the given space complexity

# Another Approach: Using C++'s inbuilt reverse function i.e reverse(arr.begin(), arr.end())
## Code:

```c
#include <bits/stdc++.h>
using namespace std;

void reverseArray(vector<int> &arr){
    reverse(arr.begin(), arr.end());
}

int main() {
    vector<int> arr={1, 2, 3, 4, 5};
    reverseArray(arr);
    for(int i=0;i<arr.size();i++){
        cout<<arr[i]<<" ";
    }
    return 0;
}
```
## Time Complexity: O(n)
## Space Complexity: O(1)


