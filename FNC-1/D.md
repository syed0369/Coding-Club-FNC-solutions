Problem Statement: [D - Crushed Apples and a Balance Scale](https://vjudge.net/contest/672020#problem/D)


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
