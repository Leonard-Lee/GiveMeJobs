### Owner
- Stephen

### Question Title
- Possible edges of a triangle

### Question Description
Given an integer array with all positive number (0 not included), please return any three numbers that can build a triangle.

For example:
```
Examples: 
Input: [7, 3, 3, 3 ,6, 1 ]
Output: [1, 3, 3] or [3, 3, 3] or [6, 3, 7]

Input: [10, 3, 1, 6, 5, 2]
Output: [10, 6, 5]

```

### Question Type
- [x] Sort

### Follow Up
None

---------------------------------------------------------------------------
# [Solution 1] 


### Thoughts
1. First step sort
2. 構成三角形的條件: 任兩邊相加要大於第三邊
3. 假設三個邊長有a, b,c 且 a <= b <= c，我們只要判斷 a + b > c成立，該三個邊a,b,c就可以構成一個三角形，其餘不用判斷了，因為已經sorted了。

### Complexity
- Time: O(nlogn)
- Space: In place


### Ref Links


### Source Code
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class TriangleEdgesImpl_0307 implements TriangleEdges {
	@Override
	public List<Integer> findTriangleEdges(int[] nums) {
		List<Integer> res = new ArrayList<>();
		Arrays.sort(nums);
		for (int i = 2; i < nums.length; i++) {
			if (nums[i-2] + nums[i-1] > nums[i]) {
				res.add(nums[i-2]);
				res.add(nums[i-1]);
				res.add(nums[i]);
			}
		}
		return res;
	}
}
```