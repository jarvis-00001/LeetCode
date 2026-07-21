# 🟡 15. 3Sum

![Difficulty](https://img.shields.io/badge/Medium-ffc01e?style=for-the-badge) ![Language](https://img.shields.io/badge/Java-333333?style=for-the-badge) ![Version](https://img.shields.io/badge/v1-6366f1?style=for-the-badge) [![LeetCode](https://img.shields.io/badge/View_on_LeetCode-FFA116?style=for-the-badge&logo=leetcode)](https://leetcode.com/problems/3sum/)

---

## 📖 Description

Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.

 

Example 1:

Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
Explanation: 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.


Example 2:

Input: nums = [0,1,1]
Output: []
Explanation: The only possible triplet does not sum up to 0.


Example 3:

Input: nums = [0,0,0]
Output: [[0,0,0]]
Explanation: The only possible triplet sums up to 0.


 

Constraints:

3 <= nums.length <= 3000
-105 <= nums[i] <= 105

---

## 📋 Problem Details
| | |
|---|---|
| **Difficulty** | 🟡 Medium |
| **Language** | Java |
| **Tags** | `Array`  `Two Pointers`  `Sorting` |
| **Version** | v1 |
| **Solved On** | 2026-07-21 |

## 📊 Complexity Analysis
| Measure | Complexity | Details |
|---------|-----------|---------|
| ⏱️ **Time** | `O(n log n)` | Sorting dominates over single loop |
| 💾 **Space** | `O(1)` | No significant data structure allocations detected |

## 🎯 Approach
- **Linear Scan** — iterates through the input once
- **Sort-Based** — sorts input to enable ordered traversal

## 💻 Solution
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        Arrays.sort(nums);

        for (int i = 0; i < nums.length; i++) {
            if (i > 0 && nums[i] == nums[i-1]) {
                continue;
            }
            
            int j = i + 1;
            int k = nums.length - 1;

            while (j < k) {
                int total = nums[i] + nums[j] + nums[k];

                if (total > 0) {
                    k--;
                } else if (total < 0) {
                    j++;
                } else {
                    res.add(Arrays.asList(nums[i], nums[j], nums[k]));
                    j++;

                    while (nums[j] == nums[j-1] && j < k) {
                        j++;
                    }
                }
            }
        }
        return res;        
    }
}
```

---
<sub>Auto-synced by **LeetFolio** — 2026-07-21</sub>
