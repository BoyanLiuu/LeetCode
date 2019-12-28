# We can use 2 pointer in linkedlist question

``` Java
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode slow  = head;
        ListNode quick =  head;
        
        while(slow !=null && quick !=null && quick.next !=null){
            slow = slow.next;//the slow pointer will jump 1 step
            quick = quick.next.next;//the fasr pointer will jump 2 steps 
            
            // when the pointers become equal then there must be a loop
            if(slow == quick){
                return true;
                
            }
        
            
        }
        
        return false;
        
    }
}


```

