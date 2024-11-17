# Problem: Reverse an Array

## Problem Statement
Given an array of integers `arr[]`, reverse the array in place.

### Examples:

**Input:**  
`arr = [1, 4, 3, 2, 6, 5]`  
**Output:**  
`[5, 6, 2, 3, 4, 1]`  

**Input:**  
`arr = [4, 5, 2]`  
**Output:**  
`[2, 5, 4]`  

**Input:**  
`arr = [1]`  
**Output:**  
`[1]`  

### Constraints:
1<=arr.size()<=105
0<=arr[i]<=105


---

## Approach 1: Iterative Two-Pointer Method

```java
class Solution {
    public void reverseArray(int arr[]) {
        int j = arr.length - 1;
        for (int i = 0; i < j; i++) {
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
            j--;
        }
    }

    public static void main(String[] args) {
        Solution solution = new Solution();

        int[] arr1 = {1, 4, 3, 2, 6, 5};
        solution.reverseArray(arr1);
        System.out.println(java.util.Arrays.toString(arr1)); // Output: [5, 6, 2, 3, 4, 1]

        int[] arr2 = {4, 5, 2};
        solution.reverseArray(arr2);
        System.out.println(java.util.Arrays.toString(arr2)); // Output: [2, 5, 4]

        int[] arr3 = {1};
        solution.reverseArray(arr3);
        System.out.println(java.util.Arrays.toString(arr3)); // Output: [1]
    }
}

```
---

## Approach 2: Recursive Approach 

```java
public void reverseArray(int arr[], int start, int end) {
        if (start >= end) {
            return;
        }

        // Swap elements at start and end
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;

        // Recursive call
        reverseArray(arr, start + 1, end - 1);
    }
```
---
### Time and Space Complexity:

| **Approach**           | **Time Complexity** | **Space Complexity** |
|------------------------|---------------------|----------------------|
| Reversal using two pointers | \( O(n) \)        | \( O(1) \)           |
| Reversal using extra array  | \( O(n) \)        | \( O(n) \)           |

