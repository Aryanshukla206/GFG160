## Majority Element II

### Problem Statement:
You are given an array of integers `arr[]` where each number represents a vote for a candidate. Return the candidates that have votes greater than one-third of the total votes. If no such candidate exists, return an empty array. The result should be returned in increasing order.

### Examples:

**Example 1:**
- Input: `arr[] = [2, 1, 5, 5, 5, 5, 6, 6, 6, 6, 6]`
- Output: `[5, 6]`
- Explanation: 5 and 6 occur more than `n/3` times.

**Example 2:**
- Input: `arr[] = [1, 2, 3, 4, 5]`
- Output: `[]`
- Explanation: No candidate occurs more than `n/3` times.

---

### Constraints:
1 <= arr.size() <= 106  
-109 <= arr[i] <= 109

---

### Approach 1: Boyer-Moore Majority Vote Algorithm  
This algorithm finds potential majority elements and validates them in a second pass.  

#### Steps:
1. Identify up to 2 potential candidates using the Boyer-Moore voting mechanism.  
2. Validate the candidates by counting their occurrences.  

```java
class Solution {
    public List<Integer> findMajority(int[] nums) {
        List<Integer> result = new ArrayList<>();
        int num1 = -1, num2 = -1, count1 = 0, count2 = 0;

        // Step 1: Find potential candidates
        for (int num : nums) {
            if (num == num1) {
                count1++;
            } else if (num == num2) {
                count2++;
            } else if (count1 == 0) {
                num1 = num;
                count1 = 1;
            } else if (count2 == 0) {
                num2 = num;
                count2 = 1;
            } else {
                count1--;
                count2--;
            }
        }

        // Step 2: Validate candidates
        count1 = 0;
        count2 = 0;
        for (int num : nums) {
            if (num == num1) count1++;
            else if (num == num2) count2++;
        }

        if (count1 > nums.length / 3) result.add(num1);
        if (count2 > nums.length / 3) result.add(num2);

        return result;
    }
}

```
---

### Approach 2: HashMap Approach

## Steps:
Count occurrences of each number using a HashMap.  
Iterate through the map and add numbers with count > n/3  
```java
class Solution {
    public List<Integer> findMajority(int[] nums) {
        List<Integer> result = new ArrayList<>();
        HashMap<Integer, Integer> map = new HashMap<>();
        int n = nums.length / 3;

        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            if (entry.getValue() > n) {
                result.add(entry.getKey());
            }
        }

        return result;
    }
}

```
---
### Complexity Analysis

| **Approach**                        | **Time Complexity** | **Space Complexity** |
|-------------------------------------|----------------------|-----------------------|
| Boyer-Moore Majority Vote Algorithm | \( O(n) \)           | \( O(1) \)            |
| HashMap Approach                    | \( O(n) \)           | \( O(n) \)            |

