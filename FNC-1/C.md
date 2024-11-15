## Problem Statement
[C - Fixed Points](https://codeforces.com/problemset/problem/347/B)

## Solution
The permutation should be sorted in ascending order. Check if a cycle of length 2 isformed between any two numbers, if yes we can swap these two and increase `count` by 2 else we can only adjust 1 element's position so increase by 1.

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int i, n, count, flag;
    cin >> n;
    vector<int> arr(n);
    count = 0;
    for(i = 0; i < n; i++) 
        cin >> arr[i];
        
    flag = 0;
    for(i = 0; i < n; i++) {
        if(arr[i] == i)
            count++;
        if(arr[i] < i) {
            if(arr[arr[i]] == i) {
                flag = 1;
            }
        }
    }
    cout << count + ((n - count >= 2)? ((flag)? 2 : 1) : 0) << "\n";
}

int main()
{
    int t;
    t = 1;
    while(t--) {
        solve();
    }
    return 0;
}
```

## Analysis
Time Complexity: For each test case <i>O(n)</i>
<br>
Space COmplexity: <i>O(n)</i>
