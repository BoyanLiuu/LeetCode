# Given a stream of integers and a window size, calculate the moving average of all integers in the sliding window.

##  Question
Given a stream of integers and a window size, calculate the moving average of all integers in the sliding window.
## Example
```
MovingAverage m = new MovingAverage(3);
m.next(1) = 1
m.next(10) = (1 + 10) / 2
m.next(3) = (1 + 10 + 3) / 3
m.next(5) = (10 + 3 + 5) / 3
```


## Solution:
``` Java
class MovingAverage {

    Queue<Integer> q;
    int capacity;
    double currSum;

    /** Initialize your data structure here. */
    public MovingAverage(int size) {
        q = new LinkedList<Integer>();
        capacity = size;
        currSum = 0.0;
    }
    
    public double next(int val) {
        currSum += val;
        //add value into queue
        q.add(val);
        //remove front if current size is > capacity
        if(q.size() > capacity ){
            currSum -= q.remove();
        }
       
        return currSum / q.size() ;
    }
}

/**
 * Your MovingAverage object will be instantiated and called as such:
 * MovingAverage obj = new MovingAverage(size);
 * double param_1 = obj.next(val);
 */
```
