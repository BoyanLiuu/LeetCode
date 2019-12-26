# Explanation
The algorithm for this solution is to first create a new array with products of all elements to the left of each element as done on the code I have strong emphasis. Then multiply each element in that array to the product of all the elements to the right of the array by traversing it in reverse as done on code I have strong emphasis.
```
class Solution {
    public int[] productExceptSelf(int[] nums) {
    int n = nums.length;
    int i, temp = 1; 

    // Allocation of result array
    int result[] = new int[n]; 

    // Initializing the result array by 1
    for(int j=0; j < n; j++) 
      result[j] = 1; 

    // Product of elements on left side excluding arr[i]
    //arr[1,2,3,4] will make result become [1,1,2,6];
    for (i = 0; i < n; i++)  
    { 
      #* result[i] = temp; 
      #* temp *= nums[i]; 
    } 

    // Initializing temp to 1 for product on right side
    temp = 1; 

    // Product of elements on right side excluding arr[i] */
    for (i = n - 1; i >= 0; i--)  
    { 
     #* result[i] *= temp; 
     #* temp *= nums[i]; 
    } 
    return result; 
  } 
    }
  ```
