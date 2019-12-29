# Solution 1  Optimized  pop(),
pop() take O(n) and enqueue operation takes push time O(1),peek is O(n)
``` Java
class MyQueue {
 Stack<Integer>  stack1;
Stack<Integer> stack2 ;
    /** Initialize your data structure here. */
    public MyQueue() {
     stack1 = new Stack<>();
       stack2 = new Stack<>();
        
    }
    
    /** Push element x to the back of queue. */
    public void push(int x) {
        stack1.push(x);
        
    }
    
    /** Removes the element from in front of queue and returns that element. */
    public int pop() {
    //Traverse stack1 and pop all elements in stack2
        while(!stack1.empty()){
            stack2.push(stack1.pop());
        }
        //pop from stack2 which was at the end of the stack1
        int result =  stack2.pop();
      //put all elements back in stack1  
      while(!stack2.empty()){
            stack1.push(stack2.pop());
        } 
        return result;
        
    }
    
    /** Get the front element. */
    public int peek() {
     while(!stack1.empty()){
            stack2.push(stack1.pop());
        }
     int result =  stack2.peek();
      while(!stack2.empty()){
            stack1.push(stack2.pop());
        }  
        return result;
    }
    
    /** Returns whether the queue is empty. */
    public boolean empty() {
        return stack1.empty();
        
    }
}
```

# Solution 2: Optimizing both  peek() pop() push method  amortized
This solution is more optimized than the previous one, as the transfer of elements between stacks takes place only if stack2 is empty. Therefore, the amortized complexity of the dequeue operation becomes O(n) while the time complexity for the enqueue operation is O(1).
``` Java
class MyQueue {

    Stack<Integer> stack1 = new Stack();
    Stack<Integer> stack2 = new Stack();
    
    public void push(int x) {
        stack1.push(x);
    }

    public void pop() {
        peek();
        stack2.pop();
    }

    public int peek() {
        if (stack2.empty())
            while (!stack1.empty())
                stack2.push(stack1.pop());
        return stack2.peek();
    }

    public boolean empty() {
        return stack2.empty() && stack1.empty();
    }
}


```
