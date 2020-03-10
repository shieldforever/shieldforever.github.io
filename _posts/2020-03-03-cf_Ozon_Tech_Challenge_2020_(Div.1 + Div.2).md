# cf_Ozon_Tech_Challenge_2020_(Div.1 + Div.2)

1. [TOC]
{:toc}

## A
```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 1010
int a[N], b[N], n;
int main(){
    int T;
    cin>>T;
    while(T--){
        scanf("%d", &n);
        for(int i = 1; i <= n; i++)scanf("%d", &a[i]);
        for(int i = 1; i <= n; i++)scanf("%d", &b[i]);
        sort(a + 1, a + 1 + n);
        sort(b + 1, b + 1 + n);
        for(int i = 1; i < n; i++) printf("%d ", a[i]);
        printf("%d\n", a[n]);
        for(int i = 1; i < n; i++) printf("%d ", b[i]);
        printf("%d\n", b[n]);    
    } 
    return 0;
}
```

## B
```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 1010
int n, l[N], r[N];
char s[N];
int c[N], ans[N], k;
void solve(){
    l[0] = 0; r[n + 1] = 0;
    for(int i = 1; i <= n; i++){
        l[i] = l[i - 1];
        if(s[i] == '(') l[i]++;
    }
    for(int i = n; i >= 1; i--){
        r[i] = r[i + 1];
        if(s[i] == ')') r[i]++;
    }
    int f = 0, p = 0;
    for(int i = 1; i <= n - 1; i++){
        if(p < min(l[i], r[i + 1])){
            p = min(l[i], r[i + 1]);
            f = i;
        }
    }
    if(f == 0){
        printf("0\n"); return ;
    }
    printf("1\n%d\n", p * 2);
    int pp = p;
    for(int i = 1; i <= f; i++){
        if(s[i] == '('){
            pp--;
            printf("%d ", i);
            if(pp == 0) break;
        }
    }
    int o = 0;
    for(int i = n; i >= f + 1; i--){
        if(s[i] == ')'){
            p--;
            ans[++o] = i;
            if(p == 0) break;
        }
    }
    for(int i = o; i >= 1; i--){
        if(i != 1) printf("%d ", ans[i]);
        else printf("%d\n", ans[i]);
    }
    return ;
}

int main(){
    scanf("%s", s + 1);
    n = strlen(s + 1);
    solve();
    return 0;
}
```

## C
```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 200200
int n, m;
int a[N];
void init(){
    scanf("%d%d", &n, &m);
    for(int i = 1; i <= n; i++) scanf("%d", &a[i]);
    if(n > m){
        printf("0\n"); return ;
    }
    int ans = 1;
    for(int i = 1; i <= n; i++){
        for(int j = i + 1; j <= n; j++){
            int x = a[i] - a[j];
            if(x == 0){
                printf("0\n"); return ;
            }
            if(x < 0) x *= -1;
            x %= m;
            ans = (ans * x) % m;
        }
    }
    printf("%d\n", ans);
    return ;
}
int main(){
    init();
    return 0;
}
```

## D
```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 3030
struct node{
    int to, next;
}e[N];
int head[N], len = 0, n, m;
int tag[N], vis[N], ans[N], cnt = 0;
int d[N], h[N];
void add_edge(int u, int v){
    e[++len].to = v;
    e[len].next = head[u];
    head[u] = len;
    return ;
}
void init(){
    scanf("%d", &n);
    m = n - 1;
    memset(head, -1, sizeof(head));
    for(int i = 1; i <= m; i++){
        int u, v;
        scanf("%d%d", &u, &v);
        d[u]++; d[v]++;
        add_edge(u, v); add_edge(v, u);
    }
    return ;
}
void tp(){
    queue<int > q;
    for(int i = 1; i <= n; i++){
        if(d[i] == 1){
            q.push(i), vis[i] = 1;
            //cout<<i<<endl;
        }
    }
    h[0] = 0;
    while(!q.empty()){
        int u = q.front(); q.pop();
        h[++h[0]] = u;
        for(int i = head[u]; i != -1; i = e[i].next){
            int v = e[i].to;
            if(d[v] == 1) continue;
            d[v]--;
            if(d[v] == 1){
                q.push(v);
            } 
        }
    }
    return ;
}
bool dfs(int cur, int p){
    if(cur == p) return true;
    vis[cur] = 1;
    for(int i = head[cur]; i != -1; i = e[i].next){
        int v = e[i].to;
        if(!vis[v]){
            vis[v] = 1;
            if(dfs(v, p)){
                tag[v] = 1; return true;
            }
        }
    }
    return false;
}
void solve(){
    ans[0] = 0;
    for(int i = 1; i < n; i += 2){
        printf("? %d %d\n", h[i], h[i + 1]);
        fflush(stdout);
        int x;
        scanf("%d", &x);
        ans[++ans[0]] = x;
        if(x == h[i]){
            //tag[h[i + 1]] = 1;
            memset(vis, 0, sizeof(vis));
            dfs(x, h[i + 1]);
        }
        else if(x == h[i + 1]){
            //tag[h[i]] = 1;
            memset(vis, 0, sizeof(vis));
            dfs(x, h[i]);
        }
        else{
            //cout<<"dsfa"<<endl;
            //for(int o = 1; o <= n; o++) cout<<tag[o]<<' ';
            //cout<<endl;
            //tag[h[i]] = tag[h[i + 1]] = 1;
            memset(vis, 0, sizeof(vis));
            dfs(x, h[i]); 
            //for(int o = 1; o <= n; o++) cout<<tag[o]<<' ';
            //cout<<endl;
            memset(vis, 0, sizeof(vis));
            dfs(x, h[i + 1]);
            //for(int o = 1; o <= n; o++) cout<<tag[o]<<' ';
            //cout<<endl;
        }
    }
    for(int i = 1; i <= ans[0]; i++){
        if(!tag[ans[i]]){
            printf("! %d\n", ans[i]); return ;
        }
    }
    printf("! %d\n", h[n]);
    return ;
}
int main(){
    init();
    tp();
    solve();
    return 0;
}
```

## E
```cpp
#include<bits/stdc++.h>
using namespace std;
#define N 5050
#define Base 5e8
int n, m, a[N];
void solve(){
    cin>>n>>m;
    int cnt = 0;
    for(int i = 1; i <= n - 1; i++) cnt += i / 2;
    if(m > cnt){
        printf("-1\n"); return ;
    }
    cnt = 0;
    int p = 0;
    for(int i = 1; cnt <= m; i++){
        a[i] = i; cnt += i / 2; p = i;
    }
    cnt -= p / 2;
    a[p + 1] = 2 * p + 1 - 2 * (m - cnt);
    int d = 0;
    for(int i = p + 2; i <= n; i++){
        a[i] = Base + d; d += 10001;
    }
    for(int i = 1; i <= n; i++) {
        if(i != n) printf("%d ", a[i]);
        else printf("%d\n", a[i]);
    }
    return ;
}
int main(){
    solve();
    return 0;
}
```
