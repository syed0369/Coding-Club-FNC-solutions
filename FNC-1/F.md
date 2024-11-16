## Proble Statement
[F - Sum of Goodness](https://www.codechef.com/problems/SEQGOODNESS?tab=statement)

## Solution
Find the number of times each number contributes to the goodness. Let `i` be the position of the muber in the sorted array, then only if atleast `arr[i] - 1` elements are there before `i`, it contributes to the goodness. The numbers in front can be arrange in <i><sup>i</sup>C<sub>arr[i] - 1</sub></i> ways, the numbers after `i` can be selected or not i.e. <i>2<sup>n - i - i</sup></i> number of ways.

## Code
```cpp
#include <bits/stdc++.h>
#define MOD (int)(1e9 + 7)
using namespace std;


long long nCr(int n, int r, vector<long long>& fac, vector<long long>& invfac) {
    return ((fac[n] * invfac[r]) % MOD) * invfac[n - r] % MOD;
}

long long power(long long a, int b) {
    long long ans;
    ans = 1;
    while(b) {
        if(b & 1)
            ans = (ans * a) % MOD;
        a = (a * a) % MOD;
        b >>= 1;
    }
    return ans;
}

void solve(vector<long long>& fac, vector<long long>& invfac) {
    int i, n;
    long long sum, total_sum;
    cin >> n;
    vector<int> arr(n);
    
    for(i = 0; i < n; i++) {
        cin >> arr[i];
    }
    sort(arr.begin(), arr.end());
    total_sum = 0;
    
    for(i = 0; i < n; i++) {
        if(arr[i] - 1 <= i) {
            sum = nCr(i, arr[i] - 1, fac, invfac);
            sum = sum * power(2, n - i - 1) % MOD;
            total_sum = (total_sum + sum) % MOD;
        }
    }
    cout << total_sum << "\n";
}


int main() {
	
	int i, t;
	vector<long long> fac(1000000 + 1), invfac(1000000 + 1);
	cin >> t;
	fac[0] = invfac[0] = 1;
	for(i = 1; i < 1000000 + 1; i++) {
	    fac[i] = (fac[i - 1] * i) % MOD;
	}
	for(i = 1; i < 1000000 + 1; i++) {
	    invfac[i] = power(fac[i], MOD - 2);
	}
	while(t--) {
	    solve(fac, invfac);
	}
	return 0;
}
```

## Analysis
Time Complexity: For each test case ~ <i>O(nlog(n))</i>
<br>
Space Complexity: <i>O(n)</i>
