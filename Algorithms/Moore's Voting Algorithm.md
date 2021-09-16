### Moore's Voting Algorithm

This algorithm is used to find a majority element in a given array of elements. A majority element is an element whose **frequency > (total_number_of_elements/2)**.

Here is a great video explanation for the same: [Moore's Voting Algorithm](https://www.youtube.com/watch?v=n5QY3x_GNDg)

Here is a leetcode problem that asks you to apply the same: [LeetCode Problem](https://leetcode.com/problems/majority-element/)

I have coded it down below. You can take a look at the code, copy it and try to give it different inputs to test it.

```C++
#include <bits/stdc++.h>
using namespace std;

void moore(int arr[], int n){
    int candidate_key = arr[0], count = 1;

    for(int i = 1; i < n; ++i){
        
        if(arr[i] == candidate_key){
            count++;
        } else {
            candidate_key = arr[i];
            --count;
        }

        if(count == 0) ++count;
    }

    int rqrd = floor(n/2);
    int candidate_key_count = 0;

    for(int i = 0; i < n; ++i)
        if(arr[i] == candidate_key) 
            ++candidate_key_count;

    if(candidate_key_count > rqrd)
        cout << "Majority Element: " << candidate_key;
    else 
        cout << "No majority element present";
}

int main(){
    int n = 0;
    cin >> n;
    int arr[n];
    for(int i = 0; i < n; ++i)
        cin >> arr[i];
    moore(arr, n);
    return 0;
}
```