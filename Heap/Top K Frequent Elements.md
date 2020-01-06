```Java
class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<Integer,Integer>();
        for(int x: nums){
            if(!map.containsKey(x)){
                map.put(x,1);
            }else{
                map.put(x, map.get(x)+1);
            }   
        }
    PriorityQueue<Integer> heap =
            new PriorityQueue<Integer>((n1, n2) ->  map.get(n1) -  map.get(n2));
        
    // build a heap for k top frequent elements in the heap.
    for (int n: map.keySet()) {
      heap.add(n);
      if (heap.size() > k)
        heap.poll();
    } 
        // build output list
        List <Integer> result =  new LinkedList();
        
        while(!heap.isEmpty()){
            result.add(heap.poll());
        }
        Collections.reverse(result);
        return result;
    }
}
```
## Use Bucket sort
```Java
class Solution {
//     public List<Integer> topKFrequent(int[] nums, int k) {
//         Map<Integer, Integer> map = new HashMap<Integer,Integer>();
//         for(int x: nums){
//             if(!map.containsKey(x)){
//                 map.put(x,1);
//             }else{
//                 map.put(x, map.get(x)+1);
//             }   
//         }
//     PriorityQueue<Integer> heap =
//             new PriorityQueue<Integer>((n1, n2) ->  map.get(n1) -  map.get(n2));
        
//     // build a heap for k top frequent elements in the heap.
//     for (int n: map.keySet()) {
//       heap.add(n);
//       if (heap.size() > k)
//         heap.poll();
//     } 
//         // build output list
//         List <Integer> result =  new LinkedList();
        
//         while(!heap.isEmpty()){
//             result.add(heap.poll());
//         }
//         Collections.reverse(result);
//         return result;
//     }
    
    
     public List<Integer> topKFrequent(int[] nums, int k) {
    Map<Integer, Integer> hm = new HashMap<>();
    List<Integer>[] bucket = new List[nums.length + 1];
    List<Integer> res = new ArrayList<>();
    for(int num: nums){
        hm.put(num, hm.getOrDefault(num, 0) + 1);
    }
    for(int key: hm.keySet()){
        int frequency = hm.get(key);
        if(bucket[frequency] == null)
            bucket[frequency] = new ArrayList<>();
        bucket[frequency].add(key);
    }
    for(int pos = bucket.length-1; pos >= 0; pos--){
        if(bucket[pos] != null){
            for(int i = 0; i < bucket[pos].size() && res.size() < k; i++)
                res.add(bucket[pos].get(i));
        }
    }
    return res;
  }
}
```
