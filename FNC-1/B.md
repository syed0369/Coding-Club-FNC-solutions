## Problem Statement
[B - Everyone Loves Tres](https://codeforces.com/problemset/problem/2035/B)

## Solution
Since it should be divisible by 33 and 66, finding the lcm, we get 66 == 2 * 3 * 11. So the number should be divisible by 2, 3 and 11. 
<br>
+ Divisibility by 2: should end with even. Only possible in this case is 6.
+ Divisibility by 3: Always divisible as any combination of 3 and 6 gives a sum divisible by 3
+ Divisibility by 11: for even length numbers, it should end with 66 and prepended by `n - 2` number of 3s, for odd length numbers, it should end with 36366 prepended by `n - 5` 3s.

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    
    int i, n;
    string s;
    cin >> n;
    if(n == 1 || n == 3) {
        cout << "-1\n";
        return;
    }
    else if(n & 1) {
        s = "36366";
        for(i = 0; i < n - 5; i++) {
            s = "3" + s;
        }
    }
    else {
        s = "66";
        for(i = 0; i < n - 2; i++) {
            s = "3" + s;
        }
    }
    cout << s << "\n";
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
Time Complexity: For each test case <i>O(1)</i>
<br>
Space Complexity: <i>O(1)</i>
