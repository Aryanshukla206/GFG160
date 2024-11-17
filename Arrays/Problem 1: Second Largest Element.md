# Problem: Second Largest Element

## Problem Statement

Given an array of positive integers `arr[]`, return the **second largest element**. If the second largest element doesn't exist (i.e., all elements are equal), return `-1`.

---

### Examples

1. **Input**: `arr[] = [12, 35, 1, 10, 34, 1]`  
   **Output**: `34`  
   **Explanation**: The largest element is `35` and the second largest is `34`.

2. **Input**: `arr[] = [10, 5, 10]`  
   **Output**: `5`  
   **Explanation**: The largest element is `10` and the second largest is `5`.

3. **Input**: `arr[] = [10, 10, 10]`  
   **Output**: `-1`  
   **Explanation**: All elements are equal, so there is no second largest element.

---

## Solution 1: Sorting-Based Approach

### Code:
```java
import java.util.Arrays;

public class Solution {
    public int getSecondLargest(int[] arr) {
        // Sort the array in ascending order
        Arrays.sort(arr);

        // Traverse from the end to find the second largest
        for (int i = arr.length - 1; i > 0; i--) {
            if (arr[i] != arr[i - 1]) {
                return arr[i - 1];
            }
        }

        // If no second largest element exists
        return -1;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();

        int[] arr1 = {12, 35, 1, 10, 34, 1};
        System.out.println(solution.getSecondLargest(arr1)); // Output: 34

        int[] arr2 = {10, 5, 10};
        System.out.println(solution.getSecondLargest(arr2)); // Output: 5

        int[] arr3 = {10, 10, 10};
        System.out.println(solution.getSecondLargest(arr3)); // Output: -1
    }
}


### Code:
public int getSecondLargest(int[] arr) {
        int first = Integer.MIN_VALUE;
        int second = Integer.MIN_VALUE;

        // Traverse the array to find the first and second largest elements
        for (int num : arr) {
            if (num > first) {
                second = first;  // Update second largest
                first = num;     // Update largest
            } else if (num > second && num < first) {
                second = num;    // Update second largest if it's less than first
            }
        }

        // If no valid second largest exists, return -1
        return (second == Integer.MIN_VALUE) ? -1 : second;
    }





| **Comparison Approach**    | **Time Complexity** | **Space Complexity** |
|----------------------------|----------------------|-----------------------|
| Sorting-Based (First)       | O(n log n)          | O(1)                  |
| Optimized Single Pass       | O(n)                | O(1)                  |
