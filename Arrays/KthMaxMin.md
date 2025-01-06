# Kth max and min element in an array
# Intuition:
Here k will represent a number within the array bounds and we have to find the kth smallest or largest element like if given array is nums[]={1, 2, 3, 4} 2nd smallest is 2 and 2nd largest is 3
# Approach 1: Using sort() function

Here we sort the given array ans get the kth smallest element at (k-1)th index so basically arr[k-1] while kth largest at index (n-k) so arr[n-k]

# Code for kth smallest element
```c
#include <bits/stdc++.h>
using namespace std;

void kthmin(vector<int> &arr, int k){
    sort(arr.begin(), arr.end());
    cout<<arr[k-1];
}

int main() {
    vector<int> arr={2, 1, 9, 4, 7, 10};
    int k;
    cin>>k;
    kthmin(arr, k);
    return 0;
}
```
# Code for kth largest element
```c
#include <bits/stdc++.h>
using namespace std;

void kthmax(vector<int> &arr, int k){
    int n=arr.size();
    sort(arr.begin(), arr.end());
    cout<<arr[n-k];
}

int main() {
    vector<int> arr={2, 1, 9, 4, 7, 10};
    int k;
    cin>>k;
    kthmax(arr, k);
    return 0;
}
```
## Time Complexity: O(nlogn)
## Space Complexity: O(1)

Approach 2: Using quicksort algorithm
We apply the partition step of the Quicksort algorithm, where a pivot element is chosen, and the array is rearranged such that all elements smaller than the pivot are on its left, and all elements greater are on its right.
Here in simple words we apply quicksort algorithm to find the partition index then:
1. if partition index matches " k-1 " then we have found our kth smallest element
2. else if it is less than " k-1 " then we make left=index+1, in doing so we know there is no point searching in the left half of the index evaluated since we know the kth smallest element lies in the right half
3. likewise if the above cases are not satisfied we eliminate the right half by making right=index-1

# Code for kth smallest
```c
#include <bits/stdc++.h>
using namespace std;

int partition(vector<int> &arr, int low, int high){
    int pivot=arr[low];
    int i=low;
    int j=high;
    while(i<j){
        while(arr[i]<=pivot && i<=high){
            i++;
        }
         while(arr[j]>pivot && j>=low){
            j--;
        }
        if(i<j){
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[low], arr[j]);
    return j;
}

int kthmin(vector<int> &arr,int k){
    int n=arr.size(), low=0, high=n-1, kth;
    while(low<=high){
        int index=partition(arr, low, high);
        if(index == k-1){
            kth=arr[index];
            break;
        }else if(index<k-1){
            low=index+1;
        }else{
            high=index-1;
        }
    }
    return kth;
}

int main() {
    vector<int> arr={2, 1, 9, 4, 7, 10};
    int k;
    cin>>k;
    int kth = kthmin(arr, k);
    cout<<kth;
    return 0;
}
```
Similarly we change the (k-1)th index to (n-k)th index which will support the kth largest elemnt case using the same code
# Code for kth largest
```c
#include <bits/stdc++.h>
using namespace std;

int partition(vector<int> &arr, int low, int high){
    int pivot=arr[low];
    int i=low;
    int j=high;
    while(i<j){
        while(arr[i]<=pivot && i<=high){
            i++;
        }
         while(arr[j]>pivot && j>=low){
            j--;
        }
        if(i<j){
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[low], arr[j]);
    return j;
}

int kthmin(vector<int> &arr,int k){
    int n=arr.size(), low=0, high=n-1, kth;
    while(low<=high){
        int index=partition(arr, low, high);
        if(index == n-k){
            kth=arr[index];
            break;
        }else if(index<n-k){
            low=index+1;
        }else{
            high=index-1;
        }
    }
    return kth;
}

int main() {
    vector<int> arr={2, 1, 9, 4, 7, 10};
    int k;
    cin>>k;
    int kth = kthmin(arr, k);
    cout<<kth;
    return 0;
}
```
## Time Complexity: O(n)
## Space Complexity: O(1)

It is to be notes that time complexity is O(n) in average case but it can get to O($n^2$) like when the array is sorted and pivot everytime is either the smallest or largest element in that case one half of the array will always have zero elements as a result this results in n recursive calls being made.

