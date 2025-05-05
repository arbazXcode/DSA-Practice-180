# 🧠 DSA LeetCode Practice – Beginner Friendly

This repo contains beginner-friendly problems with clean explanations and optimized code in C++. Each section is divided into:

- 🔹 Problem Link
- 🔹 Beginner-Friendly Explanation
- 🔹 Code Only (copyable)
- 🔹 Time & Space Complexity

---

## ✅ 1. [Two Sum](https://leetcode.com/problems/two-sum/)

### 🧾 Problem:
Given an array of integers `nums` and an integer `target`, return **indices of the two numbers** such that they add up to the target.

You may assume that each input would have **exactly one solution**, and you may not use the same element twice.

---

### 🧠 Beginner-Friendly Approach:

- Use a hash map to store the **value and its index**.
- For each number, check if `(target - current_number)` exists in the map.
- If it exists, return both indices.

---

### ✅ CODE ONLY – Two Sum (C++)

```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> mp;  // stores value → index

        for (int i = 0; i < nums.size(); i++) {
            int complement = target - nums[i];

            if (mp.find(complement) != mp.end()) {
                return {mp[complement], i};
            }

            mp[nums[i]] = i;
        }

        return {}; // won't reach here as per problem constraint
    }
};

```

- Time & Space Complexity:
-Time: O(n)

-Space: O(n) (hashmap)



# 🧠 DSA LeetCode Practice – Beginner Friendly

This repo contains beginner-friendly problems with clean explanations and optimized code in C++. Each section is divided into:

- 🔹 Problem Link
- 🔹 Beginner-Friendly Explanation
- 🔹 Code Only (copyable)
- 🔹 Time & Space Complexity

---

## ✅ 1. [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)

### 🧾 Problem:

You are given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively. Merge `nums2` into `nums1` as one sorted array **in-place**.

`nums1` has extra space at the end (size `m + n`) to hold the elements of `nums2`.

---

### 🧠 Beginner-Friendly Approach (Two Pointers from End):

- **Concept:** We are merging two sorted arrays. Instead of inserting elements at the beginning (which would be inefficient), we will start filling the merged array from the **end** to keep the order intact.
  
- **Steps:**
  1. Start three pointers:  
     - `i` at `m-1` (the last valid element in `nums1`),  
     - `j` at `n-1` (the last element of `nums2`),  
     - `k` at `m+n-1` (the end of the `nums1` array).
     
  2. **While both arrays have elements left** (i.e., `i >= 0` and `j >= 0`), compare the elements at `nums1[i]` and `nums2[j]`, and insert the larger one at `nums1[k]`.
  
  3. **If there are remaining elements in `nums2`**, copy them directly into `nums1`.

---


### ✅ CODE ONLY – Merge Sorted Array (C++)

``` 
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int i = m - 1;         // pointer at end of nums1 part
        int j = n - 1;         // pointer at end of nums2
        int k = m + n - 1;     // pointer at end of total nums1

        // Compare and place elements from the back
        while (i >= 0 && j >= 0) {
            if (nums1[i] > nums2[j]) {
                nums1[k--] = nums1[i--];
            } else {
                nums1[k--] = nums2[j--];
            }
        }

        // Fill leftover nums2 elements (if any)
        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
};

```
# apple

- Time & Space Complexity:
- Time: O(m + n)

- We are iterating through both arrays once.

- Space: O(1) (in-place)

- No additional space used other than the input arrays.
