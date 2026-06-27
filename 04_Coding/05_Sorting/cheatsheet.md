# Sorting — Cheat Sheet

## Algorithms & Templates (C++)

```cpp
// BUBBLE SORT (optimized)
for(int i=0; i<n-1; i++) {
  bool swapped = false;
  for(int j=0; j<n-1-i; j++) {
    if(a[j] > a[j+1]) { std::swap(a[j], a[j+1]); swapped = true; }
  }
  if(!swapped) break;
}

// SELECTION SORT
for(int i=0; i<n-1; i++) {
  int minIdx = i;
  for(int j=i+1; j<n; j++) { if(a[j] < a[minIdx]) minIdx = j; }
  std::swap(a[i], a[minIdx]);
}

// INSERTION SORT
for(int i=1; i<n; i++) {
  int key = a[i], j = i - 1;
  while(j >= 0 && a[j] > key) { a[j+1] = a[j]; j--; }
  a[j+1] = key;
}

// DUTCH NATIONAL FLAG (0s, 1s, 2s sort)
int lo=0, mi=0, hi=n-1;
while(mi<=hi) {
  if(a[mi]==0) { std::swap(a[lo++], a[mi++]); }
  else if(a[mi]==1) { mi++; }
  else { std::swap(a[mi], a[hi--]); }
}
```

## C++ STL Sorting Shortcuts

```cpp
#include <algorithm>

std::sort(v.begin(), v.end());                         // Ascending
std::sort(v.rbegin(), v.rend());                       // Descending
std::stable_sort(v.begin(), v.end());                  // Stable Sort

// Kth smallest element in O(N) average time
std::nth_element(v.begin(), v.begin() + k, v.end());
int kthSmallest = v[k];

// Custom Sort (Lambda)
std::sort(v.begin(), v.end(), [](const auto& a, const auto& b){
  return a[0] < b[0]; // Sort by first column ascending
});
```

## Complexity Summary

| Algorithm | Worst Time | Space | Stable |
|-----------|------------|-------|--------|
| Bubble | O(n²) | O(1) | Yes |
| Selection | O(n²) | O(1) | No |
| Insertion | O(n²) | O(1) | Yes |
| Merge | O(n log n) | O(n) | Yes |
| Quick | O(n²) | O(log n) | No |
| Heap | O(n log n) | O(1) | No |
| std::sort | O(n log n) | O(log n) | No |
| std::stable_sort | O(n log n) | O(n) | Yes |
```
