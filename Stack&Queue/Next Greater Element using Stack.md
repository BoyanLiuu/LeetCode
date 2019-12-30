# Problem For each element in an array, it finds the next greater element in that list.

## input: 
```
arr = {4,6,3,2,8,1}
```
## Output: 
```
arr = {6,8,8,8,-1,-1}
```

# Solution:
``` Java
public static int[] nextGreaterElement(int[] arr) {
        int[] result = new int[arr.length];
        int resultIndex = 0;
        Stack<Integer> stack = new Stack<>(arr.length);
       
        // iterate for rest of the elements
        for (int i = arr.length - 1; i >= 0; i--) {
            if (!stack.isEmpty()) {
                while (!stack.isEmpty() && stack.top() <= arr[i]) {
                    stack.pop();
                }
            }-
            //if it is last element in the array
           if(stack.isEmpty()){
                result[i] = -1;
            }
            else
                result[i]  = stack.top();
            stack.push(arr[i]);
        }
        return result;
    }
```
