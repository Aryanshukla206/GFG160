# Next Permutation

## Problem Statement

Given an array of integers `arr[]` representing a permutation, implement the next permutation that rearranges the numbers into the lexicographically next greater permutation. If no such permutation exists, rearrange the numbers into the lowest possible order (i.e., sorted in ascending order).

**Note**: A permutation of an array of integers refers to a specific arrangement of its elements in a sequence or linear order.

---

## Examples

### Example 1:
**Input**:  
`arr = [2, 4, 1, 7, 5, 0]`  
**Output**:  
`[2, 4, 5, 0, 1, 7]`  
**Explanation**: The next permutation of the given array is {2, 4, 5, 0, 1, 7}.

### Example 2:
**Input**:  
`arr = [3, 2, 1]`  
**Output**:  
`[1, 2, 3]`  
**Explanation**: As `arr[]` is the last permutation, the next permutation is the lowest one.

### Example 3:
**Input**:  
`arr = [3, 4, 2, 5, 1]`  
**Output**:  
`[3, 4, 5, 1, 2]`  
**Explanation**: The next permutation of the given array is {3, 4, 5, 1, 2}.

---

## Constraints

1 ≤ arr.size() ≤ 105
1 ≤ arr[i] ≤ 105

---

## Solution

### Approach: Next Permutation Algorithm

```java
import java.util.Arrays;

class Solution {
    public void nextPermutation(int[] arr) {
        if (arr == null || arr.length <= 1) return;

        int i = arr.length - 2;

        // Step 1: Find the first decreasing element from the right
        while (i >= 0 && arr[i] >= arr[i + 1]) i--;

        if (i >= 0) {
            // Step 2: Find the next larger element from the right
            int j = arr.length - 1;
            while (arr[j] <= arr[i]) j--;

            // Step 3: Swap elements at i and j
            swap(arr, i, j);
        }

        // Step 4: Reverse elements from i+1 to the end
        reverse(arr, i + 1, arr.length - 1);
    }

    private void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

    private void reverse(int[] arr, int start, int end) {
        while (start < end) {
            swap(arr, start, end);
            start++;
            end--;
        }
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        
        int[] arr1 = {2, 4, 1, 7, 5, 0};
        solution.nextPermutation(arr1);
        System.out.println(Arrays.toString(arr1)); // Output: [2, 4, 5, 0, 1, 7]

        int[] arr2 = {3, 2, 1};
        solution.nextPermutation(arr2);
        System.out.println(Arrays.toString(arr2)); // Output: [1, 2, 3]

        int[] arr3 = {3, 4, 2, 5, 1};
        solution.nextPermutation(arr3);
        System.out.println(Arrays.toString(arr3)); // Output: [3, 4, 5, 1, 2]
    }
}
```
--
## Complexity Analysis

| **Approach**               | **Time Complexity** | **Space Complexity** |
|----------------------------|----------------------|-----------------------|
| Next Permutation Algorithm | O(n)                | O(1)                  |
