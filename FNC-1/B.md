## Problem Statement
[B - Everyone Loves Tres](https://codeforces.com/problemset/problem/2035/B)

## Solution
Since it should be divisible by 33 and 66, finding the lcm, we get 66 == 2 * 3 * 11. So the number should be divisible by 2, 3 and 11. 
<br>
+ Divisibility by 2: should end with even. Only possible in this case is 6.
+ Divisibility by 3: Always divisible as any combination of 3 and 6 gives a sum divisible by 3
+ Divisibility by 11: alternate difference and sum of digits should be a multiple of 11. For even numbers it can be of the form (33)*66. For odd numbers, `n = 3` there is no number possible ending with 6. For `n = 5` it can be of the form 36366 as 3 - 6 + 3 - 6 + 6 = 0. Hence for odd numbers it will be of the form (33)*36366.

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
Time Complexity: For each test case <i>O(n)</i>
<br>
Space Complexity: <i>O(1)</i>
