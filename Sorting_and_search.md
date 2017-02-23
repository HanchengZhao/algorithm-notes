## Search

### Binary search
Use binary search to find the index

```
    def binarySearch(self, nums, target, index):
        if not nums:
            return -1
        mid = len(nums)/2
        if target == nums[mid]:
            return target
        elif target > nums[mid]:
            return self.binarySearch(nums[mid+1:], target, index+mid)
        elif target < nums[mid]:
            return self.binarySearch(nums[:mid], target, index)
```





## Selection

### Quickselect

Quickselect is a selection algorithm to find the kth smallest element in an unordered list.

[hkth-largest-element-in-an-array](https://leetcode.com/problems/kth-largest-element-in-an-array/)

## Sorting

### Common sorting algorithm

Sort in Python:

```
intervals = sorted(intervals, key = lambda x : x.start)
```

bucketsort:
[top-k-frequent-elements](https://leetcode.com/problems/top-k-frequent-elements/)
by using bucket sort, it can reduce the time comlexity from O(nlogn) to O(n)
