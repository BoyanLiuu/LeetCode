# Question: Given a stack, can you sort all its values in an ascending way? 

##  Sample input: 
``` Java
stack = {23,60,12,42,4,97,2}
```

##  Sample output:
``` Java
result = {2,4,12,23,42,60,97}
```

# Solution:
``` Java
public static void sortStack(Stack<Integer> stack) {
        //1. Use a second tempStack.
        //2. Pop value from mainStack.
        //3. If the value is greater or equal to the top of tempStack, then push the value in tempStack
        //else pop all values from tempStack and push them in mainStack and in the end push value in tempStack and repeat from step 2.
        //till mainStack is not empty.
        //4. When mainStack will be empty, tempStack will have sorted values in descending order.
        //5. Now transfer values from tempStack to mainStack to make values sorted in ascending order.
        Stack<Integer> newStack = new Stack<>(stack.getMaxSize());
        while (!stack.isEmpty()) {
            Integer value = stack.pop();
            if (!newStack.isEmpty() && value >= newStack.top()) {
                newStack.push(value);
            } else {
                while (!newStack.isEmpty() && newStack.top() > value)
                    stack.push(newStack.pop());
                newStack.push(value);
            }
        }

        while (!newStack.isEmpty())
            stack.push(newStack.pop());
    }
```
