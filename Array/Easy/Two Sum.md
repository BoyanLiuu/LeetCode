
##Brute Force Solution 1
This is the most time-intensive but intuitive solution. Traverse the whole array of the given size. For each element in an array, 
check if any of the two elements add up to the given number n. 
Use a nested for-loop for this purpose and iterate over the entire array for each element
##Time Complexity O(n^2)

##Use HashSet Solution2
```
class Solution {
public int[] twoSum(int[] nums, int target) {
   Map <Integer,Integer> map = new HashMap<>();
    for(int i = 0;i< nums.length;i++){
        int complement = target  -nums[i];
        if(map.containsKey(complement)){
            return new int[]{map.get(complement),i};
        }
        map.put(nums[i],i);
        
    }
    throw new IllegalArgumentException("No two sum solution");
}
}
```
