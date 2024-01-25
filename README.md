Arrays are Disjoint or not in C++
Here, in this page we will discuss the program to check whether the two arrays are disjoint or not in C++ programming language. Arrays are disjoint if the don’t contain any common value.

Arrays are disjoint or not in C++
Here, we will discuss the following methods to check whether the given integer arrays are disjoint or not

Method 1 : Using Naive approach.
Method 2 : Using sorting and hashing
Method 3 : Using Set
Method 1 :
Run a loop from index 0 to n
Run a nested loop from 0 to m
Check if (arr1[i]==arr2[j]) return 0.
Otherwise, return 1.
Time and Space Complexity :
Time Complexity : O(n2)
Space Complexity : O(1)
Method 1 : Code in C++
#include<bits/stdc++.h>
using namespace std;

int disjoint(int arr1[], int arr2[], int n, int m){
    
    for(int i=0; i<n; i++){
        for(int j=0; j<m; j++){
            if(arr1[i]==arr2[j]){
                return 0;   
            }
        }
    }
    return 1;
}

int main(){
    
    int arr1[] = {10, 20, 30, 67};
    int arr2[] = {20, 90, 80, 77, 23};
    int n = sizeof(arr1)/sizeof(arr1[0]);
    int m = sizeof(arr2)/sizeof(arr2[0]);
    
    if(disjoint(arr1, arr2, n, m))
    cout<<"Yes";
    
    else cout<<"No";
    
}
Output :
No
Related Pages
Find all Symmetric pairs in an array

Find maximum product sub-array in a given array

Determine Array is a subset of another array or not

Determine can all numbers of an array be made equal

Finding Minimum sum of absolute difference of given array

Method 2 :
In this method first sort both the given integer arrays, then using the merge process we compare the elements in both arrays.

Method 2 : Code in C++
#include<bits/stdc++.h>
using namespace std;

int disjoint(int arr1[], int arr2[], int n, int m){
    
    sort(arr1, arr1+n);
    sort(arr2, arr2+m);
    
    // Check for same elements using merge like process
    int i = 0, j = 0;
    while (i < m && j < n)
    {
        if (arr1[i] < arr2[j])
            i++;
        else if (arr2[j] < arr1[i])
            j++;
        else /* if set1[i] == set2[j] */
            return 0;
    }
 
    return 1;
}

int main(){
    
    int arr1[] = {10, 20, 30, 67};
    int arr2[] = {20, 90, 80, 77, 23};
    int n = sizeof(arr1)/sizeof(arr1[0]);
    int m = sizeof(arr2)/sizeof(arr2[0]);
    
    if(disjoint(arr1, arr2, n, m))
    cout<<"Yes";
    
    else cout<<"No";
    
}
Output :
No
Method 3 :
In this method we use the concept of set.

Iterate through the first array and store every element in the set.
Iterate through the second array and check if any element is present in the set.
If present, then returns false, else ignore the element. 
If all elements of the second array are not present in the set, return true.
While loop in C
Method 3 : Code in C++
#include<bits/stdc++.h>
using namespace std;

int disjoint(int arr1[], int arr2[], int n, int m){
    
    set st;
 
    // Traverse the first set and store its elements in hash
    for (int i = 0; i < n; i++)
        st.insert(arr1[i]);
 
    // Traverse the second set and check if any element of it
    // is already in hash or not.
    for (int i = 0; i < m; i++)
        if (st.find(arr2[i]) != st.end())
            return 0;
 
    return 1;
}

int main(){
    
    int arr1[] = {10, 20, 30, 67};
    int arr2[] = {20, 90, 80, 77, 23};
    int n = sizeof(arr1)/sizeof(arr1[0]);
    int m = sizeof(arr2)/sizeof(arr2[0]);
    
    if(disjoint(arr1, arr2, n, m))
    cout<<"Yes";
    
    else cout<<"No";
    
}
Output :
No
