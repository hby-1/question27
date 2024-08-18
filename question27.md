# 搜索插入位置

给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

请必须使用时间复杂度为 `O(log n)` 的算法。

## 示例 1:
>### 输入: 
>nums = [1,3,5,6], target = 5
### 输出: 
>2

## 示例 2:
>### 输入: 
>nums = [1,3,5,6], target = 2
### 输出: 
>1

## 代码：
1.

    public class Solution {
        public int SearchInsert(int[] nums, int target) {
            int index=0;
            if(nums[nums.Length-1]<target){
                return nums.Length;
            }
            for(int i=0,n=1;i<nums.Length||n<nums.Length;i++,n++){
                if(nums[i]==target){
                    index=i;
                    break;
                }
                if(nums[n-1]<target&&nums[n]>target){
                    index=n;
                    break;
                }
            }
            return index;
        }
    }
2.

    public class Solution {
        public int SearchInsert(int[] nums, int target) {
            return SearchInsert(nums, target, 0, nums.Length - 1);
        }

        public int SearchInsert(int[] nums, int target, int low, int high) {
            if (low > high) {
                return low;
            }
            int mid = low + (high - low) / 2;
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] > target) {
                return SearchInsert(nums, target, low, mid - 1);
            } else {
                return SearchInsert(nums, target, mid + 1, high);
            }
        }
    }
3.

    public class Solution {
        public int SearchInsert(int[] nums, int target) {
            int low = 0, high = nums.Length - 1;
            while (low <= high) {
                int mid = low + (high - low) / 2;
                if (nums[mid] == target) {
                    return mid;
                } else if (nums[mid] > target) {
                    high = mid - 1;
                } else {
                    low = mid + 1;
                }
            }
            return low;
        }
    }

