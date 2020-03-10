# CodeCraft-20(Div. 2)
[contest_link](https://codeforces.com/contest/1316)

1. [TOC]
{:toc}

## A
```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 1010
int a[N], n, m;
void init(){
    cin>>n>>m;
    for(int i = 1; i <= n; i++) scanf("%d", &a[i]);
    return ;
}
void solve(){
    int s = 0; 
    for(int i = 1; i <= n; i++) s += a[i];
    if(s > m) s = m;
    printf("%d\n", s);
    return ;
}
int main(){
    int T;
    cin>>T;
    while(T--){        
        init();
        solve();
    }
    return 0;
}
```

## B
```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 5050
string s[N];
char c[N];
struct node{
    string s;
    int k;
}a[N];
int n;
bool cmp(node a, node b){
    if(a.s != b.s) return a.s < b.s;
    else return a.k < b.k;
}
void solve(){
    string ss = "";
    for(int k = 1; k <= n; k++){
        if((n - k + 1) % 2 == 0) s[k] = ss;
        else{
            reverse(ss.begin(),ss.end());
            s[k] = ss;
            reverse(ss.begin(),ss.end());
        }
        ss = ss + c[k];
        // cout<<s[k]<<' '<<k << endl;
    }
    string x = "";
    for(int k = n; k >= 1; k--){
        
        x = c[k] + x;
        // cout<<x<<endl;
        s[k] = x + s[k];
        // cout<<s[k]<<' '<<k <<endl;
        a[k].s = s[k]; a[k].k = k;
    }
    sort(a + 1, a + 1 + n, cmp);
    cout<<a[1].s<<endl;
    cout<<a[1].k<<endl;
    return ;
}
int main(){
    int T;
    cin>>T;
    while(T--){
        cin>>n;
        scanf("%s", c + 1);
        solve();
    }
    return 0;
}
```

## C
```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 1000100
int a[N], b[N], p, n, m;
int main(){
    scanf("%d%d%d", &n ,&m, &p);
    int x, y;
    for(int i = 0; i < n; i++){
        scanf("%d", &a[i]);
        if(a[i] % p != 0) x = i;
    }
    for(int i = 0; i < m; i++){
        scanf("%d", &b[i]);
        if(b[i] % p != 0) y = i;
    }
    // cout<<x<<' '<<y<<endl;
    printf("%d\n", x + y);

    return 0;
}
```
