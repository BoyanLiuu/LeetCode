## Solution1 : two stack  Runtime: 39 ms
``` Java
class MinStack {

    Stack<Integer> mainStack;
    Stack<Integer> minStack;
    

    /** initialize your data structure here. */
    public MinStack() {
        //We will use two stacks mainStack to hold origional values
        //and minStack to hold minimum values. Top of minStack will always
        //be the minimum value from mainStack
        mainStack = new Stack<>();
        minStack = new Stack<>();
    }
     //pushes value into the stack
    public void push(Integer value){
        int temp;
        //1. Push value in mainStack and check value with the top value of minStack
        //2. If value is greater than top, then push top in minStack
        //else push value in minStack
        mainStack.push(value);
        System.out.println(value);
        if(!minStack.isEmpty() && minStack.peek() < value){
            minStack.push(minStack.peek());
        }
        else{
            minStack.push(value);
        }       
    }
    //removes and returns value from stack
    public void pop() {
        //1. Pop element from minStack to make it sync with mainStack,
        //2. Pop element from mainStack 
        minStack.pop();
        mainStack.pop();
        
    }
    
    public int top() {
        return mainStack.peek();
        
    }
    
    public int getMin() {
        return minStack.peek();
        
    }
}
```

## Solution2  : One stack Runtime: 4 ms
```Java
class MinStack {
    int min = Integer.MAX_VALUE;
    Stack<Integer> stack = new Stack<Integer>();
    public void push(int x) {
        // only push the old minimum value when the current 
        // minimum value changes after pushing the new value x
        if(x <= min){          
            stack.push(min);
            min=x;
        }
        stack.push(x);
    }

    public void pop() {
        // if pop operation could result in the changing of the current minimum value, 
        // pop twice and change the current minimum value to the last minimum value.
        if(stack.pop() == min) min=stack.pop();
    }

    public int top() {
        return stack.peek();
    }

    public int getMin() {
        return min;
    }
}
```
