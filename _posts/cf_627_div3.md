# cf_627_div3

[contest_link](https://codeforces.com/contest/1324)

1. [TOC]
{:toc}


[TOC]

## A *easy-*

### *solution:*

显然同奇偶才能成功。

### *code:*

```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 110
int a[N], n;
void init(){
    scanf("%d", &n);
    for(int i = 1; i <= n; i++) scanf("%d", &a[i]);
    return ;
}
void solve(){
    int x = 0, y = 0;
    for(int i = 1; i <= n; i++){
        if(a[i] % 2 == 0) ++x;
        else ++y;
    }
    if(x > 0 && y > 0) printf("NO\n");
    else printf("YES\n");
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

## B *easy-*

### *solution:*

题意为判断一个数字串中是否有长度不少于3的回文子串存在（不要求连续）
对于$a_i$，若在$a_1 \sim a_{i-2}$中存在与$a_i$相等的，那么一定可以构造出长度 $\geq$ 3的回文串。

### *code:*

```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 5050
int a[N], n, b[N], t[N];
void init(){
    cin>>n;
    for(int i = 1; i <= n; i++) scanf("%d", &a[i]);
    return ;
}
void solve(){
    memset(t, 0, sizeof(t));
    t[a[1]]++;
    for(int i = 3; i <= n; i++){
        if(t[a[i]] > 0){
            printf("YES\n"); return ;
        }
        ++t[a[i - 1]];
    }
    printf("NO\n");
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

## C *easy-*

### *solution:*

题意为青蛙要从0跳到n+1，$a_1$至$a_n$为L或R，在L上只能向左跳，在R上只能向右跳。
问至少要多大步长。
将0和n+1都看作R，求出最大的两个相邻R的距离即可。
WA两次是因为把n和s一起定义，搞成了char qaqaq...

### *code:*

```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 500050
char s[N];
int n;
void solve(){
    scanf("%s", s + 1);
    n = strlen(s + 1);
    s[0] = 'R'; s[n + 1] = 'R';
    int last = 0, ans = 0;
    for(int i = 1; i <= n + 1; i++){
        if(s[i] == 'R'){
            if(ans < i - last) ans = i - last;
            last = i;
        }
    }
    printf("%d\n", ans);
    return ;
}
int main(){
    int T;
    cin>>T;
    while(T--){
        solve();
    }
    
    return 0;
}
```

## D *easy*

### *solution:*

题意为对于数组a和b，找出(i,j)，使之满足$a_i + a_j > b_i + b_j$ (i < j)
$\Rightarrow (a_i - b_i) + (a_j - b_j) > 0$
设$c_i = a_i - b_i$
对$c_i$排序，卡住$c_i > 0$的边界，分类讨论扫一遍即可计算出结果。

### *code:*

```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 200020
typedef long long LL;
int a[N], b[N], c[N], n;
LL ans = 0;
/*
7
1 1 2 4 5 6 7
2 1 2 3 4 5 5
*/
void solve(){
    sort(c + 1, c + 1 + n);
    if(c[n] <= 0){
        printf("0\n"); return ;
    }
    if(c[1] > 0){
        ans = ((LL)n) * ((LL)n - 1) / 2LL;
        printf("%lld\n", ans); return ;
    }
    int d = 1;
    while(c[d] <=0) ++d;
    --d;
    // cout<<d<<endl;
    ans = ((LL)n - d) * ((LL)n - d - 1) / 2LL;
    // cout<<ans<<endl;
    int x = n;
    for(int i = 1; i <= d; i++){
        while(c[i] + c[x] > 0) --x;
        ++x;
        if(x > n || c[i] + c[x] <= 0){
            x = n;
            continue;
        }
        ans += (n - x + 1);
    }
    printf("%lld\n", ans);
    return ;
}
int main(){
    scanf("%d", &n);
    for(int i = 1; i <= n; i++) scanf("%d", &a[i]);
    for(int i = 1; i <= n; i++) scanf("%d", &b[i]), c[i] = a[i] - b[i];
    solve();
    return 0;
}
```
## E *easy+*

### *solution:*

DP：
f[i][j]表示第i天第j时刻，是否可以成为入睡时间。
若不可以，f[i][j] = -1
若可以，则f[i][j]记录到此情况下，从第一天到现在，入睡时间处于[l,r]区间内的最多次数，$i \in [1,n], j \in [0, h)$。

### *code:*

```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 2020
int f[N][N], n, h, a[N], l, r;

void solve(){
    memset(f, -1, sizeof(f));
    f[1][a[1]] = f[1][a[1] - 1] = 0;
    if(a[1] >= l && a[1] <= r) f[1][a[1]] = 1;
    if(a[1] - 1 >= l && a[1] - 1 <= r) f[1][a[1] - 1] = 1;
    for(int i = 2; i <= n; i++){
        for(int j = 0; j < h; j++){
            int last1 = (j + h - a[i]) % h;
            int last2 = (j + h - (a[i] - 1)) % h;
            if(f[i - 1][last1] != -1 || f[i - 1][last2] != -1){
                f[i][j] = max(f[i - 1][last1], f[i - 1][last2]);
                if(j >= l && j <= r) f[i][j]++;
            }
        }
    }
    int ans = 0;
    for(int i = 0; i < h; i++) ans = max(ans, f[n][i]);
    printf("%d\n", ans);
    return ;
}
int main(){
    cin>>n>>h>>l>>r;
    for(int i = 1; i <= n; i++) scanf("%d", &a[i]);
    solve();
    return 0;
}
```