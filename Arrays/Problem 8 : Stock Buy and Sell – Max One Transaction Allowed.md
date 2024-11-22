# Stock Buy and Sell – Max One Transaction Allowed

## Problem Statement

Given an array `prices[]` of length `n`, representing the prices of the stocks on different days, the task is to find the maximum profit possible by buying and selling the stocks on different days when **at most one transaction** is allowed. Here one transaction means **1 buy + 1 sell**.  
If it is not possible to make a profit, then return `0`.

### Note:
- Stock must be bought before being sold.

---

### Examples

#### Example 1
**Input:**  
`prices[] = [7, 10, 1, 3, 6, 9, 2]`  
**Output:**  
`8`  
**Explanation:**  
You can buy the stock on day 2 at price = 1 and sell it on day 5 at price = 9. Hence, the profit is 8.

#### Example 2
**Input:**  
`prices[] = [7, 6, 4, 3, 1]`  
**Output:**  
`0`  
**Explanation:**  
Here the prices are in decreasing order, hence if we buy any day then we cannot sell it at a greater price. Hence, the answer is 0.

#### Example 3
**Input:**  
`prices[] = [1, 3, 6, 9, 11]`  
**Output:**  
`10`  
**Explanation:**  
Since the array is sorted in increasing order, we can make maximum profit by buying at `prices[0]` and selling at `prices[n-1]`.

---

## Constraints

1 <= prices.size()<= 105  
0 <= prices[i] <=104

---

## Solution

### Code Implementation

```java
class Solution {
    public int maximumProfit(int prices[]) {
        // Code here
        int n = prices.length;
        int profit = 0;
        int i = 0;
        int j = 1;
        while (j < n) {
            if (prices[i] < prices[j]) {
                profit = Math.max(profit, prices[j] - prices[i]);
                j++;
            } else {
                i = j;
                j++;
            }
        }
        return profit;
    }
}

```
---

## Complexity Analysis

| **Approach**        | **Time Complexity** | **Space Complexity** |
|----------------------|---------------------|-----------------------|
| Greedy Algorithm     | \( O(n) \)         | \( O(1) \)           |

 ---
