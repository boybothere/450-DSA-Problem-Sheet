# Intuition: I am assuming one side to be the end of the array
So the ouput will be like positive numebers followed by negative numbers
Alao assuming no number order preservation
# Approach 1: Using sort() function

## Code:

```c
#include <bits/stdc++.h>
using namespace std;

void MoveNegativeElementsToOneSideOfTheArray(vector<int> &arr){
    sort(arr.begin(), arr.end(), greater<int>());
    for(int i=0;i<arr.size();i++){
        cout<<arr[i]<<" ";
    }
}

int main() {
    vector<int> arr={1, -2, 3, 5, -6, 7, 9, -10, 10};
    MoveNegativeElementsToOneSideOfTheArray(arr);
    return 0;
}
```
 Here greater&lt;int&gt;() is used since it has to be sorted in non incraesing order
## Time Complexity: O(nlogn)
## Space Complexity: O(1)

# Approach 2: Better
Here we try and use the 2 pointers approach
# Steps:
1. Initialise n as size of the array, i=0, j=n-1, posIndex = 0, negIndex = n-1 plus a new array nums[] of size n
2. while(i<=j), we check whether the number is positive or negative
   -> if positive then nums[posIndex++]=arr[i] and i++
   -> else nums[negIndex--]=arr[i] and j--
3. Print the array nums[]

## Code:

```c
#include <bits/stdc++.h>
using namespace std;

void MoveNegativeElementsToOneSideOfTheArray(vector<int> &arr){
   int n=arr.size(),posIndex=0, negIndex=n-1;
   vector<int> nums(n, 0);
   for(int i=0;i<n;i++){
       if(arr[i]>=0){
           nums[posIndex++]=arr[i];
       }else{
           nums[negIndex--]=arr[i];
       }
   }
   for(int i=0;i<n;i++){
       cout<<nums[i]<<" ";
   }
}

int main() {
    vector<int> arr={1, -2, 3, 5, -6, 7, 9, -10, 10};
    MoveNegativeElementsToOneSideOfTheArray(arr);
    return 0;
}

```
## Time Complexity: O(n)
## Space Complexity: O(n)

# Approach 3: Optimal
Using the Dutch National Flag algorithm for sorting 2 distinct kind of features

Positive Elements.....Unknown Elements.......Negative Elements

0    to   low-1 | low        to        high | high + 1  to  n-1

## Code:

```c
#include <bits/stdc++.h>
using namespace std;

void MoveNegativeElementsToOneSideOfTheArray(vector<int> &arr){
    int n=arr.size(),low=0, high=n-1;
    while(low<=high){
        if(arr[low]>=0){
            low++;
        }else{
            swap(arr[low],arr[high]);
            high--;
        }
    }
    for(int i=0;i<n;i++){
        cout<<arr[i]<<" ";
    }
}

int main() {
    vector<int> arr={1, -2, 3, 5, -6, 7, 9, -10, 10};
    MoveNegativeElementsToOneSideOfTheArray(arr);
    return 0;
}

```
## Time Complexity: O(n)
## Space Complexity: O(1)

