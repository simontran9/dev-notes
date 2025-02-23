# Sorting

## Problem

**Description**
Given an array `array` of elements, sort it in non-decreasing order.

**Input**
An array `array` of elements.

**Output**
- If the sorting is in-place, the original `array` should be modified so that its elements are sorted in non-decreasing order.
- If the sorting is not in-place, return a new array that is a sorted version of `array`, leaving the original unchanged.

## Bubble sort

**Idea**

**Time complexity** 
Worst-case $O(n^2)$

**Properties**
- Stable
- In-place

**Pseudocode**
```
func bubble_sort(array: Array[Int]) -> Void {
    swapped: Bool = False;

    for i in 0..array.len() - 1 {
        for j in 0..(array.len() - i - 1) {
            if array[j] > array[j + 1] {
                array[j], array[j + 1] = array[j + 1], array[j];
                swapped = True;
            }
        }

        if not swapped {
            break;
        }
    }
}
```

## Selection sort

**Idea**
1. Find the minimum element in the remaining unsorted part of the list
2. Swap the found minimum with the current element
3. Repeat until sorted

**Time complexity**
Worst-case $O(n^2)$

**Properties**
- Not stable
- In-place

**Pseudocode**
```
func selection_sort(array: Array[Int]) -> Void {
	for i in 0..(array.len() - 1) {
		var min_index: Int = i;
		for j in (i + 1)..array.len() {
			if array[j] < array[min_index] {
				min = j;
			}
		}
		if not min_index = i {
			array[min_index], array[i] = array[i], array[min_index];
		}
	}
}
```

## Insertion sort

**Idea**

![[Pasted image 20250216060209.png|500]]

**Time complexity**
Worst-case $O(n^2)$ 

**Properties**
- Stable
- In-place

**Pseudocode**
```
func insertion_sort(array: Array[Int]) -> Void {
	for i in 1..array.len() {
		current: Int = array[i];
		j: Int = i - 1;
		while j >= 0 and array[j] > current {
			array[j + 1] = array[j];
			j -= 1;
		}
		array[j + 1] = current;
	}
}
```

## Merge sort

**Idea**
1. Split $A$ into two subarrays $A_L$ and $A_R$ that are roughly half as big
2. Recursively sort $A_L$ and $A_R$
3. After $A_L$ and $A_R$ have been sorted, use merge them into a single sorted array
![[Pasted image 20250216155742.png|500]]

**Time complexity**
Worst-case $O(n \log n)$ 

**Properties**
- Stable
- Not in-place

**Pseudocode**
```
func merge_sort(array: Array[Int]) -> Array[Int] {
    if array.len() <= 1 {
        return array;
    }

    mid: Int = array.len() / 2;
    // TODO?
    left: Array[Int] = array[0..mid];
    right: Array[Int] = array[mid..array.len()];

    left = merge_sort(left);
    right = merge_sort(right);

    return merge(left, right);
}

func merge(left: Array[Int], right: Array[Int]) -> Array[Int] {
    left_index: Int = 0;
    right_index: Int = 0;
    merged: ArrayList<Int> = ArrayList::new();

    while left_index < left.len() and right_index < right.len() {
        if left[left_index] < right[right_index] {
            merged.add_last(left[left_index]);
            left_index += 1;
        } else {
            merged.add_last(right[right_index]);
            right_index += 1;
        }
    }

    while left_index < left.len() {
        merged.add_last(left[left_index]);
        left_index += 1;
    }
    while right_index < right.len() {
        merged.add_last(right[right_index]);
        right_index += 1;
    }

    return merged;
}
```

## Quick sort

**Idea**

**Time complexity**
- Average-case: $O(n \log n)$
- Worst-case: $O(n^2)$

**Properties**
- Not stable
- In-place

**Pseudocode**
```
func quick_sort(array: Array[Int], low: Int, high: Int) -> Void {
	if low >= high { return }
	pivot: Int = lomuto_partition(array, low, high);
	quick_sort(array, low, pivot - 1);
	quick_sort(array, pivot + 1, high);
}

func lomuto_partition(array: Array[Int], low: Int, high: Int) -> Int {
    i: Int = low - 1;
    pivot: Int = array[high];

    for j in low..high {
        if array[j] < pivot {
            i += 1;
            array[i], array[j] = array[j], array[i];
        }
    }

    i += 1;
    array[i], array[high] = array[high], array[i];

    return i;
}
```

## Heap sort

**Idea**
1. Insert all elements of an input array into a heap priority queue
2. From the last element to the first element in the input array, set at every iteration into the input array the top element of the heap priority queue

**Time complexity**
Worst-case $O(n \log n)$

**Properties**
- Not stable
- In-place

**Pseudocode**
```
func heap_priority_queue_sort(array: Array[Int]) -> Void {
	pq: MaxHeapPriorityQueue<Int> = MaxHeapPriorityQueue::from(array);
	for i in (0..pq.len()).rev() {
		array[i] = pq.remove_top();
	}
}
```

