## Rotate array by one place(Right Rotation)
# Intuition:
Here basically we move the rightmost element to the leftmost end and adjust the others by shifting their places bt 1 to the right

# Approach 1: Using array temp[]

In this case use another array temp[] declared of the same size as input array arr[] and we shift elements from index i=0 till n-2 to their correct positions then we manipulate the first element at index 0 of the array temp[].
# Code
```c
#include <bits/stdc++.h>
using namespace std;

void rotateByOne(vector<int> &arr){
    int n=arr.size();
    vector<int> temp(n,0);
    temp[0]=arr[n-1];
    for(int i=0;i<=n-2;i++){
        temp[i+1]=arr[i];
    }
    for(int i=0;i<temp.size();i++){
        cout<<temp[i]<<" ";
    }
}

int main() {
    vector<int> arr={2, 1, 9, 4, 7, 10};;
    rotateByOne(arr);
    return 0;
}
```

## Time Complexity: O(n)
## Space Complexity: O(n)

# Approach 2: Using input array itself by taking care of avoiding segmentation faults and overwriting errors
# Code
```c
#include <bits/stdc++.h>
using namespace std;

void rotateByOne(vector<int> &arr){
    int n=arr.size();
    int temp=arr[n-1];
    for(int i=n-2;i>=0;i--){
        arr[i+1]=arr[i];
    }
    arr[0]=temp;
    for(int i=0;i<n;i++){
        cout<<arr[i]<<" ";
    }
}

int main() {
    vector<int> arr={2, 1, 9, 4, 7, 10};;
    rotateByOne(arr);
    return 0;
}
```
Here we make sure elements are not overwritten by starting our traversal from n-2 and also storing arr[0] in a variable temp if we didnt do so and try doing this after the loop we would have copied the wrong value of arr[0]

## Time Complexity: O(n)
## Space Complexity: O(1)

