## Input:
The input is a string containing a postfix mathematic expression. Each digit is considered a separate number, i.e. there are no double-digit numbers.
## Output:
An integer result of the given postfix expression.

## sample input:
```
expression = "921*-8-4+"
```
## sample output:
3

## Explanation:
2*1 = 2
9-2=7
7-8 = -1
-1+4 = 3

## Solution:
``` Java
  public static int evaluatePostFix(String expression) {
  Stack<Integer> stack = new Stack<>(expression.length());
        //1.Scan expression character by character,
		//2.If character is a number push it in stack
		//3.If character is operator then pop two elements from stack
		//perform the operation and put the result back in stack
		//At the end, Stack will contain result of whole expression.
        for (int i = 0; i < expression.length(); i++) {
            char character = expression.charAt(i);

            if (!Character.isDigit(character)) {
                Integer x = stack.pop();
                Integer y = stack.pop();

                switch (character) {
                    case '+':
                        stack.push(y + x);
                        break;
                    case '-':
                        stack.push(y - x);
                        break;
                    case '*':
                        stack.push(y * x);
                        break;
                    case '/':
                        stack.push(y / x);
                        break;
                }

            } else
                stack.push(Character.getNumericValue(character));
        }
        return stack.pop();
    }
```


