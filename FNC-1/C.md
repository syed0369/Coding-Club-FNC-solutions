Problem Statement: [C - Fixed Points](https://codeforces.com/problemset/problem/347/B)

```cp
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
