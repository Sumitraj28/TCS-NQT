# Searching — Cheat Sheet

## Binary Search Templates (C++)

```cpp
// EXACT MATCH
int lo=0, hi=n-1;
while(lo<=hi){ int mid=lo+(hi-lo)/2;
  if(a[mid]==t) return mid;
  else if(a[mid]<t) lo=mid+1; else hi=mid-1; }
return -1;

// LOWER BOUND (first i: a[i]>=x)   hi=n  loop lo<hi
int lo=0, hi=n;
while(lo<hi){ int mid=lo+(hi-lo)/2;
  if(a[mid]<x) lo=mid+1; else hi=mid; }
return lo;

// UPPER BOUND (first i: a[i]>x)   hi=n  loop lo<hi
int lo=0, hi=n;
while(lo<hi){ int mid=lo+(hi-lo)/2;
  if(a[mid]<=x) lo=mid+1; else hi=mid; }
return lo;

// FIRST OCCURRENCE
int lo=0,hi=n-1,res=-1;
while(lo<=hi){ int mid=lo+(hi-lo)/2;
  if(a[mid]==t){res=mid;hi=mid-1;}
  else if(a[mid]<t)lo=mid+1; else hi=mid-1; }
return res;

// LAST OCCURRENCE
int lo=0,hi=n-1,res=-1;
while(lo<=hi){ int mid=lo+(hi-lo)/2;
  if(a[mid]==t){res=mid;lo=mid+1;}
  else if(a[mid]<t)lo=mid+1; else hi=mid-1; }
return res;

// PEAK ELEMENT
int lo=0,hi=n-1;
while(lo<hi){ int mid=lo+(hi-lo)/2;
  if(a[mid]<a[mid+1]) lo=mid+1; else hi=mid; }
return lo;

// ANSWER SPACE (minimize first feasible answer)
int lo=minAns,hi=maxAns;
while(lo<hi){ int mid=lo+(hi-lo)/2;
  if(feasible(mid)) hi=mid; else lo=mid+1; }
return lo;
```

## C++ STL equivalent
```cpp
#include <algorithm>

std::binary_search(a.begin(), a.end(), x); // returns bool
std::lower_bound(a.begin(), a.end(), x);    // iterator to first >= x
std::upper_bound(a.begin(), a.end(), x);    // iterator to first > x
```

## Rules

| Rule | Exact | Bound/Peak |
|------|-------|-----------|
| hi init | `n-1` | `n` (bound) or `n-1` (peak) |
| loop | `lo<=hi` | `lo<hi` |
| on match (bounds) | return | `hi=mid` or `lo=mid+1` |
| mid formula | `lo+(hi-lo)/2` always | same |
