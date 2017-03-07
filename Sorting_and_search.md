## Search

### Binary search
Use binary search to find the index
- recurtion:
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

- iteration:

```
 while left <= right:
            mid = (left + right) / 2
            if citations[mid] == leng - mid:
                return citations[mid]
            elif citations[mid] > leng - mid:
                right = mid-1
            else:
                left = mid+1
```





## Selection

### Quickselect

Quickselect is a selection algorithm to find the kth smallest element in an unordered list. 

[hkth-largest-element-in-an-array](https://leetcode.com/problems/kth-largest-element-in-an-array/)

## Sorting

### Common sorting algorithm

#### Bubble Sort | Runtime O(O^2) average and worst case. Memory O(1)

```
def bubbleSort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(1,n-1):
            if arr[j-1] > arr[j]:
                arr[j-1],arr[j] = arr[j], arr[j-1]
    return arr
```

#### Selection Sort | Runtime O(O^2) average and worst case. Memory O(1)

Steps:
1. choose the min(max) value in an unordered list and put it in the begin
2. repeat the same process for the rest 

```
def select_sort(ary):
    n = len(ary)
    for i in range(0,n):
        min = i                             #find the min index
        for j in range(i+1,n):
            if ary[j] < ary[min] :
                min = j     
        ary[min],ary[i] = ary[i],ary[min]   #exchange
    return ary
```

#### Insertion Sort | Runtime O(O^2) average and worst case. Memory O(1)

#### Merge Sort | Runtime O(nlog(n)) average and worst case. Memory O(n)

Merge sort divides then array in half, sorts each of those halves, and then merges them back together. Each of those halves has the same sorting algorithm applied to it. Eventually, you are merging just two single-element arrays. It is the “merge” part that does all the heavy lifting.

The merge method operates by copying all the elements from the target array segment into a helper array, keeping track of where the start of the left and right halves should be (**helperLeft** and **helperRight**).

```
void mergesort(int[] array){
    int[] helper = new int[array.length];
    mergesort(array, helper, 0, array.length - 1)
}

void merge(int[] array, int[] helper, int low, int middle, int high){
    for (int i = low; i <= high; i++){
        helper[i] = array[i];
    }

    int helperLeft = low;
    int helperRight = middle + 1;
    int current = low;

    while (helperLeft <= middle && helperRight <= high){
        if (helper[helperLeft] <= helper[helperRight]){
            array[current] = helper[helperLeft];
            helperLefting;
        }
        else {
            array[current] = helper[helperRight];
            helperRight++;
        }
        current++;
    }

    int remaining = middle - helperLeft;
    for (int i = 0; i <= remaining; i++){
        array[current + i] = helper[helperLeft + i];
    }
}
```
You may notice that only the remaining elements from the left half of the helper array are copied into the target array. Why not the right half? The right half doesn't need to be copied because it's already there.

#### Quick Sort | Runtime O(nlog(n)) average and worst case. Memory O(log(n)

In quick sort, we pick a random element and partition the array, such that all numbers that are less than the partitioning element come before all elements that are greater than it. The partitioning can be performed efficiently through a series of swaps.

```
void quickSort(int arr[], int left, int right){
    int index = partition(arr, left, right);
    if (left < index - 1){
        quickSort(arr, left, index - 1);
    }
    if (index < right){
        quickSort(arr, index, right);
    }
}

int partition(int arr[], int left, int right){
    int pivot = arr[(left + right) / 2];
    while (left <= right){
        while (arr[left] < pivot) left++;
        while (arr[right] > pivot) right--;

        // Swap elements, and move left and right indices
        if (left <= right){
            swap(arr, left, right);
            left++;
            right--;
        }
    }
    return left;
}
```


### Sorted in Python:

```
intervals = sorted(intervals, key = lambda x : x.start)
```

bucketsort:
[top-k-frequent-elements](https://leetcode.com/problems/top-k-frequent-elements/)
by using bucket sort, it can reduce the time comlexity from O(nlogn) to O(n)
