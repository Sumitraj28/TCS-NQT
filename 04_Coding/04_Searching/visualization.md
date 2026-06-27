# Searching — Visualization

## Diagram 1 — Binary Search Trace

```mermaid
flowchart TD
    Start(["Search for target=7 in arr=[1,3,5,7,9,11,13]  lo=0 hi=6"])
    Start --> S1["mid=3  arr[3]=7  == target  ✓  FOUND at index 3"]

    Start2(["Search for target=6 in arr=[1,3,5,7,9,11,13]  lo=0 hi=6"])
    Start2 --> S2a["mid=3  arr[3]=7  > target  hi=2"]
    S2a --> S2b["lo=0 hi=2  mid=1  arr[1]=3  < target  lo=2"]
    S2b --> S2c["lo=2 hi=2  mid=2  arr[2]=5  < target  lo=3"]
    S2c --> S2d["lo=3 > hi=2  → EXIT  NOT FOUND  return -1"]

    style S1 fill:#2ecc71,color:#fff
    style S2d fill:#e74c3c,color:#fff
```

---

## Diagram 2 — Lower Bound vs Upper Bound

```mermaid
flowchart LR
    subgraph arr["arr = [1, 3, 3, 3, 5, 7]  (indices 0-5)"]
        direction LR
        A0["1\ni=0"] --- A1["3\ni=1"] --- A2["3\ni=2"] --- A3["3\ni=3"] --- A4["5\ni=4"] --- A5["7\ni=5"]
    end

    LB["lowerBound(arr, 3) = 1\nFirst index where arr[i] >= 3"]
    UB["upperBound(arr, 3) = 4\nFirst index where arr[i] > 3"]
    CNT["count(3) = 4 - 1 = 3"]

    arr --> LB
    arr --> UB
    LB --> CNT
    UB --> CNT

    style LB fill:#3498db,color:#fff
    style UB fill:#9b59b6,color:#fff
    style CNT fill:#2ecc71,color:#fff
```

---

## Diagram 3 — First vs Last Occurrence Search

```mermaid
flowchart TD
    subgraph arr2["arr = [2, 4, 4, 4, 7, 9]  Find first and last of 4"]
        direction LR
    end

    subgraph firstOcc["First Occurrence"]
        F1["lo=0 hi=5  mid=2  arr[2]=4 == target\n  result=2  hi=mid-1=1"]
        F2["lo=0 hi=1  mid=0  arr[0]=2 < target\n  lo=mid+1=1"]
        F3["lo=1 hi=1  mid=1  arr[1]=4 == target\n  result=1  hi=mid-1=0"]
        F4["lo=1 > hi=0 → DONE  first=1"]
        F1 --> F2 --> F3 --> F4
    end

    subgraph lastOcc["Last Occurrence"]
        L1["lo=0 hi=5  mid=2  arr[2]=4 == target\n  result=2  lo=mid+1=3"]
        L2["lo=3 hi=5  mid=4  arr[4]=7 > target\n  hi=mid-1=3"]
        L3["lo=3 hi=3  mid=3  arr[3]=4 == target\n  result=3  lo=mid+1=4"]
        L4["lo=4 > hi=3 → DONE  last=3"]
        L1 --> L2 --> L3 --> L4
    end

    style F4 fill:#2ecc71,color:#fff
    style L4 fill:#2ecc71,color:#fff
```

---

## Diagram 4 — Binary Search on Answer Space (First Bad Version)

```mermaid
flowchart TD
    Problem["Versions 1..10. Version 4 is first bad.\nisBad(v): false for 1,2,3; true for 4..10"]
    Problem --> S1["lo=1 hi=10  mid=5  isBad(5)=true  hi=5"]
    S1 --> S2["lo=1 hi=5   mid=3  isBad(3)=false lo=4"]
    S2 --> S3["lo=4 hi=5   mid=4  isBad(4)=true  hi=4"]
    S3 --> S4["lo=4 hi=4   lo==hi → DONE  return 4"]

    style S4 fill:#2ecc71,color:#fff
```

---

## Diagram 5 — Find Peak Element

```mermaid
flowchart TD
    Start5(["nums = [1,2,3,1]  Find peak\nlo=0  hi=3"])
    Start5 --> P1["mid=1  nums[1]=2 < nums[2]=3\n  → peak on right  lo=2"]
    P1 --> P2["lo=2 hi=3  mid=2  nums[2]=3 >= nums[3]=1\n  → peak at mid or left  hi=2"]
    P2 --> P3["lo=2 == hi=2  → return 2  (nums[2]=3 is peak)"]
    style P3 fill:#2ecc71,color:#fff
```
