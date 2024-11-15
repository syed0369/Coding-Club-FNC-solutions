## Problem Statement
[E - Cat, Fox and the Lonely Array](https://codeforces.com/contest/1973/problem/B)

## Solution
To ensure that each segment has the same OR value, there should be atleast one number with a particular bit set, the maximum distance of two such numbers with a particular bit can be found which will be the answer. `bits` array can be used to store the most recent position of the i<sup>th</sup> bit set.
<br>
Considering a case where 0 might appear at end of array, the ORed vaue of all elements is placed at end to ensure that the 0s are also considered in calculating the max_length.

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int i, n, x;
    int max_length, bit_pos;
    cin >> n;
    vector<int> arr(n + 1);
    vector<int> bits(20, 0);
    for(i = 0; i < n; i++) {
        cin >> arr[i];
        arr[n] |= arr[i];
    }
    max_length = 1;
    for(i = 0; i < n + 1; i++) {
        x = arr[i];
        bit_pos = 0;
        while(x) {
            if(x & 1) {
                max_length = max(max_length, i + 1 - bits[bit_pos]);
                bits[bit_pos] = i + 1;
            }
            x >>= 1;
            bit_pos++;
        }
    }
    cout << max_length  << "\n";
}


int main()
{
    int t;
    cin >> t;
    while(t--) {
        solve();
    }
    return 0;
}

```

## Analysis
Time Complexity: For each test case <i>O(nlog(A))</i> where A is max element in `arr`.
<br>
Space Complexity: <i>O(n)</i>
