Problem Statement: [D - Crushed Apples and a Balance Scale](https://www.codechef.com/problems/APP_BAL_SCA?tab=statement)
<br>
We can divide the whole pile of apples into two equal halves, each half into quarter of the whole pile and so on. This can be done until the number is even. Once we get an odd number, it denotes the smallest unit of measurement possible. We can pile up any number of subpiles of apples i.e. any multiple of redused `m`. 
<br>
If the number of apples needed is a multiple of redused `m`, it is possible to find `n` apples. Check for base case if `n > m`.

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    long long m, n;
	cin >> m >> n;
	if(n > m) {
	    cout << "NO\n";
	    return;
	}
	while(!(m & 1)) {
	    m >>= 1;
	}
	if(n % m == 0)
	    cout << "YES\n";
	else
	    cout << "NO\n";
}


int main() {
	int t;
	cin >> t;
	while(t--) {
	    solve();
	}
	return 0;
}

```
