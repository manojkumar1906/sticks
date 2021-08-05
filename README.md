#include<bits/stdc++.h>
#define f first
#define s second
#define rep(i, a, b) for(long long i = a; i < b; i++)


using namespace std;
using ll = long long;
using pll = pair<ll, ll>;
using vll = vector<ll>;

int main() {
    cin.sync_with_stdio(0);
    int t, n;
    cin >> t;

    while(t--) {
        cin >> n;
        map<int, int> hm;

        int num;
        while(n--) {
            cin >> num;
            if(hm.find(num) != hm.end()) {
                hm[num]++;
            }
            else {
                hm[num] = 1;
            }
        }

        auto it = hm.rbegin();
        bool found_1 = false, found_2 = false;
        ll dim_1, dim_2;
        while(it != hm.rend()) {
            // cout << it -> first << "->";
            if(it -> second > 1) {
                if(found_1) {
                    found_2 = true;
                    dim_2 = it -> first;
                    break;
                }
                found_1 = true;
                dim_1 = it -> first;
                if(it -> second > 3) {
                    dim_2 = it -> first;
                    found_2 = true;
                    break;
                }
            }
            it++;
        }
        if(found_1 and found_2) {
            cout << dim_1 * dim_2 << endl;
        }
        else {
            cout << "-1" << endl;
        }
    }

    return 0;
}
