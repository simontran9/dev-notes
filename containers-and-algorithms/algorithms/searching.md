# Searching

## Problem

**Description**
Given an array `array` and a target element `target`, determine if `target` exists in array. If it does, return its index; otherwise, return `-1`.

**Input**
- An array `array` of elements
- A target element `target` to search for

**Output:**
- The index of target in `array` if found
- `-1` if target is not present in array

## Linear search

**Time complexity**
$O(n)$

**Pseudocode**
```
func linear_search(array: Array[Int], target: Int) -> Int {
    for i in 0..array.len() {
        if array[i] == target {
            return i;
        }
    }
    return -1;
}
```

## Binary search

**Time complexity**
$O(\log n)$

**Pseudocode**
```
func iterative_binary_search(array: Array[Int], target: Int) -> Int {
    low: Int = 0;
    high: Int = array.len() - 1;
    
    while low <= high {
        mid: Int = low + (high - low) / 2;
        if array[mid] == target {
            return mid;
        } else if array[mid] < target {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }

    return -1;
}
```

```
func recursive_binary_search(array: Array[Int], low: Int, high: Int, target: Int) -> Int {
    if low <= high {
        mid: Int = low + (high - low) / 2;
        if array[mid] == target {
            return mid;
        } else if array[mid] < target {
            return recursive_binary_search(array, mid + 1, high, target);
        } else {
            return recursive_binary_search(array, low, mid - 1, target);
        }
    }
    
    return -1;
}
```

