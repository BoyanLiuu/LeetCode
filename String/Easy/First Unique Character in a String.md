# My solution,Runtime: 40 ms
```
class Solution {
    public int firstUniqChar(String s) {
        //convert string to char array
        char[] ary =  s.toCharArray();
        Map <Character, Integer> map = new HashMap<>();
        //loop through array and put them into a hashmap
    for(int i =0 ; i < ary.length; i++){
     if (map.containsKey(ary[i])) {
       map.put(ary[i],map.get(ary[i])+1);
     }else{
        map.put(ary[i],1);
     }

   }
   for(int i =0 ; i < ary.length; i++){
     if(map.get(ary[i]) == 1){
       return i;

     }
     

   }
   return -1;
 }
        
        
}
```
# Improvement Runtime: 29ms


