# Leetcode

## **快慢指针类型**

\*\*\*\*

## 滑动窗口

滑动窗口类型的题目经常是用来执行数组或是链表上某个区间（窗口）上的操作。比如找最长的全为1的子数组长度。滑动窗口一般从第一个元素开始，一直往右边一个一个元素挪动。当然了，根据题目要求，我们可能有固定窗口大小的情况，也有窗口的大小变化的情况。

### 1、最长假日

holidays 表示平日或假日，例如 0000011 表示前面 5 天是工作日，后面 2 天是假日。 pto 表示最多可以放几天假。 output: 计算在可以用完 pto 的情況下，最久可以放多长的连续的假。

#### Example：

```text
Input: holidays = [0,0,0,0,0,1,1], pto = 2, 
Output = 4 
Explanation: [0,0,0,1,1,1,1]
```

#### Solution:

```text

     
function longestHolidays(arr, pto){
  let start = 0;
  let longest = -1;
  for(let end=0;end < arr.length;++end){
    if(arr[end] === 0){
      --pto
    }
    while(pto < 0){
      if(arr[start++]===0){
        ++pto;
      }
    }
    longest = Math.max(longest, end - start + 1)
    console.log([start,end], longest)

  }
  return longest;
}

const arr = [0,0,0,0,0,1,1,0,0,0,0,0,1,1,0,0,0,0,1,1,1];
const res = longestHolidays(arr, 9);
console.log(res);     
```

### 2、[最大子数组之和](https://leetcode.com/problems/maximum-subarray/)

Given an integer array `nums`, find the contiguous subarray \(containing at least one number\) which has the largest sum and return its sum.



**Example:**

```text
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

#### Solution:

```text
function maxSubArray(nums) {
  for(let i=1;i< nums.length;i++){
     if(nums[i-1] > 0){
       nums[i] += nums[i-1] 
     }
  }
  console.log(nums)
   return Math.max(nums)
};
const arr = [-2,1,-3,4,-1,2,1,-5,4];
const res = maxSubArray(arr)
console.log(res)
```

## 循环排序

```text

```

查找

二分查找

```text
function binarySearch(arr, target) {
  let left = 0;
  let right = arr.length - 1
  while(left <= right){
    let mid = left + Math.floor((right-left)/2); 
    if(target === arr[mid]){
      return mid;
    }else if(target < arr[mid]){
      right = mid - 1;
    } else {
      left = mid + 1;
    }
  }
  return -1;
}

const arr = [1,2,3,4,5,7,8,899,1111];
const target = 31;
const res = binarySearch(arr, target);

console.log(res)
```

整数反转

```text
function reverseInt(v){
  let ret = 0;
  while(v !== 0){
    ret = ret * 10 + v % 10;
    v = Math.floor(v / 10) || 0
  }
  return ret;
}

const res = reverseInt(123);
console.log(res)
```

两数之和

```text
function getSummaryIndex(arr, target){
  const map = {};
  let ret = []
  for(let i=0;i<arr.length;i++){
    if(map[target - arr[i]]===undefined){
      map[arr[i]] = i
    }else{
      ret = [map[target-arr[i]], i]
    }
  }
  return ret;
}

const arr = [1,2,3,3, 4,4,5];
const target = 8;
const res = getSummaryIndex(arr, target);
console.log(res);
```



