### Owner
- Wayne

### Question Title
- [107. Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/?tab=Description)

### Question Description
> Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).
```
For example, given
Given binary tree [3,9,20,null,null,15,7],
    3
   / \
  9  20
    /  \
   15   7
return its bottom-up level order traversal as:
[
  [15,7],
  [9,20],
  [3]
]
```

### Question Type
- [x] BFS
- [x] DFS
- [x] Tree

### Follow Up

### Solution
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> res = new ArrayList<List<Integer>>();
        if (root == null) return res;
        
        Queue<TreeNode> bfsQueue = new LinkedList<TreeNode>();
        bfsQueue.offer(root);
        while (!bfsQueue.isEmpty()) {
            int size = bfsQueue.size();
            List<Integer> row = new ArrayList<Integer>();
            for (int i = 0; i < size; i++) {
                TreeNode node = bfsQueue.poll();
                row.add(node.val);
                
                if (node.left != null) bfsQueue.offer(node.left);
                if (node.right != null) bfsQueue.offer(node.right);
            }
            
            res.add(0, row);
        }
        
        return res;
    }
}
```

### Time Complexity
- O(N + E)

### Space Complexity
- O(N)

### Solution2
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> list = new LinkedList<List<Integer>>();
        dfs(list, 0, root);
        
        return list;
    }
    
    private void dfs(List<List<Integer>> list, int level, TreeNode root) {
        if (root == null) return;
        if (level > list.size() - 1) list.add(0, new LinkedList<Integer>());
        
        list.get(list.size() - 1 - level).add(root.val);
        dfs(list, level + 1, root.left);
        dfs(list, level + 1, root.right);
        return;
    }    
}
```

### Time Complexity
- O(N + E)

### Space Complexity
- O(N)

### Ref Links
- [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/?tab=Description)

