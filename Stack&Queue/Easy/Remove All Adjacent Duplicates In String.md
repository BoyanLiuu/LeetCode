# Naive solution: Runtime: 50 ms
```Java
class Solution {
    public String removeDuplicates(String S) {
        char arr [] = S.toCharArray();
        Stack<Character> stack = new Stack<>();
        StringBuilder  result = new StringBuilder("");
        for(Character x : arr){
            //if it is empty we just push it
            if(stack.empty()){
                stack.push(x);
            }else if(stack.peek() == x){
                //remove top of stack if we see two are same
                stack.pop();
                
            }else{
                stack.push(x);
            }
            
        }
        while(!stack.empty()){
            result.append(stack.pop());
        }
        result =result.reverse();
        return result.toString();
    }
}
```
# Better solution: Runtime: 9 ms
Use stringBuilder as stack If current char is same as the end of the StringBuilder, delete the char at end; otherwise, append it at the end.
```Java
    public String removeDuplicates(String S) {
        StringBuilder sb = new StringBuilder();
        for (char c : S.toCharArray()) {
            int size = sb.length();
            if (size > 0 && sb.charAt(size - 1) == c) { 
                sb.deleteCharAt(size - 1); 
            }else { 
                sb.append(c); 
            }
            System.out.println(sb);
        }
        return sb.toString();
    }
```
# Third solution: Runtime: 3 ms 
Use two pointer
If current char is same as the end of non-adjacent-duplicate chars, decrease the counter end by 1;
otherwise, copy the current char to its end.

``` Java
   public String removeDuplicates(String S) {
        char[] a = S.toCharArray();
        int end = -1;
        for (char c : a) {
            if (end >= 0 && a[end] == c) { 
                --end; 
            }else { 
                a[++end] = c; 
            }
        }
        return String.valueOf(a, 0, end + 1);
    }
```
