## Idea:
Iterate through the string exp.
each opening parentheses, push it into stack
For every closing parentheses check for its opening parentheses in stack
If you can't find the opening parentheses for any closing one then returns false.
and after complete traversal of string exp, if there's any opening parentheses left
in stack then also return false.
At the end return true if you haven't encountered any of the above false conditions.

## Solution
``` Java
class Solution {
    public boolean isValid(String s) {
         Stack<Character> stack = new Stack<>();

        for (int i = 0; i <s.length(); i++) {

            char character = s.charAt(i);

            if (character == '}' || character == ')' || character == ']') {

                if (stack.isEmpty()) return false;
                //return false if top of the stack is not equal to what we want.
                if ((character == '}' && stack.pop() != '{') || (character == ')' && stack.pop() != '(') || (character == ']' && stack.pop() != '[')) return false;

            }
            else stack.push(character);

        } //end of for
        
        //for edge case like [
         if (!stack.isEmpty()) return false;
        return true;
    }
}
```
