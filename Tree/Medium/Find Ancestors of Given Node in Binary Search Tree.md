```
bst = {
        6 -> 4,9
    4 -> 2,5
    9 -> 8,12
    12 -> 10,14
}
where parent -> leftChild,rightChild
 
k = 10
```
## Sample output :
```
6,9,12,
```

## Solution: time complexity:O(Logn)
``` Java

class CheckAncestors {
	public static String findAncestors(Node root, int k) { 
		
		String result = ""; 
		Node tempNode = root; 
		while(tempNode != null && tempNode.getData() != k){ 
			result = result + tempNode.getData() + ","; 
			if(k <= tempNode.getData()){ 
				tempNode = tempNode.getLeftChild(); 
			} else{ 
				tempNode = tempNode.getRightChild(); 
			} 
		} 
		if(tempNode == null){ 
			return ""; 
		} 
		return result; 
	}

}

```
