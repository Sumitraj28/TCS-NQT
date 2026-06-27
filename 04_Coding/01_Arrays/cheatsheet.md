# Arrays — Cheat Sheet (One Screen)

## Pattern → Template (C++)

```cpp
// KADANE'S (max subarray)
int max = a[0], cur = a[0];
for(int i=1; i<n; i++){ cur=std::max(a[i], cur+a[i]); max=std::max(max, cur); }

// PREFIX SUM (build)
std::vector<long long> pre(n+1, 0);
for(int i=0; i<n; i++) pre[i+1] = pre[i] + a[i];
// sum(l,r) = pre[r+1] - pre[l]

// SLIDING WINDOW — fixed k
int ws=0; for(int i=0; i<k; i++) ws+=a[i]; int mx=ws;
for(int i=k; i<n; i++){ ws+=a[i]-a[i-k]; mx=std::max(mx, ws); }

// SLIDING WINDOW — variable (min len, sum>=target)
int l=0, ws=0, minL=n+1;
for(int r=0; r<n; r++){ ws+=a[r]; while(ws>=t){ minL=std::min(minL, r-l+1); ws-=a[l++]; } }

// TWO POINTER — pair sum (sorted)
int l=0, r=n-1;
while(l<r){ int s=a[l]+a[r]; if(s==t) found; else if(s<t) l++; else r--; }

// TWO POINTER — move zeroes
int p=0; for(int x:a) if(x!=0) a[p++]=x; while(p<n) a[p++]=0;

// SUBARRAY SUM = k (prefix + map)
std::unordered_map<int, int> m; m[0]=1;
int sum=0, cnt=0;
for(int x:a){ sum+=x; if(m.count(sum-k)) cnt+=m[sum-k]; m[sum]++; }

// SIGN MARKING (find missing)
for(int x:a){ int i=std::abs(x)-1; if(a[i]>0) a[i]=-a[i]; }
for(int i=0; i<n; i++) if(a[i]>0) /* i+1 is missing */;

// DUTCH NATIONAL FLAG
int lo=0, mi=0, hi=n-1;
while(mi<=hi){
  if(a[mi]==0){ std::swap(a[lo++], a[mi++]); }
  else if(a[mi]==1){ mi++; }
  else{ std::swap(a[mi], a[hi--]); } }

// ROTATE RIGHT by k
k%=n; std::reverse(a.begin(),a.end()); std::reverse(a.begin(),a.begin()+k); std::reverse(a.begin()+k,a.end());

// PRODUCT EXCEPT SELF
std::vector<int> r(n,1);
for(int i=1; i<n; i++) r[i] = r[i-1]*a[i-1];
int rp=1; for(int i=n-1; i>=0; i--){ r[i]*=rp; rp*=a[i]; }
```

## Key Rules

| Rule | Detail |
|------|--------|
| Kadane's init | `nums[0]`, NOT 0 |
| Prefix long | Use `long long` if sum can exceed 2×10⁹ |
| Sign marking | Always `std::abs(num)-1` |
| Dutch flag | `mid` does NOT advance when case==2 |
| Rotation | `k = k % n` first |
| Subarray=k | Count BEFORE put |

## Complexity

| Pattern | T | S |
|---------|---|---|
| Kadane | O(n) | O(1) |
| Prefix | O(n) | O(n) |
| Window | O(n) | O(1) |
| 2-ptr | O(n) | O(1) |
| Hash Map | O(n) | O(n) |
| Sort+2ptr | O(n log n) | O(1) |
```
