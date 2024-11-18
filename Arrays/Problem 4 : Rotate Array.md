# Problem: Rotate Array

## Problem Statement
Given an unsorted array `arr[]`, rotate the array to the left (counter-clockwise) by `d` steps, where `d` is a positive integer. The rotation should be done in place, considering the array as circular.

### Examples:

**Input:**  
`arr[] = [1, 2, 3, 4, 5]`, `d = 2`  
**Output:**  
`[3, 4, 5, 1, 2]`  
**Explanation:** Rotated by 2 elements, resulting in `[3, 4, 5, 1, 2]`.

**Input:**  
`arr[] = [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]`, `d = 3`  
**Output:**  
`[8, 10, 12, 14, 16, 18, 20, 2, 4, 6]`  
**Explanation:** Rotated by 3 elements, resulting in `[8, 10, 12, 14, 16, 18, 20, 2, 4, 6]`.

**Input:**  
`arr[] = [7, 3, 9, 1]`, `d = 9`  
**Output:**  
`[3, 9, 1, 7]`  
**Explanation:** After 9 rotations, we get `[3, 9, 1, 7]`.

---

## Constraints:
1 <= arr.size(), d <= 105
0 <= arr[i] <= 105

---

## Approach 1: Naive Rotation (Iterative)
### Code:
```java
class Solution {
    public void rotateLeft(int[] arr, int d) {
        int n = arr.length;
        d = d % n; // Handle cases where d > n
        
        for (int i = 0; i < d; i++) {
            int temp = arr[0];
            for (int j = 0; j < n - 1; j++) {
                arr[j] = arr[j + 1];
            }
            arr[n - 1] = temp;
        }
    }
}
```
---

## Approach 2: triple Reverse
### Code:
```java
class Solution {
    // Function to rotate an array by d elements in counter-clockwise direction.
    static void rotateArr(int arr[], int d) {
        // add your code here
        int n = arr.length;
        d = d % n;
        int i = 0 ;
        reverse(arr,0,d-1);
        reverse(arr,d,n-1);
        reverse(arr,0,n-1);
        
    }
    static void swap(int[] arr, int i, int j){
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
    static void reverse(int[] arr, int f, int l ){
        while(f < l){
            swap(arr,f,l);
            f++;
            l--;
        }
        
    }
}
```
---
## Complexity Analysis:

| **Approach**                  | **Time Complexity** | **Space Complexity** |
|-------------------------------|----------------------|-----------------------|
| Naive Iterative Rotation       | \( O(d * n) \)  | \( O(1) \)            |
| Optimized Reversal Approach    | \( O(n) \)           | \( O(1) \)            |



