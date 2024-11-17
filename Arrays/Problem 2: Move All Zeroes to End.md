# Problem: Move All Zeroes to End

## Problem Statement

Given an array `arr[]`, push all the zeros in the array to the **end** while maintaining the order of the non-zero elements. Perform this operation **in place**.

---

### Examples

1. **Input**: `arr[] = [1, 2, 0, 4, 3, 0, 5, 0]`  
   **Output**: `[1, 2, 4, 3, 5, 0, 0, 0]`  
   **Explanation**: Three `0`s are moved to the end while maintaining the order of the other elements.

2. **Input**: `arr[] = [10, 20, 30]`  
   **Output**: `[10, 20, 30]`  
   **Explanation**: No zeros, so no change.

3. **Input**: `arr[] = [0, 0]`  
   **Output**: `[0, 0]`  
   **Explanation**: All elements are zeros, so no change.

---

## Constraints
- 1 ≤ arr.length ≤ 10⁵  
- 0 ≤ arr[i] ≤ 10⁵



---



## Approach 1: Brute Force with Nested Loops
### Code:
```java
class Solution {
    void pushZerosToEnd(int[] arr) {
        // Iterate over each element of the array
        for (int i = 0; i < arr.length - 1; i++) {
            if (arr[i] == 0) {
                int j = i + 1;
                // Find the next non-zero element
                while (j < arr.length && arr[j] == 0) {
                    j++;
                }
                if (j < arr.length) {
                    // Swap zero with the next non-zero element
                    int temp = arr[i];
                    arr[i] = arr[j];
                    arr[j] = temp;
                }
            }
        }
    }
}

```
---
## Approach 2: Single Pass
### Code:
```java
class Solution {
    void pushZerosToEnd(int[] arr) {
        int count = 0; // Keeps track of the position to place non-zero elements

        // Traverse the array
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] != 0) {
                // Swap current non-zero with the count index
                swap(arr, i, count);
                count++;
            }
        }
    }

    void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}

```
---
| **Approach**               | **Time Complexity** | **Space Complexity** |
|----------------------------|----------------------|-----------------------|
| Brute Force (Nested Loops) | O(n²)               | O(1)                  |
| Optimized Single Pass       | O(n)                | O(1)                  |
