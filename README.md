# 🚀 LeetCode Solutions in C++
---

## 1. [Two Sum](https://leetcode.com/problems/two-sum)

### 🔍 Problem:
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

###  Optimal Approach (Hash Map):

**Approach:**
- Use a hash map to store elements and their indices.
- For each element, check if the complement `(target - nums[i])` exists in the map.

**Time Complexity:** O(n)  
**Space Complexity:** O(n)

### 💻 Code:
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> mp; // value -> index

        for (int i = 0; i < nums.size(); i++) {
            int complement = target - nums[i];
            if (mp.find(complement) != mp.end()) {
                return {mp[complement], i}; // return pair indices
            }
            mp[nums[i]] = i; // store index of current number
        }

        return {}; // no pair found
    }
};



# 🧩 LeetCode Problem: Merge Sorted Array

**Link:** [Merge Sorted Array – LeetCode](https://leetcode.com/problems/merge-sorted-array)

---

## 📘 Problem Statement

You are given two integer arrays `nums1` and `nums2`, sorted in non-decreasing order, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.

Merge `nums2` into `nums1` as one sorted array in-place.

`nums1` has a length of `m + n`, where the last `n` elements are set to 0 and should be ignored during the merge.

---

## ✅ Optimal Approach: Two Pointers (From End)

### 🔹 Idea:
- Start from the **end** of `nums1` and `nums2`.
- Compare the elements and insert the **larger one** at the back of `nums1`.
- Continue until all elements from `nums2` are merged.

### 🔹 Why from the end?
Because `nums1` has enough space at the end to hold merged elements — starting from the back avoids overwriting useful data.

---

## 💻 C++ Code with Comments

```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int i = m - 1;         // Pointer to last valid element in nums1
        int j = n - 1;         // Pointer to last element in nums2
        int k = m + n - 1;     // Pointer to last position in nums1

        // Merge both arrays from the back
        while (i >= 0 && j >= 0) {
            if (nums1[i] >= nums2[j]) {
                nums1[k--] = nums1[i--];  // Place nums1[i] at the end
            } else {
                nums1[k--] = nums2[j--];  // Place nums2[j] at the end
            }
        }

        // If any elements left in nums2 (nums1 elements already in place)
        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
};

