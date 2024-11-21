# Stock Buy and Sell – Multiple Transaction Allowed

---

## Problem Statement

The cost of stock on each day is given in an array `price[]`. Each day you may decide to either buy or sell the stock at `price[i]`, and you can even buy and sell the stock on the same day. Find the maximum profit that you can get.

**Note:** 
- A stock can only be sold if it has been bought previously.
- Multiple stocks cannot be held on any given day.

---

## Examples

### Example 1:
**Input:**  
`prices[] = [100, 180, 260, 310, 40, 535, 695]`  

**Output:**  
`865`  


---

### Example 2:
**Input:**  
`prices[] = [4, 2, 2, 2, 4]`  

**Output:**  
`2`  

---

## Constraints
1 <= prices.size() <= 105
0 <= prices[i] <= 104

---

## Solution Approaches

### Approach 1: Greedy Algorithm
This approach involves identifying every increasing sequence of prices. Whenever the price of the stock increases, we calculate the difference and add it to our total profit.

---

### Implementation:

```java
class Solution {
    public int maximumProfit(int nums[]) {
        int n = nums.length;
        int i = 1;
        int profit = 0;
        while (i < n) {
            if (nums[i] >= nums[i - 1]) {
                profit += (nums[i] - nums[i - 1]);
            }
            i++;
        }
        return profit;
    }
}

```
---
## Complexity Analysis

| **Approach**          | **Time Complexity** | **Space Complexity** |
|------------------------|---------------------|-----------------------|
| Greedy Algorithm       | \( O(n) \)         | \( O(1) \)           |
