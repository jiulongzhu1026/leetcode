# [560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k)

[中文文档](/solution/0500-0599/0560.Subarray%20Sum%20Equals%20K/README.md)

## Description

<p>Given an array of integers <code>nums</code> and an integer <code>k</code>, return <em>the total number of subarrays whose sum equals to <code>k</code></em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,1,1], k = 2
<strong>Output:</strong> 2
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,3], k = 3
<strong>Output:</strong> 2
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>-1000 &lt;= nums[i] &lt;= 1000</code></li>
	<li><code>-10<sup>7</sup> &lt;= k &lt;= 10<sup>7</sup></code></li>
</ul>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        counter = Counter({0: 1})
        ans = s = 0
        for num in nums:
            s += num
            ans += counter[s - k]
            counter[s] += 1
        return ans
```

### **Java**

```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        Map<Integer, Integer> counter = new HashMap<>();
        counter.put(0, 1);
        int ans = 0, s = 0;
        for (int num : nums) {
            s += num;
            ans += counter.getOrDefault(s - k, 0);
            counter.put(s, counter.getOrDefault(s, 0) + 1);
        }
        return ans;
    }
}
```

### **TypeScript**

```ts
function subarraySum(nums: number[], k: number): number {
    let ans = 0,
        s = 0;
    let counter = new Map();
    counter[0] = 1;
    for (const num of nums) {
        s += num;
        ans += counter[s - k] || 0;
        counter[s] = (counter[s] || 0) + 1;
    }
    return ans;
}
```

### **C++**

```cpp
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        unordered_map<int, int> counter;
        counter[0] = 1;
        int ans = 0, s = 0;
        for (int& num : nums)
        {
            s += num;
            ans += counter[s - k];
            ++counter[s];
        }
        return ans;
    }
};
```

### **Go**

```go
func subarraySum(nums []int, k int) int {
	counter := map[int]int{0: 1}
	ans, s := 0, 0
	for _, num := range nums {
		s += num
		ans += counter[s-k]
		counter[s]++
	}
	return ans
}
```

### **...**

```

```

<!-- tabs:end -->
