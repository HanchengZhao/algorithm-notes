## Recursion and DP

## Recursion
 - return each layer's value to upper level in bottom-up solution
 
```java
public class Solution {
    int result = 0;
    
    public int findTilt(TreeNode root) {
        postOrder(root);
        return result;
    }
    
    private int postOrder(TreeNode root) {
        if (root == null) return 0;
        
        int left = postOrder(root.left);
        int right = postOrder(root.right);
        
        result += Math.abs(left - right);
        
        return left + right + root.val;
    }
}
```
- Recurse from different nodes to the end
[link](http://note.youdao.com/)


### Dp example

- Top down solution:
Using memoization
[climbing-stairs](https://leetcode.com/problems/climbing-stairs/#/description)
